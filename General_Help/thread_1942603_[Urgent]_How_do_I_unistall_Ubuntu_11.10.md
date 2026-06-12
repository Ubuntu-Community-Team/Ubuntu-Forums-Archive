---
title: "[Urgent] How do I unistall Ubuntu 11.10?"
date: 2012-03-17
forum: General Help
---

### Post by JoshuaMiller0 on 2012-03-17
I love Ubuntu and I am not leaving, however I probably shouldn't have it on my school computer...

Anyway, I need to somehow remove Ubuntu from either withing itself or with a startup disk, as I have no admin rights on my dual-boot windows 7.

please help me ASAP

PS I have tried Google and all sorts of things to no good luck.

---

### Post by octohedra on 2012-03-17
well man, back up your stuff, put the windows 7 install dvd and format the linux partitions?

---

### Post by zombifier25 on 2012-03-17
You should format the Ubuntu partition and expand the Windows 7 partition using a boot CD (or USB) The Ubuntu CD has a tool called GParted that will just do the job. Choose the Ubuntu partiton, delete it, and expand the Windows partition.
And then, put the Windows 7 DVD in, boot from it and choose to repair Windows (so that the bootloader is repaired)

---

### Post by dave2001 on 2012-03-17
> **octohedra said:**
> well man, back up your stuff

Yep, you don't want to try any of this advice without making a good backup HDD image first in case things get fubar'd.

Zombifier's suggestion sounds like it should work easily enough.

---

### Post by JoshuaMiller0 on 2012-03-18
> **octohedra said:**
> ...put the windows 7 install dvd and format the linux partitions?

I said it was a school computer without administrator privileges. I do  not have a windows 7 install disk. Everything is set up for me and I  installed Ubuntu myself.

> **zombifier25 said:**
> ...The Ubuntu CD  has a tool called GParted that will just do the job.


The Ubuntu CD? I set up my own startup disk (USB) and as of 11.10 it  seems to not have menu. I do not know how to use the tool if it is on  there. How could I go about getting this tool on a startup disk?


 > **zombifier25 said:**
> And then, put the Windows 7 DVD in, boot from it and choose to repair Windows (so that the bootloader is repaired)
 
I have no Windows disk.

> **dave2001 said:**
> Yep, you don't want to try any of this advice  without making a good backup HDD image first in case things get fubar'd.

Zombifier's suggestion sounds like it should work easily enough.

Agreeing with other people's suggestions is not going to help anyone.

---

### Post by decrepit on 2012-03-18
If nobody can come up with a better method of getting you out of the s&^t.
You could set grub up to boot into windows with no delay and no splash screen.
Then keep your fingers crossed nobody notices the loss of memory.

---

### Post by Zill on 2012-03-18
> **JoshuaMiller0 said:**
> I said it was a school computer without administrator privileges. I do  not have a windows 7 install disk. Everything is set up for me and I  installed Ubuntu myself...
In which case I doubt if you were authorised to install Ubuntu.  Looking at this another way... would you be happy for someone else to install a new OS on *your* PC without your permission?

I suggest you confess all to your IT department and ask them to repair Windows as discussed.

---

### Post by Subidubi32 on 2012-03-18
So do you have any type of windows installed on your computer too, or just Ubuntu? the Ubuntu installer on usb must contain the GParted, or you can download the Gparted, write it on a cd , boot from it, and get rid of Ubuntu.

---

### Post by Subidubi32 on 2012-03-18
How don't you have administrator privileges? You installed a complete operating system for yourself on it.. I don't get it.

---

### Post by winh8r on 2012-03-18
As suggested already, go to the IT department, and explain what you have done. Don't do anything which will potentially make the situation worse.


The machine does not belong to you, so you should not be messing around and installing things on it , hence the reason you have no admin rights on the Windows partition.

Believe me, honesty is the best policy in a situation like this. Better to take it in and admit your mistake than present them with a broken filesystem and then have to admit it.

Hope this helps.

---

### Post by zombifier25 on 2012-03-18
EDIT: Oh great, I forgot that you had no admin privileges. Oh well, the only thing you can do now is follow other's advice: Confess to your IT department about it.

---

### Post by dave2001 on 2012-03-18
> **JoshuaMiller0 said:**
> 
Agreeing with other people's suggestions is not going to help anyone.

For starters, I didn't just agree with other people suggestions, I reminded you to make a hdd image backup before you tried anything.

Also, quibbling with the people trying to offer assistance definitely isn't going to inspire further support.

---

