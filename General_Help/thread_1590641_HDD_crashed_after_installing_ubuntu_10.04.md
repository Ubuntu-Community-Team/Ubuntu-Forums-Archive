---
title: "HDD crashed after installing ubuntu 10.04"
date: 2010-10-08
forum: General Help
---

### Post by ishanjain on 2010-10-08
Here is a quick review of the problem....
I have 2 hard disks installed in my system, 160 GB and 500 GB. I have using windows 7 installed on the 160 GB disk for past 2 years now and never faced any problem with my HDDs. Now this 500 GB is some problematic one. Remember the 500 gb disks from seagate which was a huge failure, i have that model. I bought it with 3 more of my friends. All other's HDD's crashed again and again except mine. I did some scanning and all with all sort of HDD softwares but all is well, except one soft called HDD health that showed my 500 gb has 48% health. It remain like that for an year, so i stopped worrying about that. I have stuffed my disk with data and never faced any problem up untill now.
Now yesterday i decided to install Ultimate edition 2.7 64-bit. I downloaded it and burned the dvd at 4x speed and how i wanted to install it is like the way that it should go into the 500 gb one without having to do anything with 160 gb one having windows 7. I have done this earlier and it caused absolutely no problem. I just change the boot sequence to whatever disk i wanted to log into windows or linux(remember i did that with the same disks). Now i emptied a partition in 500 gb one, deleted it with the help of partition manager inbuild in windows 7, unplugged the 160 gb and booted thru live cd of UEU 2.7 and started the installation. When i got on the partition selection screen, what it showed me was just a 500 gb of "unallocated space", which i s actually healthy 6 partitions containing data which i have been using for years. No traces of the 30 space i unallocated in windows for linux. Now first question, "Why the hell did it not recognized my HDD when its perfectly operational in windows and i have installed UEU 2.5 on it once". It should have shown me the partitions. Does that means that my HDD was having some problem already ??
Now i booted back in windows, reallocated my 30 gb space, emptied some space from a 160 gb HDD's partition and got back into linux, with both HDD's plugged in this time. Now i started the installation. Again it didnt recognized the 500 gb chunk but did recognized the partitions in 160 gb and also recognized windows 7 installation. I formatted the partition with ext 4, didnt provide any partition for swap as i have 4gb ram and changed the boot loader to GRUB. Installation was successful. I can see all the drives from 160 GB one but only one partition from 500 GB one, no traces of other partitions, not even in Gparted. And yeah, the disk was mounted. 
Now everything was looking fine, i switched back and forth from windows to linux a couple of times, switched off the computer for some time, switched back on and watched a movie and finally shut down properly last night.

Now this morning my brother switched on the PC and it just wonts start. It restarts again and again just after the BIOS screen. I checked everything but couldnt find the problem. So finally i de attached the hardware one by one and found its the 500 GB that was causing the problem. I plugged it out and booted in again. To my surprise, the windows 7 booted in from 160 GB HDD **with no traces of linux what so ever**. Its was in the same HDD, i installed the common boot loader and have seen it my self when i switch on the pc, showing all linux options first and then windows 7 as other OS. It has nothing to do with 500 GB one, no dynamic partition, no system files or any thing. I suppose that windows 7 cant take back te boot loader without the help of installation disk and i have not used any. There was not even any kind of system recovery installed. Then how the hell windows 7 came back and linux just disappeared. The partition manager shows that the newly created partition for linux as "healthy and primary" partition. I have no explanation to all this, plz help me...

And plz say it once that all this mess was only due to i screw up the installation and my 500 GB is not dead. I will die without my data.

---

### Post by ishanjain on 2010-10-08
More than 60 views and not even a single reply.. come on guys i need help ASAP

---

### Post by Yougo on 2010-10-08
hi,
the lack of replies might have something to do with the lack of interpunction and paragraphs in your post. makes it harder to read.
Also it's not uncommon for a day or so to pass before someone picks up on a post. patience is virtue. 

that said, i read it, and judging by what you wrote, a number of things could have happened.

1. you somehow created a partition on the 500gb and installed there. then the drive died. it would explain why you can't find either, and the pc has trouble booting up. maybe some rescue kit can retreive your data, but things are looking sour. sorry.

as you said, you installed and dual-booted before so i assume you had enough of an idea of what you were doing, so i'll consider option two aswell: 

2. somehow the partition table got messed up, giving different partition numbers, sizes and locations than what's physically on your drives. i had this once too -actually after using Vista's prtitioning tool, so i generally advice people to steer clear of partitioning tools shipped with Windows, especially concerning live partitioning- 
things no longer add up and can not be found. your W7 installation is probably the first partition in order, so it can atleast find the start of that, and boot the system. 

if you have a bootable partitioning/rescue disc, it may be able to scan your drives and write a new partition table that does match up with reality. unfortunately i can't point you to one right now. maybe someone more partition-savvy can pick up where i get stuck?

regarding the quality of your 500GB drive, it sounds like it's going belly up. this'd be a good moment to get what you can get off of it, and depart fom it...

---

### Post by pricetech on 2010-10-08
May be water under the bridge, but if you can access the 500 gig drive in any fashion, back up your stuff BEFORE you do anything else.

Beyond that, I suspect the previous poster is correct in his summation of what happened, so I won't attempt to add to it.

As far as testing your drive, I suggest you use the drive manufacturer's diagnostic and nothing else.  That's the only way I know of to get a drive replaced under warranty by the manufacturer anyway.

---

### Post by ishanjain on 2010-10-09
You got it all **misunderstood**. Let me break down in points
**Earlier**
I have 1 160 gb and a 500 GB disk. 160 GB holds the Windows 7 in the first partition. The 500 gb one is seperate and has nothing to do with windows. I can remove it anytime.

**When i tried to install linux**
I decided to make separate boot records, as in let the windows 7 be in 160 gb and install linux on 500 gb and plug out the 160 gb while installing so that it doesnt get to know about windows 7. I have done this earlier and i change the boot sequence to the disk whichever's windows i wanted to run. It worked absolutely fine with me. Later i removed linux from 500 gb and things are back on track.
This time, when i plugged off 160 gb and tried to install on 500 gb, it showed me a whole 500gb of unknown type, while it was working perfectly under windows. Does that means it has some configeration issues??

**So what i did** is plugged back the 160 gb, deleted one chunk of 40 gb **from the 160 gb**, booted thru linux cd with both the HDD's on and then installed. Again it showed 500 gb of unknown type and showed all partitions from 160 GB properly. I formatted that 40 gb partition as ext 4 and carried on with my installation. It did found about windows 7 and i changed the boot loader to grub. Thats all, everything went fine.

After that, i restarted like 4-5 times, it showed me GRUB boot screen, i tried accessing both windows 7 and linux and everything was fine except one thing. I can see **only one partition from my 500 gb in linux** whereas it is working absolutely fine under windows. I thought that was some problem and i will fix them later. Last time, i booted into windows, watched a movie, did a proper shutdown and went to sleep. It died during the night somehow.



Now the problem is that the PC keeps on restarting just after the BIOS screen if i plug in the 500 gb. I dont know if this is a hardware problem or software problem, but it is happening. So i cant plug it in and capture screenshots of it in windows. **There is something you should note**.....
When i have kept everything separate from 500 gb and all the files of windows and linux and the GRUB is in 160 GB, where the hell did linux disappeared when i plugged out 500 gb ??
Ok we can say that linux somehow got corrupted in 160 gb, then why is it that GRUB boot screen also disappeared ??
Windows cant repair the boot problems without the rescue disk, then how the hell did windows 7 took over the GRUB and removed every single trace of it ??
**And remember that i have nothing like system recovery installed in my system**.

Things will get clearer when i try to plug in my 500 gb in my friends computer...

---

### Post by ishanjain on 2010-10-11
Ok now i tried plugging in my 500 GB in a friends PC. Good news, the computer didnt restarted on plugging it in, bad news, its still behaving strangely.
It has 6 partition and when i booted into his OS(which is also UEU 2.7 64-bit BTW), it shouwed me only only 4. The first and the last partitions are missing. Does this indicate something ??
Also, the last partition which is also the biggest and the most important for me, is showing up in my computer but is completely unaccessible. I tried force mounting it but it didnt work. 
I backed up most of my data and tried to tinker with it thru Gparted, but all it was showing is this 500 gb chunk of unknown filetype. So i couldnt do anything about it.
I bought it back home, plugged it in but its still restarting. Then i tried to boot in thru live CD with both HDDs on. This time it didnt restarted after BIOS and showed the boot menu. I selected run live CD and the DVD started spinning and the cursor blinking and and blinking but no progress for 5 mins. 
Now back on 160 GB and still waiting for help!!!!

---

### Post by dino99 on 2010-10-11
Dont worry but you might understand how grub-pc deal with devices:

each one get a uuid, but if you swith (unplug/plug) it, a new uuid is created, that explain that grub is lost because it cant find the previous uuid and dont know about the new one.

sudo blkid
sudo grub-mkconfig
sudo update-grub

If you often need to switch your hdds, a workaround is to set label, but its not the ubuntu default choice. See grub guide below.

---

