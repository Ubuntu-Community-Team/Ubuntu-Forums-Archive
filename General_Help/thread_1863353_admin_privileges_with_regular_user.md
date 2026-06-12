---
title: "admin privileges with regular user"
date: 2011-10-17
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-10-17
i am the administrator on Ubuntu 11.10, and have a second account setup as a regular user. from time to time, i need to change things around on the regular user side, and find that it will not let me. 

su, sudo, gksudo, etc.. ask for a password, entering regular password says you are not sudoer, action is logged. trying to input my admin password tells me wrong password. 

i require the admin privilege to run a command to return screen brightness after dim/suspend. (setpci -s 00:02.0 F4.B=00). trying it without tells me i dont have access to /sys/ something or another. I tried, as admin, to take control of said file, and make it read/write for all.. but it still wont do it without 'sudo'

---

### Post by haqking on 2011-10-17
> **SE7EN-LOCSTA said:**
> i am the administrator on Ubuntu 11.10, and have a second account setup as a regular user. from time to time, i need to change things around on the regular user side, and find that it will not let me. 

su, sudo, gksudo, etc.. ask for a password, entering regular password says you are not sudoer, action is logged. trying to input my admin password tells me wrong password. 

i require the admin privilege to run a command to return screen brightness after dim/suspend. (setpci -s 00:02.0 F4.B=00). trying it without tells me i dont have access to /sys/ something or another. I tried, as admin, to take control of said file, and make it read/write for all.. but it still wont do it without 'sudo'

then add that user to the sudoers file if they need to perform sudo actions.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by syntr on 2011-10-17
Simple, add the following to /etc/sudoers:

<regular user's name> <computer name> = #0 NOPASSWD /usr/bin/setpci

You can read more here: [https://help.ubuntu.com/community/Sudoers#User_Aliases](https://help.ubuntu.com/community/Sudoers#User_Aliases)

---

### Post by SE7EN-LOCSTA on 2011-10-17
thanks!!

---

