# Linux File Permissions Management

## Project Description
In this project, I worked as a security professional responsible for managing file permissions for a research team. My task was to examine the existing permissions in the `/home/researcher2/projects` directory and ensure they followed the organization's security policy.

Using Linux commands, I checked file permissions, identified incorrect access levels, and updated permissions to ensure only authorized users could access or modify files.

---

## Checking File Permissions

To display file permissions and hidden files, I used the following command:

```bash
ls -la /home/researcher2/projects
```

### Explanation

- `ls` lists directory contents
- `-l` displays detailed information including permissions
- `-a` shows hidden files

This command allowed me to review the permissions of all files and directories in the projects folder.

---

## Understanding Linux Permission Strings

Example permission string:

```
-rw-rw-r--
```

Explanation:

- `-` indicates a regular file
- `rw-` user (owner) can read and write
- `rw-` group can read and write
- `r--` others can only read

Symbols meaning:

| Symbol | Meaning |
|------|------|
| r | Read |
| w | Write |
| x | Execute |
| - | No permission |

---

## Removing Unauthorized Write Permissions

The organization does not allow **others** to have write access to files.

File affected:

```
project_k.txt
```

Original permission:

```
-rw-rw-rw-
```

Command used:

```bash
chmod o-w project_k.txt
```

This command removes write permission for others.

Updated permission:

```
-rw-rw-r--
```

---

## Updating Permissions for a Hidden File

Hidden file:

```
.project_x.txt
```

This file should allow:

- User → read and write
- Group → read only
- Others → no access

Command used:

```bash
chmod 640 .project_x.txt
```

Permission breakdown:

| Number | Permission |
|------|------|
| 6 | read + write |
| 4 | read |
| 0 | none |

Resulting permission:

```
-rw-r-----
```

---

## Restricting Directory Access

Directory:

```
drafts
```

Requirement: Only the owner `researcher2` should access this directory.

Command used:

```bash
chmod 700 drafts
```

Permission meaning:

| User | Group | Other |
|----|----|----|
| rwx | --- | --- |

Result:

```
drwx------
```

Only the owner can access the directory.

---

## Summary

In this project, I examined Linux file permissions and ensured they followed the organization's security policy. Using the `ls -la` command, I reviewed existing permissions and identified files with incorrect access rights.

I then used the `chmod` command to remove unauthorized write permissions, update permissions on hidden files, and restrict access to sensitive directories. These steps ensured that only authorized users had appropriate access to the system resources.
