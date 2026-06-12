---
title: "/proc/acpi/fan empty"
date: 2006-02-07
forum: General Help
---

### Post by anandrd on 2006-02-07
Hello,

My /proc/acpi/fan directory is empty. I have also been experiencing suspend issues (the laptop - Inspiron 6000, comes back from suspend immediately) and after it comes back I see the line 

grep: /proc/acpi/fan/*/state: No such file or directory.

1. Is /proc/acpi/fan/ being empty a reason to worry?
2. Is its being empty related to the suspend issue?

Thanks

---

### Post by dcstar on 2006-02-08
[QUOTE=anandrd]Hello,

My /proc/acpi/fan directory is empty. I have also been experiencing suspend issues (the laptop - Inspiron 6000, comes back from suspend immediately) and after it comes back I see the line 

grep: /proc/acpi/fan/*/state: No such file or directory.

1. Is /proc/acpi/fan/ being empty a reason to worry?
2. Is its being empty related to the suspend issue?

Thanks[/QUOTE]
Being empty just seems to indicate that the Linux system cannot get any information for this device via the ACPI system (mine is also empty).

The error line you see is probably a misconfiguration in the Restore scripts, (trying to change something that doesn't exist).

It may well be related, you should probaqbly check your /var/log/syslog & message log files to see if there are any related messages.

---

