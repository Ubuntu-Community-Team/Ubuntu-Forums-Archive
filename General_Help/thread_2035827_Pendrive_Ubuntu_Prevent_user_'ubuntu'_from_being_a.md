---
title: "Pendrive Ubuntu Prevent user 'ubuntu' from being added to /etc/sudoers"
date: 2012-07-31
forum: General Help
---

### Post by vilwarin on 2012-07-31
I recently created a persistent Pendrive Ubuntu (12.04) using usb-creator-gtk.
It works like a charm and I personalized it to suit my needs.

My only complaint is that user 'ubuntu' keeps getting added to the sudoers file. 'ubuntu' ist the standard user, when using Live-Ubuntu. Thus initially it needed to be in sudoers.
However I created my own user and removed 'ubuntu' from sudoers using visudo. I also checked that /etc/sudoers is read only. Still once I reboot 'ubuntu' is again in /etc/sudoers just under my own user. Sometimes I even found it several times.

Furthermore using sudo does not initially require to enter a password. No matter what user is logged in. I managed to disable autologin editing (/etc/lightdm/lightdm.conf). But if someone is clever enought to switch to tty1-6, he still gets an automatically logged in ubuntu user with a free to use sudo.

Any ideas, how I can
a) permanetely keep 'ubuntu' out of sudoers (or delete the user alltogether, which also does not seem to work) and 
b) make sudo initally require a password (and then save it for some minutes) like in a normal ubuntu installation
c) force ubuntu to also require login/password for the other text-only ttys.

Thank You!

vilwarin

---

### Post by vilwarin on 2012-08-02
no ideas?

---

