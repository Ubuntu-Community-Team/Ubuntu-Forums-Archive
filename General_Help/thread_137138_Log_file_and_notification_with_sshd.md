---
title: "Log file and notification with sshd?"
date: 2006-02-27
forum: General Help
---

### Post by matt7340 on 2006-02-27
Is there a sshd generated log file so I can monitor who is logging into my computer and when?  Also is there a way to setup a graphical notification?  Is there even a gUI version of the "who" command?

Any suggestions appreciated.
Matt

---

### Post by dcstar on 2006-02-28
[QUOTE=matt7340]Is there a sshd generated log file so I can monitor who is logging into my computer and when?  Also is there a way to setup a graphical notification?  Is there even a gUI version of the "who" command?

Any suggestions appreciated.
Matt[/QUOTE]
/var/log/auth/log should have all of this information, and you can run the monitor function in Applications-System Tools-System Log on the file to see changes as they happen.

---

