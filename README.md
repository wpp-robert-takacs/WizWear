# WizWear — Mini E‑Commerce Backend Interview Task

## Overview
Your task is to design and implement a minimal backend service for **WizWear**, a fictional online clothing store, using **.NET**.  
You should apply:
- **Test‑Driven Development (TDD)**
- **Domain‑Driven Design (DDD)**
- **Event‑Driven Architecture**

The goal is not to build a complete production system, but to demonstrate **clean architecture**, **testability**, and **good design practices**.

---

## Scenario
WizWear sells clothing and accessories online.  
We need a simple backend that allows customers to place orders for products.  
When an order is placed, the system should trigger **order processing** via an event handler.

---

## Requirements

### Core Domain
- **Entities**
- **Customer**: `Id`, `Name`, `email`
- **Product**: `Id`, `Name`, `Price`
- **Order**: `Id`, `CustomerId`, `OrderLines` (ProductId, Quantity, Price), `TotalAmount`

### Use Cases
1. **Place an Order**
- Input: `CustomerId` and a list of `(ProductId, Quantity)`
- Rules:
    - All products must exist
    - Quantity must be greater than zero
    - Total amount is calculated from product prices
- On success:
    - Raise an **OrderPlaced** domain event

---

## Event‑Driven Requirement
- When an **OrderPlaced** event is raised:
- An **OrderProcessingHandler** should handle it
- The handler should simulate **processing the order** (mark as "Processed" and send an email)
- Processing logic should be **testable** and follow DDD principles
