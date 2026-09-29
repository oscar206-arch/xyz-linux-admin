XYZ Technologies : Log Changes

Change 001 : Departmental Groups

Date:2026-09-26
Admin:os206
System: n8server

#### Objective

Create Linux groups representing the departments within XYZ Technologies.

#### Changes made

The following groups were created:
-"it"
-"hr"
-"finance"
-"sales"

#### Verification

The groups were verified using:

'''bash
getent group it
getent group hr
getent group finance
getent group sales

Change 002: Department Shared Directories

Date:2020-09-29
Admin:os206
System:n8server

### Objective

Create shared departmental directories with controlled group-based access.

### Changes Made

Created:

- `/company/IT`
- `/company/HR`
- `/company/Finance`
- `/company/Sales`

Assigned group ownership:

- `/company/IT` → `it`
- `/company/HR` → `hr`
- `/company/Finance` → `finance`
- `/company/Sales` → `sales`

Configured permissions to allow full access for the directory owner and corresponding department group while denying access to other users.

Enabled the setgid bit on all departmental directories so newly created files inherit the appropriate departmental group.

### Security Model

Department members:
- Read
- Write
- Execute

Other users:
- No access

### Verification

Directory permissions and group ownership were verified using:

```bash
ls -ld /company/*
stat -c '%A %U %G %n' /company/*
