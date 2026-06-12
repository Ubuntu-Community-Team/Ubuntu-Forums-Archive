---
title: "Permission problems"
date: 2006-02-23
forum: General Help
---

### Post by brennan001 on 2006-02-23
I'm total new to Linux, but hear that ubuntu would be a good way to create a domain for my office. I'm rumming ubuntu 5.10 on a VMware Workstation to test if it will work. I installed the os by the instrutions on[http://www.howtoforge.com/book/print/917]("http://www.howtoforge.com/book/print/917"), only installing the server part of the system. My first problem I ran into is when i tryed to access the file /etc/network/interfaces to change to IP i get the error

-bash: /etc/network/interfaces: Permission denied

I tried to access the file both in the account I set up durning installation and as th root user. Can anyone help with this?

---

### Post by KroniX on 2006-02-23
type "sudo" before any command that requires permission.

---

