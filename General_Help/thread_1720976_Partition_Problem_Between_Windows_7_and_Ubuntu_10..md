---
title: "Partition Problem Between Windows 7 and Ubuntu 10.10"
date: 2011-04-03
forum: General Help
---

### Post by brc0005 on 2011-04-03
I am having problems with Ubuntu 10.10 not being able to see my Windows 7 Partitions. I would appreicate any help that is given. I am new to Ubuntu and have been working on this issue for a couple of hours. Thanks!
 
Below is a picture of what I am seeing in Windows 7 (which is a new install) and Ubuntu Live CD.
 
 
[IMG]http://i873.photobucket.com/albums/ab297/bcarter19/Windows%207%20Ubuntu%2010%2010%20Problems/Ubuntu.png[/IMG]
 
[IMG]http://i873.photobucket.com/albums/ab297/bcarter19/Windows%207%20Ubuntu%2010%2010%20Problems/Windows.png[/IMG]

---

### Post by idoitprone on 2011-04-03
ouuuuuuuuuuucccccccccccccccch, you are using dynamic disk. I dont think people on this forum can help you that much. You have to stay with that windows utility forever because you are a victim of microsoft.

dynamic disk are evvvvvvvvvvvvilllllllll

[http://ubuntuforums.org/showthread.php?t=367307](http://ubuntuforums.org/showthread.php?t=367307)

Note: disregard everything above, i just kept it there so i look more like an idoit lol

---

### Post by brc0005 on 2011-04-03
idoitprone: I am not using Dyanmic Disk I am using Basic Disk (Disk 0 is my hard drive).  Disk 1 is my USB drive.  Please explain is if I wrong or dont understand. 
 
Thanks for the reply.

---

### Post by idoitprone on 2011-04-03
> **brc0005 said:**
> idoitprone: I am not using Dyanmic Disk I am using Basic Disk (Disk 0 is my hard drive).  Disk 1 is my USB drive.  Please explain is if I wrong or dont understand. 
 
Thanks for the reply.

sorry i just the ball. I saw that windows utility and assume. my idoit mistake lol. Then I am not sure what is going on, since gparted should be able to read the partition table unless you are using gpt not mbr, but then again gparted have gpt support i believe

---

### Post by techunit on 2011-04-03
You should never partition Win vista or Win7 with Gparted anyway! You will break the boot config in Windows. Use windows disk management!

Please heed these warnings as, as much as I love fixing grub problems I could do without one that could have been prevented.

---

### Post by brc0005 on 2011-04-03
I am not Partition with GParted.  I recently formatted the hard drive clean.  After that I installed a clean Windows 7 install after the was finish I went over to Ubuntu and was going to install that on a different partition. When I switched over I notice that GParted is not finding any of the partitions that was made in Windows. 

Any suggestions???

 
Thanks for the replies!

---

### Post by techunit on 2011-04-03
That may be to prevent gparted from doing any damage to that partition. I know that gparted would detect it in the past. I wonder if its like that for everyone.

---

### Post by brc0005 on 2011-04-03
Ya, I dont know. I have been messing around with it for the better part of the day today. And nothing has come from it.  
 
Anyone else having this problem or know of a solution?
 
Thanks

---

### Post by idoitprone on 2011-04-03
[http://askubuntu.com/questions/27663/ubuntu-installer-thinks-my-drive-is-empty-does-not-see-windows-paritions](http://askubuntu.com/questions/27663/ubuntu-installer-thinks-my-drive-is-empty-does-not-see-windows-paritions) i believe you have the same problem. if you start gparted in the terminal, you might get an error. I cant really debug it

---

### Post by techunit on 2011-04-03
Why is this a problem though? I am not following sorry. Are you sure that sda is your windows partition? Try using the drop down to select another?

It sounds like you know what your talking about but some better explanation could help?

---

### Post by srs5694 on 2011-04-04
Chances are you've got a damaged partition table. GParted tends to flake out and show the disk as blank whenever it sees something that's even slightly off. To be sure of the diagnosis, you'll need to boot the Ubuntu installer in "try it now" mode, launch a Terminal window, and type the following command:

```

sudo fdisk -lu

```

Note that's a lowercase letter L, not a digit 1, in the "-lu" part. Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags (or post a screen shot of the Terminal window).

You can read [a Web page I wrote about this symptom,](http://www.rodsbooks.com/missing-parts/index.html) but I'm afraid it's rather verbose and could use some cleaning up. Chances are my [FixParts](http://www.rodsbooks.com/fixparts/) utility can fix the problem, but I can't be certain of that without seeing the fdisk output.

---

