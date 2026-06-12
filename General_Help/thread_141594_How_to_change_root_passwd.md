---
title: "How to change root passwd"
date: 2006-03-08
forum: General Help
---

### Post by makiavelo on 2006-03-08
Hi, i just installed ubuntu and i´d like to make some changes but i cant log on as root. How can i change root passwd or how can i set an administrative user.

---

### Post by polpak on 2006-03-08
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-03-08
Read these two links:
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by HokeyFry on 2006-03-08
well, if you want to use the terminal to do everything, use the "sudo" command to gain root priveleges. The password you are prompted for is the password for the surrent user. Type in "sudo su" if you want to make yourself root for the rest of the terminal session.

If you REALLY want to use the GUI for changing things, then do the following, although it is highly discouraged:

Open *System->Administration->Login Screen Setup*.
Click the Security tab.
Click the box that says "Allow root to log in with GDM".
Close Login Screen Setup.
Open a terminal.
Type in "sudo passwd root".

The first password input is for YOUR password; it is associated with sudo.
The prompt for the root password change will say "Enter new UNIX password".

And there you go!:)
Now you should be able to login as root through the login screen.

---

