---
title: "How do I format the drive &amp; re-install Ubuntu?"
date: 2010-06-23
forum: General Help
---

### Post by Nbala on 2010-06-23
Hello! I'm semi-new to Ubuntu- but I *do* know my way around the terminal and general system procedures.

[CENTER][FONT=Century Gothic][SIZE=3]**Here's the situation I need help with:**[/SIZE][/FONT]
[/CENTER]

[LIST=1]
[*]An upgrade %100 pwnd my system: I performed an upgrade to *Lucid* from *Karmic* and I lost my keyboard input and sound *etc* *etc* *etc*.  :mad:
[*]I then **made a Karmic boot-run/install CD, & a USB startup stick.**
[*]I then **backed up** my important information on flashdrives etc.
[*]At this point in time **I have  2 partitions** :?: one with my old user account & info on it, and the other as a new (re)installed Karmic partition.
[/LIST]
[CENTER][FONT=Century Gothic][SIZE=3][COLOR=Red]_**My question is:**_[/COLOR][/SIZE][/FONT][FONT=Century Gothic]
[/FONT] [/CENTER]
[FONT=Century Gothic][SIZE=3][COLOR=Blue][COLOR=Teal]What is the procedure for: [/COLOR] 
a)[I] **formatting the drive**,
[/I]b)[I] **not** keeping the 2 partitions, and 
[/I]c)* **re-installing Ubuntu** (karmic) back onto it?*[/COLOR][/SIZE][/FONT]

I have **GParted** ( but I can't see how to use it to ***format*** ), and *I have no clue* how to format the Drive from either within the GUI or at the command-line.

[B][SIZE=4]How do I format & re-install Ubuntu?
[/SIZE][/B][SIZE=4]**What is the sequence or steps?**[/SIZE]

I can probably do the re-install intuitively but I'm concerned there may be Ubuntu tricks I don't know about! **Also- does this 2 partition thing cause any complications to formatting??**
So honestly ***my question is simply how to format the drive from within the system.***

Community, you have been **very** helpful in the past =D> and I am hoping someone will reply with the what to do. I thank you very much in advance ( I use this box for my online university program so its really important to me to clear this up! )

Thank you SO much! :grin:
~Drew, (aka Nbala)

---

### Post by phildini on 2010-06-23
When you reinstall Ubuntu from the CS, there are options for reformatting the entire drive, or manually specifying how you want partitions laid out. Does this answer your question?

---

### Post by khelben1979 on 2010-06-23
In my opinion, you should just let Ubuntu format the harddrive within a standard install which you get by booting it from an CD-R/DVD-R disc.

By formatting the harddrive from within the system, you erase the system which you're using which is not to recommend. However, if you intend to just reformat some partitions, then that would be possible from using GParted and if you search for GParted on YouTube you should find what you're looking for.

---

### Post by C.S.Cameron on 2010-06-23
The install will be quicker if you do it fro the Live USB rather than from the Live CD.
Simplest way to install will be to Boot the Live USB select install and when you get to partitioning use the "Use the Entire Disk" method.

---

### Post by Nbala on 2010-06-24
> **khelben1979 said:**
> In my opinion, you should just let Ubuntu format the harddrive within a standard install which you get by booting it from an CD-R/DVD-R disc.

By formatting the harddrive from within the system, you erase the system which you're using which is not to recommend. However, if you intend to just reformat some partitions, then that would be possible from using GParted and if you search for GParted on YouTube you should find what you're looking for.
Thanks khelben! *This answer led me down the right path.* 
I *tried* repartitioning (with *Gparted*- great tool btw) from *within* Ubuntu, but even if I unmounted and shrank or deleted the 'extra' partitions, I could not add it to the Ubuntu-containing partition because it was *un*-unmountble ( it was in use of course ). I didn't know how to do a complete format- I know the live CD/USB offers "Install Ubuntu" but I wasnt sure if it would format first or just put it on the partition again. ( The documentation was very unclear about this- search "format" and you get 100 things NOT about how to format, but about formatting as a stage in some other procedure. Seriously, the canonical documentation is very weak about this!!!)
So I ended up booting from a USB, then unmounting the Ubuntu drive (as I was running from USB) and using *gparted* to fix it all.
Thank you very much for your help!! :)

---

### Post by RJ12 on 2010-06-24
> **Nbala said:**
> Thanks khelben! *This answer led me down the right path.* 
I *tried* repartitioning (with *Gparted*- great tool btw) from *within* Ubuntu, but even if I unmounted and shrank or deleted the 'extra' partitions, I could not add it to the Ubuntu-containing partition because it was *un*-unmountble ( it was in use of course ). I didn't know how to do a complete format- I know the live CD/USB offers "Install Ubuntu" but I wasnt sure if it would format first or just put it on the partition again. ( The documentation was very unclear about this- search "format" and you get 100 things NOT about how to format, but about formatting as a stage in some other procedure. Seriously, the canonical documentation is very weak about this!!!)
So I ended up booting from a USB, then unmounting the Ubuntu drive (as I was running from USB) and using *gparted* to fix it all.
Thank you very much for your help!! :)

Glad to see you got it all sorted out :p I love this community too! Could you mark this thread as solved, using the Thread Tools at the top of your first post? Thanks!!

---

### Post by Nbala on 2010-06-24
> **C.S.Cameron said:**
> The install will be quicker if you do it fro the Live USB rather than from the Live CD.
Simplest way to install will be to Boot the Live USB select install and when you get to partitioning use the "Use the Entire Disk" method.
Thanks for the idea :idea:- it told me how to do what I wanted to:* keep it all like it was, but just grow the Ubuntu partition to max *( it was running on a 800mb partition! ) 
I didn't do exactly what you said ( as I wanted to *keep* the *Ubuntu* as is ideally, the re-install idea was only because ppl were telling me to- 
I told them [I]"If I wanted to EVER reinstall the OS, I'd still be using Windows!"
[/I]BUT- ***my version of your liveUSB idea did it***- as I said to khelben:

[LIST]
[*]     I did the "*try Ubuntu*" mode, and from there repartitioned the *now* *unmounted *Ubuntu drive, just deleted the other parts and grew the U-partition. Thereby keeping my OS & settings just like I wanted, but got rid of the extra partitions including the failed *Lucid* OS partition.
[/LIST]
     People should know that ( if they dont already!) if you have partitioning problems or disk problems, running Ubuntu from the USB & using *Gparted* will give you Uber-Sudo power over disk changes when needed! A useful "loophole".
~ Thanks so much for helping me out!!!! :D

---

