---
title: "Transferring from Windows to Ubuntu"
date: 2009-07-18
forum: General Help
---

### Post by Bowarrowranch on 2009-07-18
Hey people.  I have a question about transferring files such as music and pictures from Windows to Ubuntu.  I'm going to have to stick with the dual boot seeing as how I can't get my AT&T wireless to install in Ubuntu.  Is it possible to do the transfer or is what I have in Windows stuck there.  I have way to much stuff to just throw it all away and it would be cheaper than buying blank discs'.  If anyone can help I'd appreciate it.  thanks in advance.

---

### Post by DeMus on 2009-07-18
> **Bowarrowranch said:**
> Hey people.  I have a question about transferring files such as music and pictures from Windows to Ubuntu.  I'm going to have to stick with the dual boot seeing as how I can't get my AT&T wireless to install in Ubuntu.  Is it possible to do the transfer or is what I have in Windows stuck there.  I have way to much stuff to just throw it all away and it would be cheaper than buying blank discs'.  If anyone can help I'd appreciate it.  thanks in advance.

When you have booted into Ubuntu,go to Places > Home Folder. On the left of the screen do you see your Windows drive(s)? Maybe they have different names, like 100GB.
If not, do this:

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

Now it will be possible to see your Windows disk(s). From now on it is just a matter of making a copy of (or move) your files on the Windows disk to a Ubuntu folder.

---

### Post by Bowarrowranch on 2009-07-18
Thank you DeMus.  I'll do that.  Again, I appreciate the help.

---

### Post by qshop on 2009-07-18
just go buy a usb flash drive man.  If you don't already got one you probably should anyways.  But either way what DeMus said should work.

---

### Post by amishtrucker on 2009-07-19
I have an AT&T Mercury USB. With Windows it is about a 15 minute install routine to make it work. When I plugged it into Ubuntu the first time, a window popped up asking me if I want to use the usb device to connect to the internet. I said yes, then it asked maybe one more question, like who my carrier was. Then it automatically connected and I was online in less than a minute.

---

