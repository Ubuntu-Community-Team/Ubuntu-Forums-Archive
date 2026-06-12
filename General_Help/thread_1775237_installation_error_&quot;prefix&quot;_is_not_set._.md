---
title: "installation error: &quot;prefix&quot; is not set. Help me plz!"
date: 2011-06-04
forum: General Help
---

### Post by Artistbuon on 2011-06-04
Hi every one!
I'm a newbie. I decided to use Ubuntu-11.04 a few days ago.  Start with "Live-CD". I downloaded and installed as instructed but i get this error when i reboot my computer:
[COLOR=Red]          -------------- "prefix" is not set? -----------------------[/COLOR]
[COLOR=Black]I tried 4 times to reinstall[/COLOR] but i got the same result.
Any way, my current OS  is WinXP SP2.
Can anybody help me to install Ubuntu sucessfully.
Sory for may bad english. I'm not native English speaker.
Thanks for all!

---

### Post by Rubi1200 on 2011-06-04
Hi and welcome to the forums :-)

Please go to the Disk Management utility in Windows and take a screenshot of how the disks are seen by Windows.

Post the screenshot here in a new post by using the paper-clip icon on the menu bar.

---

### Post by Artistbuon on 2011-06-04
Hi!
this is my "Disk Management" screenshot ( attacked file ).

---

### Post by Rubi1200 on 2011-06-04
Okay, so there does not appear to be a problem with the disks.

Next thing to try is download the same wubi.exe and Desktop iso image and place them in the same folder. Then run wubi.exe again.

> download both Wubi.exe and the required Desktop ISO from the same location (the release has to match): 

[LIST]
[*]For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) 
[*]For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) 
[*]For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/) 
[/LIST]
Copy both files into the same folder on the machine and run the Wubi executable

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Artistbuon on 2011-06-04
Hi [Rubi1200]("http://ubuntuforums.org/member.php?u=1040746"),
Thank you very much for your replies.
I did the same as you told me but i still got the same problem.
[COLOR=Red]
Try (hd0,0): NTFS5: error: "Prefix" is not set.
Error: no such device/ubuntu/install/boot/grub/.....[/COLOR]
[COLOR=Black]
The processes are alright: 
+ dowload the ISO file
+ extract to the same folder
+ run the wubi.exe
+ set the user name, password, size
+ wubi ask to reboot PC
+ after reboot the computer, i choose ubuntu to install, it works well and then reboot the 
   computer again.   
+ i choose ubuntu to start ( another OS is Window XP ) and the problem start again as mentioned above.
..............
what's going on?
Would you give me any advice to solve this problem?
Changing to a brand new OS is so difficult....:(! 

[/COLOR]

---

### Post by Rubi1200 on 2011-06-04
Where are you trying to install Wubi to C, D, or E drive?

If possible, burn the iso image to CD and boot the computer with it choosing to try not install.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You need to set BIOS to boot from the CD drive.

Then, download and run the boot info script. There is a link at the bottom of my post with instructions.

This is a bit of a strange error, but hopefully we can help you sort it out and get Ubuntu installed.

Thanks.

---

### Post by whoeverwhatever on 2011-09-09
hello there, 

I have the same problem. And here is the Result.txt from 
**boot info script**

---

### Post by bonyjose on 2011-11-06
> **Artistbuon said:**
> Hi every one!
I'm a newbie. I decided to use Ubuntu-11.04 a few days ago.  Start with "Live-CD". I downloaded and installed as instructed but i get this error when i reboot my computer:
[COLOR=Red]          -------------- "prefix" is not set? -----------------------[/COLOR]
[COLOR=Black]I tried 4 times to reinstall[/COLOR] but i got the same result.
Any way, my current OS  is WinXP SP2.
Can anybody help me to install Ubuntu sucessfully.
Sory for may bad english. I'm not native English speaker.
Thanks for all!
same error here...any help?

---

### Post by muquang on 2011-11-06
> **bonyjose said:**
> same error here...any help?

me too :-(

---

### Post by Rubi1200 on 2011-11-06
@ bonyjose and muquang

Please start your own threads outlining the problem and providing as much information as possible including error messages, log files (found in %temp%) and, if possible, the boot info script (link at the bottom of my post with instructions).

Thread closed as information here may no longer be relevant.

---

