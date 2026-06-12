---
title: "windows networking issues"
date: 2006-04-30
forum: General Help
---

### Post by blackjack6.21.91 on 2006-04-30
I am trying to network between this and a windows computer directly using a USB cord (i'm a bit of a newb, so tell me if this isn't possible, i should be able to just find another cord and connect them both to the router, but i dont think thats the whole problem).  I've configured samba to share some things, and the Windows C is shared, but it prompts me for a password (screenshot).  I don't know what the password is, and if I just press cancel i cant see the other computer.  help! thanks

---

### Post by Wyrm_1972 on 2006-04-30
Did you set up a samba username & password on your linux box? You need to.

From a bash prompt type:
sudo smbpasswd -a username

username can be anything you want. For ease I have it set to the same as my  Ubuntu user. It'll then prompt you to set a password.

---

### Post by blackjack6.21.91 on 2006-04-30
alright
that solved that problem

but is there anyway i can make it so that no password is necessary to access my files over a LAN?

thanks

---

### Post by Wyrm_1972 on 2006-04-30
[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)

... solves the Linux end.

The Windows end is easy too. I've only done it with XP Home... the username and password to access the LAN needs to be the loggin username and password for XP Home.

---

