---
title: "Removal of Server without password"
date: 2011-01-14
forum: General Help
---

### Post by Walkerst on 2011-01-14
Hi,  I have recently installed what I thought was going to be Ubuntu client on to my laptop but it turned out to be server 10.04.   I kept meaning to uninstall it and install the client version but have left it so long that I have forgotten the username and password.  Is there any way around this and how do I go about uninstalling the server edition to install the client?

---

### Post by KeyserSoze93 on 2011-01-14
You don't need the login for the installed operating system to install a fresh copy. Provided you have no data on there you want to retrieve, simply put the Ubuntu Desktop CD in your drive and reboot the system.

You may need to select a boot device from the BIOS but after that the install should come up and you can simply install over the previous drive.

---

### Post by Walkerst on 2011-01-14
Does it have to be on a CD as I dropped it on to a DVD and tried this but didn't work.

---

### Post by gordintoronto on 2011-01-14
"Didn't work" isn't enough detail to help you. What did you do, and what was the result?

I have installed from a DVD with no problem whatsoever.

---

### Post by gordintoronto on 2011-01-14
"Didn't work" isn't enough detail to help you. What did you do, and what was the result?

I have installed from a DVD with no problem whatsoever.

---

### Post by pl@yer on 2011-01-14
boot any bootable *nix and mount the root partition of the computer
example
```

mount /dev/sdb1 /mnt/mydisk

```
chroot to the mounted root partition
```

chroot /mnt/mydisk

```
now change password

---

### Post by pl@yer on 2011-01-14
boot a bootable linux and mount the root partition of the computer
example
```

mount /dev/sdb1 /mnt/mydisk

```
chroot to the mounted root partition
```

chroot /mnt/mydisk

```
now change password exit reboot and log into the computer.

what is the diff between server and client versions? I would imagine just some daemons why not just use netstat to see what daemons are listening and uninstall the unwanted ones or stop them from starting with sysv-rc-conf

---

### Post by Walkerst on 2011-01-18
Thanks for your help, found out the issue was that I burnt the CD as data rather than image!!

Have a new issue with the install of 10.10 desktop after getting it to work.  It has gone through using the whole Hard drive without partition (will change later), the time set up and the keyboard set up and goes to the 'Who are you' screen for my name, computer name, username and password and states at the bottom of the window that it is 'copying files'.

I put all the info in and then (after a short while) where it said 'copying files at the bottom of the screen it says 'ready when you are' but the only button that is available to me is the 'Back' button as the 'Forward' button is greyed out.  I can expand the line and a greyed out 'skip' button appears along with a box that I can only describe as a command prompt type box which is black.

Just wondering if I was doing anything wrong or if anyone had come across this before.  I have only ever installed Ubuntu as a virtual machine not requiring a CD or a couple of years ago with an official preloaded ubuntu CD.

:-?

---

### Post by gordintoronto on 2011-01-18
Use lower case for the computer name and username.

---

### Post by Walkerst on 2011-01-19
Will try that when I get home. hopefully it is that simple :D

---

