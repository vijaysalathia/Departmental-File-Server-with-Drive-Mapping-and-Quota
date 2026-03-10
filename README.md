# Project 2 — Departmental File Server with Drive Mapping and Quota

## Description
Implemented a departmental file server using Windows Server and Active Directory. Configured shared folders for multiple departments, automated drive mapping using Group Policy, and applied storage quotas to control disk usage.

---

## Company Scenario
**Global Finance Ltd**

The organization wants a centralized file server where each department has its own storage location. Drives should automatically map when users log in, and storage usage must be limited to prevent excessive disk consumption.

---

## Departments
- Finance
- Audit
- Management

Management must have access to all department folders for oversight and reporting purposes.

---

## Folder Structure

```
C:\Global_Finance
│
├── Audit_Files
├── Finance_Files
└── Management_Files
```

---

## Shared Folder Configuration

| Folder | Purpose |
|------|------|
| Audit_Files | Storage for audit department documents |
| Finance_Files | Storage for finance department data |
| Management_Files | Management reports and documents |

Main folder shared as:

```
\\DC01\Global_Finance
```

---

## Drive Mapping Configuration (Group Policy)

Automatic drive mapping was configured using Group Policy Preferences.

| Drive Letter | Location | Target Department |
|--------------|---------|------------------|
| A: | \\DC01\Audit_Files | Audit |
| F: | \\DC01\Finance_Files | Finance |
| M: | \\DC01\Management_Files | Management |

Item Level Targeting was used to ensure only authorized groups receive their respective mapped drives.

Example Security Groups:

- Global_DL_Audit_SG
- Global_DL_Finance_SG
- Global_DL_Management_SG

---

## Permissions

| Folder | Allowed Group | Access |
|------|------|------|
| Audit_Files | Audit_Group | Modify |
| Finance_Files | Finance_Group | Modify |
| Management_Files | Management_Group | Modify |

Management users also have access to other departmental folders for monitoring purposes.

---

## Storage Quota

Disk quotas were applied to limit storage usage.

Quota per department folder:

```
2 GB
```

Purpose:

- Prevent excessive storage consumption
- Maintain controlled file server usage

---

## Features Implemented

- Departmental shared folders
- NTFS and Share permission control
- Automatic drive mapping using Group Policy
- Item Level Targeting
- Storage quota configuration
- Management oversight access

---

## Skills Demonstrated

- Windows Server File Services
- Active Directory Security Groups
- NTFS & Share Permissions
- Group Policy Drive Mapping
- Storage Quota Management
- Enterprise File Server Design
