# Active Directory Help Desk Lab: Moe's Consultant

## Overview
A home lab that simulates the IT support for a small fictional company, Moe's Consultant. I built an Active Directory domain, created departments and employees, and worked help desk tickets in Jira from report to resolution.

## Lab Environment
- Oracle VirtualBox
- Windows Server 2022 Standard Evaluation (Desktop Experience), named MD01
- Domain: lab.local
- Private internal network with a fixed IP on the domain controller
- Jira (free plan), Kanban project: Moe's Consultant Help Desk

## What I Built
- Installed the Active Directory Domain Services role and promoted the server to a domain controller with a new forest
- Created organizational units for HR, IT, Sales, and Finance
- Created sample employees in each department, set to change their password at next logon
- Set up a Jira board with help desk statuses: To Do, In Progress, Waiting for Customer, Resolved

## Ticket Log

### Ticket 1: Employee locked out of account
- **Issue:** An IT employee could not sign in after entering the wrong password several times
- **Fix:** In Active Directory Users and Computers, reset the password, unlocked the account, and required a password change at next logon
- **Result:** Account restored without needing remote access to the user's computer

### Ticket 2: New hire needs an account
- **Issue:** A new HR employee needed a network account
- **Fix:** Created the user in the HR organizational unit with the logon mturay, set a temporary password, and required the user to create their own password at first sign-in
- **Result:** New account ready for the employee

### Ticket 3: Disabled account
- **Issue:** An HR employee could not sign in because her account was disabled
- **Fix:** Enabled the account in Active Directory and required a new password at next sign-in
- **Result:** Employee regained access

### Ticket 4: Employee left the company
- **Issue:** A Sales employee had left, and her access needed to be removed
- **Fix:** Disabled her account in Active Directory
- **Result:** Account can no longer be used to sign in, and the account stays on record instead of being deleted

### Ticket 5: Shared access for the Finance team
- **Issue:** Finance employees needed a consistent way to receive shared access
- **Fix:** Created a security group called Finance-Team and added two Finance employees as members
- **Result:** Access can now be granted to one group instead of to each person

## What I Learned
- Password resets, unlocks, and enabling or disabling accounts are done centrally in Active Directory
- Organizational units organize users, but access to shared resources is controlled by security groups
- Disabling a leaver's account is safer than deleting it right away
- Good tickets keep a running history, with one comment per step
- Customer-facing replies should be clear and polite

## Next Steps
- Join a Windows 11 VM to the domain and sign in as a regular employee
- Add shared folders and assign permissions to the security group
- Add PowerShell scripts for common tasks
