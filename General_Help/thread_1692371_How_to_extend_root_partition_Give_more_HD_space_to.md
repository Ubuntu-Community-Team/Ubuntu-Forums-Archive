---
title: "How to extend root partition? Give more HD space to root?"
date: 2011-02-21
forum: General Help
---

### Post by gkkrish on 2011-02-21
Im working in a dell studio 15..
this system now has two OS, Win7 and Ubuntu 10.10

HDD size: 320 GB

currently ubuntu is installd in a 10gb partition.

the rest is allocated to windows.

i want to add some 50gb to the ubuntu root.

help!!!

PS: im a newbie to linux..

---

### Post by wiggly81 on 2011-02-21
install gparted from ubuntu software center, its a simple to use partition manager it should make it very easy to extend the partition for you

---

### Post by Quackers on 2011-02-21
Welcome to UF.
If you boot into Windows and click Start > right-click Computer and select "manage" then in the new window on the left click on Disk Management. 
A new screen will open giving a display of your current partition setup. Is there4 any unallocated space available at the moment? If not, right-click on the C: drive and select "shrink" to see if any shrinkage is available. At this stage do not continue if there is shrinkage available. You should defragment the C: drive first, at least once.
When that's done you can select the amount of shrinkage required and click OK to apply. After a few seconds it will be done.
Reboot Windows at least twice to make sure it's happy. It can be funny sometimes!

When you're sure it's happy boot from the Ubuntu live cd and go to System > Admin > gparted and post a screenshot of that screen please.

---

### Post by gkkrish on 2011-02-21
ya gotcha.. but whats the need of screen shot bro??

---

### Post by Quackers on 2011-02-21
To see whether you'll need to extend an extended partition first.

---

### Post by gkkrish on 2011-02-21
yeah.. ohk.. will do.. :)

---

