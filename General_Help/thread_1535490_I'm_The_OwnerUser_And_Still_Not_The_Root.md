---
title: "I'm The Owner/User And Still Not The Root?"
date: 2010-07-21
forum: General Help
---

### Post by technodenbow on 2010-07-21
Linux n00b and quit Windows cold turkey when Lucid was released. Since I installed, set up my user with full admin rights, I am getting questioned in Terminal a few times "are you root"?

Also have a hidden wireless network that requires me to supply my system password as opposed to logging into the network automatically. Is this a root issue?

Please tell me I do not have to reinstall in order for me to have complete control

---

### Post by marshmallow1304 on 2010-07-21
Root is the user that has complete power.  A normal user is not root for security reasons (Windows is starting to adapt to a similar system with UAC).  To gain root privileges in Ubuntu, you need to use sudo for command-line programs and gksudo for graphical programs.  You'll also need to be a member of the 'admin' group (the user created during install already is).

[URL="https://help.ubuntu.com/community/RootSudo"]
Full Explanation[/URL]

---

### Post by alphacrucis2 on 2010-07-21
> **technodenbow said:**
> Linux n00b and quit Windows cold turkey when Lucid was released. Since I installed, set up my user with full admin rights, I am getting questioned in Terminal a few times "are you root"?

Also have a hidden wireless network that requires me to supply my system password as opposed to logging into the network automatically. Is this a root issue?

Please tell me I do not have to reinstall in order for me to have complete control

There shouldn't be any need to use the root account in Ubuntu. If you want to enter a command requiring root privileges use sudo (or gksu for graphical programs). If you need to run a series of commands as root you can do sudo -i. Not sure about the wireless issue. I will try it at home later. I will change my AP to hide the SSID and see what happens.

---

### Post by aysiu on 2010-07-21
For a particular command, use *sudo*

**As user** ```
apt-cache search video
``` **As root** ```
sudo apt-get update
``` If you need to run a lot of root commands and don't want to type sudo each time, just use ```
sudo -i
``` If you want a root file browser, use ```
gksudo nautilus
``` If you use that often, create a keyboard shortcut or launcher icon for that command.

---

### Post by technodenbow on 2010-07-21
These suggestions should keep me going for a bit. Thanks to the community for your time and input!

---

