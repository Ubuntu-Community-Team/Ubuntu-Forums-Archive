---
title: "Virtualbox Snapshot Delete Issue..."
date: 2009-10-26
forum: General Help
---

### Post by Crumbles on 2009-10-26
So, here's what I did...

I made a snapshot of my XP box...  I was stuck with a 10 gig drive I made when I first set up the box, so, I decided to make a 20 gig drive.  I added a new hard drive that was 20 gigs.  I booted to a clonezilla ISO and cloned the 10 gig drive to the 20 gig drive, using expert mode to utilize the newer larger drive.

After the clone was done and I set the virtual box to use the new 20 gig drive, I booted only to find that I STILL had 10 gigs... so, I said f' it, I'll mess with this later.

I changed the virtualbox to use the original 10 gig drive, then deleted the 20 gig drive.  After that, I went to delete the snapshot I made, and it won't let me!  It says this:

---

 p, li { white-space: pre-wrap; }  Failed to discard the snapshot Clean Snapshot of the virtual machine
  p, li { white-space: pre-wrap; }  Hard disk '/home/ubuntu/.VirtualBox/HardDisks/Windows XP.vdi' has more than one child hard disk (2).
   Result Code: 
  [FONT= ]NS_ERROR_FAILURE (0x80004005)[/FONT]
   Component: 
  HardDisk
   Interface: 
  IHardDisk {62551115-83b8-4d20-925f-79e9d3c00f96}


---


So, my first question is, how do I delete this snapshot?  And two, what is the proper way to increase my hard drive space in the virualbox??


Thanks in advance.

---

### Post by Crumbles on 2009-10-26
I love you?  Friends?

---

### Post by Crumbles on 2009-10-27
*cries*

I have no friends... :(

---

### Post by zine92 on 2010-01-01
Hey, guess we have the same problem. lolz. but i really think xp on ubuntu sucks cause i have now a win 7 on ubuntu which is smoother. But anyway, i think the best way is to backup your virtual box folder which is at

```
/home/your_username/.VirtualBox
``` 

Make sure you enable hidden folder. And close all vbox windows and anything related and uninstall and restart just in case. After that, do a reinstall and set up a new windows xp. 

First, make this 2 folders, go to terminal, 

```
cd /home/your_username/.VirtualBox
```

Then, 

```
mkdir HardDisks Machines
```

Next copy your files respectively back to the folders. I.e. Your winxp.vdi should go back to 

```
/home/your_username/.VirtualBox/HardDisks
``` 

Next set up winXP again in Vbox. Go to new and when it comes to the choose HardDisk page press the little icon to the left and it will bring up a windows that let you choose your harddisk. Press Add and add the winXP.vdi back.
Guess that works for me. Hope that helps.

---

