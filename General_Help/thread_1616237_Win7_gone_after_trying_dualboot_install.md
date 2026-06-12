---
title: "Win7 gone after trying dualboot install"
date: 2010-11-08
forum: General Help
---

### Post by mpt2 on 2010-11-08
Hey guys!
Like the title says, my Windows 7 install is missing along with all the data I had from its partitions... Needless to say I'm a bit desperate to try to recover its files :C

The way it happened was as follows:

My 250gb HD was partitioned into C: 140gb and D: 97gb. 
I had Win 7 installed in C:.
I burned Ubuntu 10.10 into a 2 gb USB drive and proceeded to reboot and go through the installer.

When prompted what kind of install I wanted, i chose the first bullet option, "side by side".
Proceeding into the partitions screen, it suggested installing ubuntu into a partitioned drive (I assumed it was D: ) in halves that looked something like: "/files" 1.7gb worth of data in the first half (the partition size would be 45gb) and the second half would be ubuntu in the remaining 45gb (it had the ubuntu logo in red). I assumed the first half was containing the "live CD" data so i moved the slider to the far right making the first partition 1.7gb and the second one something around 95gb. 

After clicking forward a few more times ubuntu was installing and updating and asking me to restart. Which I did. 
After doing so, i got back directly into the ubuntu desktop, which is when i started panicking.
Restarting again confirmed my fears: there was no dual boot screen. 
Once in the desktop, i went to places > computer > filesystem properties to find out that I now have a single partition with 205gb free space and (according to the properties "192,264 items, totalling 128.0 TB
(some contents unreadable)".

So from here, what should I do next to recover the data from my old windows system? At this point all I'd like to do is get access to the files I need to back up from the old system and do a backup of them somehow before completely wiping my harddrive again and going for a new windows + ubuntu install.

Thanks in advance for any help you guys could provide,
desperately,
Mike

---

### Post by Quackers on 2010-11-08
You could try testdisk which is available from System > Admin > Synaptic Package Manager. Some people have had good results getting damaged partitions back, but I believe in your case Ubuntu has probably over-written some of it.
If you had a 250GB hard drive and it was virtually filled by its 2 partitions there was no way Ubuntu could be installed without over-writing some of it. Alarm bells should have rung when it offered to use 90GB that was not available.
Other than that you are looking at more professional data recovery. I would use the system as little as possible. Try using the Ubuntu live cd and select "try ubuntu" then try testdisk.
Good luck.

---

### Post by mpt2 on 2010-11-08
Sorry for the poor explanation. I had written a very detailed one and accidentally clicked one  of my side mouse buttons and lost it so the one that I actually posted was the second shot at typing. We all know how those go :S 

Anyways, before i installed ubuntu, my C partition (140gb total space) had 100gb of stuff, 40 gb free space; the D partition had 97gb of total and free space (i had just formatted it).

While installing ubuntu side by side with my other OS, it suggested allocating it half of an already existing 90 gb partition, in other words, a 45gb partition that looked to be half of my D partition. So per the installer, it wasn't even supposed to touch my 140gb partition. :/

When I moved the slider, i tried making it use what I thought was my full D partition.

---

### Post by rustutzman on 2010-11-08
Go to the administration menu in Ubuntu and open the disk utility. That will show you the drive partitions. Just in case your Win partition is still there.

---

### Post by oldfred on 2010-11-08
I lost a couple of folders recently and had to run photorec which is part of testdisk. It recovered many bits & pieces as some of the files I had saved many times.

If testdisk can get old partition structure back it would be better.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Quackers on 2010-11-08
I understand. That makes more sense. Unfortunately Linux doesn't use the C: and D: partition system. It may not even have recognised the partitions at all and here is where the problem has occurred.
I feel your pain. Many of us have suffered in a similar way in different circumstances at some time in the past.
The worst part of it is that if you had deleted the D: partition instead of just formatting it you would have got the option of using the unallocated space for installing Ubuntu.
All I can do is suggest booting from the live cd and giving testdisk a try.
I wish you well.

---

### Post by Decatf on 2010-11-08
Yes, your best hope is to use testdisk to recover the partition structure.

---

### Post by mpt2 on 2010-11-08
This is what disk util looks like....

[http://img203.imageshack.us/img203/1807/screenshotlm.png](http://img203.imageshack.us/img203/1807/screenshotlm.png)

just how screwed am i and/or what is the best course of action? >.<


edit: In the time I uploaded the screenie I didn't refresh to see the additional replies. I will be looking into those links oldfred posted and trying to restore whatever I can. Thanks for the help!. Should i run into any more trouble i'll post again :/

---

### Post by rustutzman on 2010-11-08
Sorry but it is bad news. Time to follow the other suggestions.

---

### Post by Quackers on 2010-11-08
Have a look at oldfred's post above.

---

### Post by Decatf on 2010-11-08
Unfortunately that does not look good for the option which you can simply recover the old partition structure. The installer has used the entire disk to install Ubuntu which means it has likely written over some data instead of resizing the partitions and using empty space. 

You can take a shot at recovering some data but some of it may be lost.

---

### Post by mpt2 on 2010-11-08
thanks for the help again folks!.
Currently running from the liveUSB and going for the data recovery.
ill report back with success or tears. hopefully the first!

---

### Post by mpt2 on 2010-11-08
well as much as a fiddled with the liveusb and even the hd ubuntu install, i couldnt figure out these recovery programs for the life of me

i ended up formatting again the whole damn thing and installing windows, scraping backup files from wherever i could, flashdrives, ipod, disks and even my email >.<

thats the end of trying to dual boot ubuntu for me. maybe ill get some courage to try again in a near future, thanks again everyone!

---

### Post by Ad@m on 2010-11-08
I hope you have learned something very valuable from your misfortune, backup before trying something new.

A great method to backup is to clone your hard disk with programs such as Norton Ghost / Acronis True Image or CloneZilla.

---

### Post by Sven6210 on 2010-11-15
> **Ad@m said:**
> I hope you have learned something very valuable from your misfortune, backup before trying something new.

A great method to backup is to clone your hard disk with programs such as Norton Ghost / Acronis True Image or CloneZilla.

Unfortunately it is too late for suggestions, however I also hardly recommend to use CloneZilla to make complete hard disk images. CloneZilla is Linux based and for free. You boot it from a USB stick and can backup/restore whole disks or partitions.

I always use it before I install a new OS to any systems and I even use it after the new system is installed in order to have a restore point. And for Windows such a restore point has the advantage that you do not need to reactivate Windows after you have restore from the image - as the images has been activated before.

---

### Post by Quackers on 2010-11-16
In my opinion you have suffered due to a poorly designed installer. There are bugs filed in this respect at Launchpad. Let's hope something is done about it before too many prospective Linux users suffer the same outcome and scoot back to Windoze.

---

