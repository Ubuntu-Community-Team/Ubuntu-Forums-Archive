---
title: "Uninstalling Ubuntu Dual-Booted w/ Vista - Help!"
date: 2010-06-20
forum: General Help
---

### Post by DanYeomans on 2010-06-20
Hey everyone, I'm currently running Ubuntu 9.10 on a 64-bit PC with Windows Vista. Today, I bought Windows 7 upgrade for my computer and have acquired a new computer in which I will be transferring Ubuntu to. What I want to do is remove Ubuntu form the current computer, change the MBR to only show windows, and then merge the linux partition with the windows partition. Basically I want to bring my computer back to the way it was before I installed linux. Now this is where a problem arises. I have looked all over the internet for the solution, and it always requires either a floppy disk containing third party software, or a windows install disk. I have neither of those (other than the windows 7 upgrade disk which would not work in this situation). I want to know if it's possible to do it without those and without having to reinstall windows.

All help is appreciated,
Dan

---

### Post by Mark Phelps on 2010-06-20
> **DanYeomans said:**
>  What I want to do is remove Ubuntu form the current computer
Best way to do that is to boot from a GParted LiveCD (which you can download and burn from distrowatch.com), boot from that, and use GParted on that to remove the Ubuntu partition(s).

> ... change the MBR to only show windows ...
Number of ways to do that, one of which is to boot into a command line from a Vista Repair CD and run "bootrec.exe /FixMbr".  IF you don't have a Vista Repair CD, you can download and burn one from the link below:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

>  ... and then merge the linux partition with the windows partition... 
Not possible since they're very different file systems.  But if what you want to do is remove the Ubuntu partition(s) and expand the Vista partition to fill the space, do this latter action using the Disk Management Utility inside Vista.

> Basically I want to bring my computer back to the way it was before I installed linux. Now this is where a problem arises. I have looked all over the internet for the solution, and it always requires either a floppy disk containing third party software, or a windows install disk. I have neither of those (other than the windows 7 upgrade disk which would not work in this situation). I want to know if it's possible to do it without those and without having to reinstall windows.

Removing Linux is not going to invoke a time machine and magically restore your box to the days before you installed Linux, but if you remove the partitions, restore the MBR, and resize the Vista partition -- you have effectively done much the same thing.

If you really DO want to restore your machine to its original state, you will either need an OEM restore CD (if it came preloaded with Vista), or a Vista installation DVD.

---

### Post by DanYeomans on 2010-06-22
When I got this computer, I had the option to make Recovery Disks, and I did make them. Will those work?

---

### Post by Mark Phelps on 2010-06-22
> **DanYeomans said:**
> When I got this computer, I had the option to make Recovery Disks, and I did make them. Will those work?

Those are similar to what I called an OEM Restore CD, in that, if you boot from the first one, it should then reformat your drive and reinstall the original Vista setup.  Note that it will most likely remove ALL files as a byproduct of doing this restore.

---

### Post by Zerocool Djx on 2010-06-22
if you configure win7 during install to format your drive it will do all this automatically for you...

---

### Post by DanYeomans on 2010-06-22
I want to keep all my files and not have to back up them... And I don't have a vista repair CD because I didn't get one with my computer.

So I'm basically screwed with repairing the Master Boot Record then? Is there any software I can burn to a dvd to use to repair my MBR?

---

### Post by DanYeomans on 2010-06-27
I just thought of something... If I upgrade my Vista to Windows 7 it will overwrite the Master Boot Record right? Can someone clarify this for me? In which case all I have to do is format the linux partition after I upgrade and merge it right? That would work, right?

---

### Post by dino99 on 2010-06-27
i hope you have an /home where you have stored your data, then format (with gparted or better partedmagic) your ubuntu partition (root=/)

---

