---
title: "Retrieve user accounts"
date: 2010-02-04
forum: General Help
---

### Post by lordbressers on 2010-02-04
I have recently come into ownership of an Ubuntu Server running v6.06.1 LTS at my workplace, but I wasn't left ANY details of login accounts for the server.

I have read numerous articles on booting in Single User Mode to get a Root command prompt, but when I try it it just shows the login prompt asking for a username and password.

My question is:
1) Is there a way I can perform some sort of rescue operation to gain access to user account details?
or
2) Is there a way I can gain access to the Root password, or at least reset the Root password?

Any suggestions would be much appreciated...

---

### Post by sisco311 on 2010-02-04
Highlight the Recovery Mode option, press e for edit,

highlight the *kernel* line & press e again,

remove the *ro single* kernel parameters and append 

the line with *rw init=/bin/bash*, press enter then b to boot.

Wait for all the boot-up processes to finish.

Change the password(s) with the *passwd* command. Press Ctrl+Alt+Del to reboot.

---

### Post by Iowan on 2010-02-04
Have you seen [this]("http://www.psychocats.net/ubuntu/resetpassword") page? Besides looking for accounts in /home, you can peek inside /etc/passwd to see what accounts exist... it's kinda busy, and includes system accounts as well as user accounts.

---

