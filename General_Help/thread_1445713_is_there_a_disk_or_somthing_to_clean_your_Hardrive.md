---
title: "is there a disk or somthing to clean your Hardrive?"
date: 2010-04-02
forum: General Help
---

### Post by Jarster1 on 2010-04-02
I noticed its my hardive that has problems and wont boot any of my operating systems not letting me get to my desktop. Is there a way i can clean it or a disk to do it but without doing it at your desktop?:confused:

---

### Post by SnickerSnack on 2010-04-02
I don't what you mean by "clean it".  It's possible that the HD has failed and will never work again, but you aren't very descriptive, so maybe you mean that it will start up, then then it hangs/freezes while trying to start an OS.

Worst case: HD is dead.
2nd worst: HD is having serious trouble and you need to back up and then replace the HD.  Use something like knoppix to backup important files, then replace the HD and reinstall.
3rd case: You just need to fix the boot loader.  Again, you'll probably need knoppix or some other live-linux.

By "but without doing it at your desktop?" do you just mean that you won't be able to use anything that requires a running OS?

---

### Post by X-Malleus on 2010-04-03
> **Jarster1 said:**
> I noticed its my hardive that has problems and wont boot any of my operating systems not letting me get to my desktop. Is there a way i can clean it or a disk to do it but without doing it at your desktop?:confused:
 
Describe exactly what happens, step by step, after you turn on your computer.

---

### Post by Tom.Gee on 2010-04-03
It is usually helpful to boot a LiveCD and examine the hard drive.  Have a flash, a NAS, or a USB HDD ready if you find you need to rescue your documents and other files.

---

### Post by Jarster1 on 2010-04-03
> **X-Malleus said:**
> Describe exactly what happens, step by step, after you turn on your computer.Im not an expert so ill try my best to describe im not sure if its my hardrive that has the problem. When i start it goes normal then it shows the ubuntu icon on the left corner it says unclean drivers or shutdown
checking dev/sda1..... and on the right corner says stage 0%. i wait a little while and then it takes me to another screen that says a manual fsck should be done so i do the fsck check. it says there is a problem so it says clear (y) iput y and it says there are illegal blocks i continue to put yes and then it shows numbers and on the right it says clear. then i keep pressing yes and nothing happens and it stops or freezes. So then i tried booting it with a ubuntu 9.10 live cd and after i put the boot option it shows the silver icon. i wait a long time then a cursor starts blinking on the left corner then i waited for 2 hours and nothing happened. So then i made a fedora disk and that also dosent work. I tried all these disks on my dads computer and they work fine. So please tell me is it my harddrive or somthing else? So i really cant get to any OS and go to the terminal or somthing thats why i want somthing that dosent need to get to your os desktop Because my computer wont let me get threw one!

---

### Post by efflandt on 2010-04-03
If you are having hard drive issues and cannot even boot a CD, then you may be having some other issue.  Check that your drive cables are seated tightly.

Did you change or add memory lately.  You might try removing and reinserting your RAM modules, which may help if there was some corrosion on the connectors.

We had a computer at work with Crucial RAM that was supposed to be compatible, but would occasionally (not very often) blue screen in Windows.  When I tested it with memtest86+ it had failures.  But when I put that RAM in another computer, it had no failures at all.  So sometimes RAM can be not quite compatible.

You might want to pick up a USB drive enclosure, so you could check that drive on another computer (if you do not know how to properly jumper and connect the drive internally to another PC).  Then you could fsck Linux partitions from an Ubuntu CD and see if everything is readable.

---

### Post by Jarster1 on 2010-04-03
> **efflandt said:**
> If you are having hard drive issues and cannot even boot a CD, then you may be having some other issue.  Check that your drive cables are seated tightly.

Did you change or add memory lately.  You might try removing and reinserting your RAM modules, which may help if there was some corrosion on the connectors.

We had a computer at work with Crucial RAM that was supposed to be compatible, but would occasionally (not very often) blue screen in Windows.  When I tested it with memtest86+ it had failures.  But when I put that RAM in another computer, it had no failures at all.  So sometimes RAM can be not quite compatible.

You might want to pick up a USB drive enclosure, so you could check that drive on another computer (if you do not know how to properly jumper and connect the drive internally to another PC).  Then you could fsck Linux partitions from an Ubuntu CD and see if everything is readable.Yeah maybe its my cd thing because every time i put a cd or dvd when it use to work it said it had problems reading it so iam going to check the ram or the cables to the cd drive thing see if its tight thanks for the help!:pI also did the memtest 86+ or somthing like that and it shows lots of numbers going down in red says errors falture or somthing what does this mean?I also dont care of memory lost or data if thats the way of fixing this.

---

### Post by spcwingo on 2010-04-03
It sounds like the southbridge on the motherboard is about to give up the ghost or bad RAM...just my $0.02.

---

