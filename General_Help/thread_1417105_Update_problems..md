---
title: "Update problems."
date: 2010-02-26
forum: General Help
---

### Post by Oz-bar11 on 2010-02-26
Ok, 

I just installed Ubuntu x64 on a partition that i just created (25gbs of my main 500gb with Xp on it) and all is going smoothly apart from the update from 9.09 to 9.10. I click on Upgrade and authorize system changes (Feels like Vista :p). It gets to  "Setting software channels" then a window called karmic comes up and says: (See picture)

[ATTACH]148352[/ATTACH]

I am thinking I need to somehow change what Ubuntu thinks is root... Is this possible?

Thanks in advance for any help!

Installed with "Install inside windows" btw.

---

### Post by captain_171 on 2010-02-26
How much room do you have left on your / partition the way you find out is:
Places
computer
Right Click on file system it will say on the bottom of that


I think that you made the Ubuntu partition to small. If that is the case there is a many choices to fix the issue.
1. Reinstall Ubuntu remove the old Ubuntu and re-size the drive so you can have at least 50GB for your / Ubuntu partition.
2. Remove windows and re-size / Ubuntu partition the whole drive from a live CD.
3. Try to clean the / Ubuntu partition and make more free space

---

### Post by Oz-bar11 on 2010-02-26
It appears that in the installation the installer resized the 25gb partition to a 7-8gb one... Erm. And no I'm not getting rid of Windows. I think i will resize from Windows. How will Ubuntu react to that?

---

### Post by schmutztaucher on 2010-02-26
I use GParted, which is very easy to use to resize partitions. It has a graphical user interface and can do a number of tasks. You would need to burn the .ISO to a CD by using Brasero's Disk Burner. Choose the "burn image" option.

---

