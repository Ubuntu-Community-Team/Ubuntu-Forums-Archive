---
title: "Unable to login to server please help!"
date: 2012-09-20
forum: General Help
---

### Post by BlackJack25 on 2012-09-20
Hi guys and ladies,
 
We are running Zentyal Server at the office and today the server was extremely slow, so I rebooted the system, but now the system only gets to the linux login prompt.  
 
When I enter the username and password it looks like the screen refreshes and then I'm at the login prompt again.
 
Is there any way to solve this as all our data are on this server.
 
Please help.

---

### Post by iponeverything on 2012-09-20
It sounds like perhaps you have the wrong password. 

So, if you can't get the password - perhaps you next option would be to reset the password.

This is pretty straightforward, if needed. 

- Just boot into single user.
- remount / read/write
- Backup /etc/passwd
- empty the password field for the account.
- save and reboot.

This is abridged and there are other ways solve you issue, just google around a bit and post back with questions if needed.

---

