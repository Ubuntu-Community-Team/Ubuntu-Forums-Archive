---
title: "auto archive in evolution"
date: 2011-02-09
forum: General Help
---

### Post by badnaam on 2011-02-09
Is it possible to set automatic archive periodically ala outlook? My server has very limited storage so I would like to delete messages from server but keep them locally.

Thanks

---

### Post by badnaam on 2011-02-10
Anyone?

---

### Post by newb85 on 2011-05-10
I don't think there is an archiver built into evolution, but you have other options.

What protocol are you using?  IMAP?  POP3?  Do you access your emails from only one computer, or more?

You could simply set up a message filter that moves everything to a local folder when it arrives.  The downside to this is that it immediately becomes unavailable for access from any other machine.

Another option would be to use a program external to evolution to carry out archiving.  "archivemail" and "archmbox" are both in the repositories, and can be installed from the Software Center.  However, both of these are command-line programs (No Graphical User Interface), so to auto archive, you would have to write a simple shell script and add it to your crontab file.

---

