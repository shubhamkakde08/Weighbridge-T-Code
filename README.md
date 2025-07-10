# Weighbridge-T-Code
This view acts as a configuration reference for different types of weighbridge transactions in the ERP system.

# ERP Weighbridge Transaction Code Master – Oracle SQL

ERP-Weighbridge-TCode-Config/
├── VIEW_WEIGHBRIDGE_TCODE.sql        # View for transaction-type mapping in weighbridge
└── README.md                         # Project documentation


## 🧭 Overview

This project contains the SQL view `VIEW_WEIGHBRIDGE_TCODE`, a master configuration that defines the logic, rules, and conditions for various types of weighbridge transactions used in the ERP system.

Each transaction type (e.g., RM Inward, Sale Return, Yard Transfer) is mapped with essential metadata that governs:

- Required gate passes
- Order dependencies
- Fields to show or hide
- Item nature applicability
- Whether approval is required
- ESBS (Electronic Slip Booking System) mapping

---

## 📄 Files Included

| File Name                    | Description                                                 |
|-----------------------------|-------------------------------------------------------------|
| `VIEW_WEIGHBRIDGE_TCODE.sql` | SQL view for weighbridge transaction type master configuration |

---

## 🔍 Transaction Type Definitions

| TCODE | Transaction Type Name              | Requires Approval | ESBS Code |
|-------|------------------------------------|-------------------|-----------|
| `P`   | RM INWARD                          | No                | `GWI`     |
| `S`   | OUTWARD                            | No                | `GWO`     |
| `I`   | STORES MATERIAL                    | No                | `GWI`     |
| `Y`   | YARD TRANSFER                      | Yes               | `GWY`     |
| `W`   | CAPTIVE TRANSFER (RECEIVED)        | Yes               | `GWY`     |
| `C`   | CAPTIVE TRANSFER (ISSUED)          | Yes               | `GWO`     |
| `G`   | GENERAL PURPOSE                    | Yes               | `GWY`     |
| `R`   | SALE RETURN                        | No                | `GWI`     |
| `U`   | PURCHASE RETURN                    | No                | `GWO`     |

---

## 🧩 Key Columns in View

- `TCODE` – Single-character code to represent transaction type
- `TNAME` – Human-readable transaction type name
- `REQUIRED_GATEPASS` – List of gate passes required before processing
- `REQUIRED_ORDER` – Whether the transaction must be tied to an order
- `APPROVE` – Whether approval is mandatory (`Y/N`)
- `ACC_SCH_STR` – Valid account schedule codes
- `ITEM_NATURE_STR` – Item types allowed (e.g., `RM`, `FG`, `SM`)
- `INVISIBLE_COLUMN_STR` – Fields to be hidden on the UI for that transaction
- `ESBS_TRANTYPE` – Mapped transaction type for external integration

---

## 🧑‍💻 Usage

- Acts as a backend validator or UI driver for the weighbridge module
- Defines mandatory fields and business rules for weighbridge slips
- Prevents entry errors and ensures standardization across divisions
- Used by ERP UI developers and backend developers for rule enforcement

---

## 🛠️ Technologies Used

- Oracle SQL
- Dual-based SELECT UNION for enum-like behavior
- Used in ERP weighbridge transactions for LHS or similar platforms

---

## ✅ Author

**Shubham Kakde**  
ERP Config Developer | Oracle SQL Expert | Logistics Module Specialist

---

## 📜 License

For internal ERP configuration use only. This is a rule-based setup and does not contain transactional data.

---
