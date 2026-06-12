---
title: "hal.dll is corrupt or missing"
date: 2010-09-21
forum: General Help
---

### Post by eterniawolf on 2010-09-21
So, first of all hello everyone! I hope I stuck this in the right place.

So, onto my question. I kind of messed up my desktop computer trying to remove Ubuntu 8.10. I had installed 8.10 as a dual boot with Windows XP a few years back and now wanted to remove it mainly because of my mother, who can BARELY even turn a computer on. Plus, I can't connect to the internet anyway with Ubuntu (I need the Netzero dial up application in windows, since all I have right now is dial up).

Here's what I did. I downloaded the program "MBRFIX" so I could directly fix the mbr inside of Windows XP, since I don't have an XP recovery disc. I downloaded MBRFIX because I needed to get rid of GRUB. I fixed the mbr, and Windows XP directly booted. 

All was said and good, except Ubuntu still existed. I poked around on the internet and found something that said for me to use the Ubuntu Live CD and go to gpartition. It said to delete the Ubuntu partitions. So, I tried that, but it said something about unmounting something (I honestly don't remember what it said).

So, I continued following instructions. It said if you couldn't delete the partitions, to go to the terminal and type in "sudo swapoff" and then "sudo umount -a". So I did that. A bunch of stuff popped up in the terminal, mainly stuff that said "cannot unmount". I tried to delete the partitions once again, but that still failed. 

Finally, I just went back to Windows XP. I went to my computer, manage, and deleted the Ubuntu partitions from there. Finally, Ubuntu was gone! Of course, I wanted my 50GB space back on my XP, but I still had no clue how to go about putting that back. 

So, I booted the Ubuntu live CD again, in hopes of trying to partition the disk together again. So once again, I went to gpartition. It STILL wouldn't let me put the disk together again, even though Ubuntu was now gone. Then, I started poking around the options and clicked on "partition table". A warning came up saying it would delete data or something, so I IMMEDIATELY hit CANCEL. At that point, I didn't care anymore. I really wanted that 50GB, but I was just going to live without it. I was going to try Windows one more time, to see if I could find an option to add it back again. If I couldn't, I was done.

So, I shut down the computer (by this point for the 6th time) and booted it back up. What am I greeted to? "Hal.dll is missing or corrupt".

Oh joy. That's exactly what I said at that point. I think one of two things happened:

1. Deleting that Ubuntu partition messed up boot.ini, and thus messing up hal.dll(I think this is what happened)
2. Even though all I did was CLICK on the partition table and canceled it, it still messed it up (I still think option 1 is more logical)

And now I need to know how to fix this problem. I have no Windows XP recovery discs. I thought I did, but it turns out they were simply BLANK discs that were included so you could make backups or whatever. 

Is there a way I can restore hal.dll with Ubuntu? If not, what are my options?

---

### Post by elliotn on 2010-09-21
yes I use to restore corruption DLL files in windows, just copy a working DLL from another machine or download one from the net (be careful of viruses) and just drop it to the correct path eg system32 folder etc

---

### Post by elliotn on 2010-09-21
alternatively u can use the windows CD and do a repair

---

### Post by eterniawolf on 2010-09-21
So, I can go into Ubuntu, and find the System 32 folder from there and drop the file in? I guess I'll try that and see how it goes (if I can find the hal.dll file, anyway).

I have no recovery CD, so I can't repair it, but I'll try the first option you gave me. I'll report back later if it works. :)

---

### Post by eterniawolf on 2010-09-21
That didn't work. I replaced hal.dll with a new hal.dll, but that did nothing. I put the old hal.dll back (I didn't want to permanently delete it) since the new one did nothing.

Thanks for the suggestion though. 

So, I need to get a recovery CD or install something else at this point, huh? :mad:

---

### Post by Grepomate on 2011-03-24
This worked best for me:
1- Boot from the Windows installation media (CD).
2- After loading initialization files you'll see a menu with 3 options, press "R" for Repair.
3- Will prompt to select the Windows installation to work with, most likely #1, so enter "1", then Enter.
4- It'll then ask for the Administrator password: enter it if you assigned one, otherwise just press Enter.
5- You'll then be presented with a prompt that looks like this: C:\WINDOWS>
6- Type bootcfg /scan, after a few minutes it will show the windows installations identified, you should see at least one, if not most likely your Windows is corrupted and you'll have to reinstall from scratch.
7- In most cases you'll see "[1]: C:\WINDOWS".
8- Just to make sure, type bootcfg /rebuild, it will then ask to confirm that you want to add the installation it found. Press "Y" for Yes.
9- You should be back at the C:\WINDOWS> prompt.
10- Type EXIT then press Enter, the system should reboot to Windows normally.

Hope this helps, otherwise post your results to examine further.
G|:popcorn:

---

