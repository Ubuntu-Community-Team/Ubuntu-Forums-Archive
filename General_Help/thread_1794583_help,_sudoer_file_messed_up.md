---
title: "help, sudoer file messed up"
date: 2011-07-01
forum: General Help
---

### Post by scharig on 2011-07-01
Hi,

I simply booted my ubuntu 11.04 on which I have only one user with root privileges and got suprised that many groups have been added in my login screen:
audio 
avahi
avahi-autoipd
timidity
and many many more

I went to Users & Groups under administration to delete them. And when promted for my passwd I got:
user is not in the sudoers file

When I checked the properties of my account, I found out that my administration privileges has been untagged, and I can no longer modify, update, upgrade anything....

How can I fix this problem?

---

### Post by pawhtiobo on 2011-07-01
Hi,

Just restart you machine and in the grub bootloader, choose recovery mode, then choose the root or netroot console option, you need to add your user again to the admin goup and edit the sudoers file, here is some documentation:

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

See ya...

---

### Post by scharig on 2011-07-01
thanks a lot for your quick reply

I tried that, it didn't work, kept getting the same message

I solved it with a new installation

:)

---

### Post by pawhtiobo on 2011-07-01
Hi, 

Well...radical choice...lolll :D

See ya...

---

