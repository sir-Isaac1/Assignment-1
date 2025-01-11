import uuid
from datetime import datetime

class Ticket:
    def init(self, title, description):
        self.id = str(uuid.uuid4())
        self.title = title
        self.description = description
        self.status = "Open"
        self.created_at = datetime.now()
        self.closed_at = None

    def close_ticket(self):
        self.status = "Closed"
        self.closed_at = datetime.now()
        print(f"Ticket {self.id} has been closed.")

    def str(self):
        closed_date = self.closed_at.strftime('%Y-%m-%d %H:%M:%S') if self.closed_at else "N/A"
        return (f"ID: {self.id}\nTitle: {self.title}\nDescription: {self.description}\n"
                f"Status: {self.status}\nCreated At: {self.created_at}\nClosed At: {closed_date}\n")

class TicketSystem:
    def init(self):
        self.tickets = {}

    def create_ticket(self, title, description):
        ticket = Ticket(title, description)
        self.tickets[ticket.id] = ticket
        print(f"Ticket created with ID: {ticket.id}")
        return ticket.id

    def view_ticket(self, ticket_id):
        ticket = self.tickets.get(ticket_id)
        if ticket:
            print(ticket)
        else:
            print("Ticket not found.")

    def close_ticket(self, ticket_id):
        ticket = self.tickets.get(ticket_id)
        if ticket and ticket.status == "Open":
            ticket.close_ticket()
        elif ticket:
            print("Ticket is already closed.")
        else:
            print("Ticket not found.")

    def list_tickets(self):
        if not self.tickets:
            print("No tickets available

            // Part 2
            class Ticket {
    constructor(title, description) {
        this.id = this.generateId();
        this.title = title;
        this.description = description;
        this.status = "Open";
        this.createdAt = new Date();
        this.closedAt = null;
    }

    generateId() {
        return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
            const r = Math.random() * 16 | 0, v = c === 'x' ? r : (r & 0x3 | 0x8);
            return v.toString(16);
        });
    }

    closeTicket() {
        this.status = "Closed";
        this.closedAt = new Date();
        console.log(Ticket ${this.id} has been closed.);
    }

    toString() {
        const closedDate = this.closedAt ? this.closedAt.toISOString() : "N/A";
        return ID: ${this.id}\nTitle: ${this.title}\nDescription: ${this.description}\nStatus: ${this.status}\nCreated At: ${this.createdAt.toISOString()}\nClosed At: ${closedDate};
    }
}

// Example usage
const ticket1 = new Ticket("Bug in Login", "User cannot login with correct credentials");
console.log(ticket1.toString());

// Closing the ticket
ticket1.closeTicket();
console.log(ticket1.toString());
