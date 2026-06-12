---
title: "Lost backup folder"
date: 2011-06-23
forum: General Help
---

### Post by vyco10 on 2011-06-23
Background: I have two HDD installed on my desktop. One WinXP, the other (was) Ubuntu 9.10. Well, I wanted to upgrade to Ubuntu 10.04 so I copied everything I was going to keep to a folder that I was going to store on the HDD with the Windows installation.

I installed Ubuntu 10.04 on the hard drive, but I forgot to turn off the Windows HDD in the BIOS and because of that Grub wrote over Windows MBR, which I then fixed.

Here's the problem I've got now, which I don't know if it's related to the MBR screw up or not. I have everything installed the way I want it... except, my backup folder is nowhere to be found on the WinXP HDD. I have two partitions, C and D on the Windows drive and I had stored the backup folder on partition D. It stands to reason that it should still be there, and Windows is even counting the drive space as being held by the folder.

Oh, and BTW... I can't see the folder even when logged into Ubuntu so it's not just an issue where Windows can't see it but Ubuntu can.

Any body got a good suggestion on a program that could help me recover this lost folder?

Thanks.

---

### Post by coldraven on 2011-06-23
Install testdisk from the Software Centre. Installing Testdisk will also install Photorec.
The next part will depend on if you have more spare space on your Ubuntu drive as there is on your drive D:. 
If not you would need to plug in a large USB drive and work from that.
If you do then in Ubuntu create a folder called, say, my_lost_files.
Make sure that your XP disk is visible and mounted in Ubuntu.
Then open a terminal with Ctrl+Alt+T and make it fullscreen.
Type ```
cd my_lost_files
```Then type ```
sudo photorec
```Select the correct partition on your XP drive.
Select where you want the files to go (either into my_lost_files or onto a USB drive)
Then press "Y" and go make a coffee.

You could read this first as I might have missed something
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

There are other, probably better, ways using "dd" but i don't know how to.
Good luck :)

---

### Post by vyco10 on 2011-06-23
Ubuntu drive is 160 GB
Windows D partition is roughly 800 GB (entire drive is 1 TB)

I have no external drive large enough to accommodate randomly recovered files. 

Surely there must be a better way of recovering this specific folder than how Photorec does it. Or maybe I'm misunderstanding how Photorec works. It does just go through and randomly saves files, truncating their names and placing them in random folders, correct?

---

### Post by vyco10 on 2011-06-26
OK... I was able to recover the files via this program on the Ultimate Boot CD For Windows called "Handy Recovery". For whatever reason this program could see the folder. It's just strange that nothing else can can.

But now I have a new problem. The backup folder and all the stuff I backed up is still there, but I can't delete it. As a result, it's taking up hard drive space that I want to free up. I can't reformat the drive because all of my stuff is on that drive and I don't have another drive to put it on.

Anybody know of a program that can delete lost/missing files and folders

---

