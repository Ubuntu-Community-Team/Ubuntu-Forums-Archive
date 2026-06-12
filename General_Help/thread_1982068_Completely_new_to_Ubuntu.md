---
title: "Completely new to Ubuntu"
date: 2012-05-17
forum: General Help
---

### Post by gwilliamskc on 2012-05-17
Hey all!

I am a Ubuntu Newbie, but so far I am LOVING it!!! I think it is great, and much more user friendly than Windows. However, it is taking some time to get used to since I have only ever used Windows (since 199'8. I just have a few questions for the experienced users out there.

[LIST=1]
[*]I see no C: drive. What is similar on Ubuntu to that drive on Windows, etc.
[*]Every time I boot up my computer, I have the option to boot into Windows or Ubuntu. How do I get rid of this so it only goes into Ubuntu, and do I have do anything special to the hard drive(s) to make this work.
[*]Can I not put things on my desktop?
[*]Can I only get Ubuntu applications through the Software Center?
[/LIST]
Thanks so much! I know thats a lot at once, but I really want to nail this Ubuntu thing! I think I've found my OS from here on out. 



Grant Williams

---

### Post by goodvikings on 2012-05-17
1) 

The file system method is quite different. As opposed to each drive in windows having it's own 'tree' of directories, a drive in ubuntu (and all unix file systems) makes up a branch of one global tree.

You can look at it like the equivalent of C:/ is actually '/' which is the root directory. You might have other drives in /mnt/drive1 for example. 

2) Complex. someone else will knoe better than I.

4) I much prefer using apt-get install (application). you find the name of an application, and type that into the command line. But then I'm mush more used to ubuntu server where there is no window environment anyway.

Hope you enjoy the change!

Ramo

---

### Post by goodvikings on 2012-05-17
3) Again, I use server so no desktop for me. But it used to be there, I guess they removed it as part of unity, the new desktop environment, (which I hate... :P ) 

Ramo

---

### Post by gwilliamskc on 2012-05-17
Hey! Thanks for the quick response. All of your answers are going to be a great help!

And I will enjoy the change!

Grant

---

### Post by ZombeApocalips on 2012-05-18
Relatively new myself but depending on your version of Ubuntu, you might also be able to download .deb packages for installing programs.  The .deb file extension seems to be roughly equivalent to a Windows .msi file.  That's my $0.02.

---

### Post by c2tarun on 2012-05-18
> **gwilliamskc said:**
> Hey all!
Every time I boot up my computer, I have the option to boot into Windows or Ubuntu. How do I get rid of this so it only goes into Ubuntu, and do I have do anything special to the hard drive(s) to make this work.
 
Grant Williams
 
 
For this you have to edit /etc/default/grub file and set 
           
***GRUB_HIDDEN_TIMEOUT=0*** 
 and then run 'sudo update-grub' from terminal
 
 
But since you are new I'LL STRONGLY RECOMMEND NOT TO DO THIS. Since you installed Ubuntu after installing windows then it should be default. Press enter and enjoy Ubuntu, it will take just fraction of seconds :)
 
Welcome to Ubuntu :)

---

### Post by mwl128340 on 2012-05-18
if your using 12.04 with unity and you want to add shortcuts for an installed program, try clicking the program and hold the click in the apps and you can drag the shortcut where ever you want to. (launcher or desktop)

---

### Post by mwl128340 on 2012-05-18
there are several ways to get apps for ubuntu. the command line is a powerful tool.

---

### Post by ubuntu27 on 2012-05-18
Hi gwilliamskc. Here is a guide on
[How to install software in Ubuntu]("Installing Software in Ubuntu")

yes, you can put files on your desktop.

---

### Post by mastablasta on 2012-05-18
> **gwilliamskc said:**
> 
 
1. I see no C: drive. What is similar on Ubuntu to that drive on Windows, etc.

Drives are marked differently and are in a directory (folder). for example /sda1 is equivalent of C:\, /sda2 is d:\ if D is a partition on same disk. if it's another disk then it will show up as /sdb1 and so on.
Since you are new a good place to start is the community made manual. you already installed it so much of the first pages you can skip and jump to the inner works of the OS.
> 
2. Every time I boot up my computer, I have the option to boot into Windows or Ubuntu. How do I get rid of this so it only goes into Ubuntu, and do I have do anything special to the hard drive(s) to make this work.

depends how you inszalled it. if you installed with wubi, then i think windows bootloader handles this part. while if oyu have a side-by side install then you need to make changes to grub (such as delete windows entry or make Ubuntu entry default and 0 seconds timer. i could be wrong (since i haven't used it in a while) but i think a nice GUI tool to do this was Ubuntu Tweak.
 
> 
3. Can I not put things on my desktop?

sorry don't use the Unity interface but KDE desktop which is a windows look a like and wheer you can put a lot more on desktop than shortcuts (wheather widgets, analogue clock etc). anyway there hsould be a desktop folder in /home where if you put something in it, it should then be on desktop. but liek i said i am not using unity.
> 
4. Can I only get Ubuntu applications through the Software Center?

 
no software center (i.e. official repositories) is the prefered and safest method.
 
other methods include: 
PPA personal package archives - packed for you by other people - for example if you need a latest (testing?!) and always upgrading version of certain software (for example opensource graphcis drivers drivers) or fi programme is not in repositories
 
finding and downloading .deb file - kind of like .exe installer
 
finding and downloading .run files - installer scripts similar to .bat files or they can simply be run like a programme.exe file (i.e. no instaling needed).
 
finding and downloading .tar.gz (or. zip) files - usually source code that needs to be compiled. instrucitons are usually found inside the archive along with compile commands that can be copied to terminal. often you need to satisfy dependencies which can be a royal PITA. you also need to install compiler (can be found in software center) for those.

---

### Post by ubuntu27 on 2012-05-18
> **gwilliamskc said:**
> Hey all!

I am a Ubuntu Newbie, but so far I am LOVING it!!!  I just have a few questions for the experienced users out there.

[LIST=1]
[*]I see no C: drive. What is similar on Ubuntu to that drive on Windows, etc.
[/LIST]

Here are some links of interest:

[Filesystem Basics]("http://linuxconfig.org/Filesystem_Basics")

[Linux Filesystem Tree Overview]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview")

[Navigating the Linux Filesystem]("http://www.linuxplanet.com/linuxplanet/tutorials/6666/1/")

[Take the Linux Filesystem Tour]("http://www.tuxradar.com/content/take-linux-filesystem-tour")

[A Tour of the Linux Filesystem]("http://www.linux-mag.com/id/525/")

[Quick Introduction to Linux Filesystem & FHS]("https://dhavalv.wordpress.com/2007/10/17/quick-introduction-to-linux-filesystem-fhs/")

[Filesystem Hierarchy Standard]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

### Post by JKyleOKC on 2012-05-18
> **gwilliamskc said:**
> 2. Every time I boot up my computer, I have the option to boot into Windows or Ubuntu. How do I get rid of this so it only goes into Ubuntu, and do I have do anything special to the hard drive(s) to make this work.
3. Can I not put things on my desktop?
4. Can I only get Ubuntu applications through the Software Center?

Thanks so much! I know thats a lot at once, but I really want to nail this Ubuntu thing! I think I've found my OS from here on out.When you get that option dialog, is it in all capital letters, or is it mixed caps and lower case? If it's all caps, it's coming from the Windows "boot.ini" file or equivalent; if it's mixed case, it's coming from Ubuntu's GRUB loader. Getting what you want will differ between the two cases, so tell us which you see and wait for detailed instructions before proceeding!

If you put things in your $HOME/Desktop folder they should appear automagically on your desktop. To launch programs, you need to create "launchers" which are the equivalent of Windows "shortcuts." Right-clicking on the desktop should give you a popup menu that includes the option to create a launcher, but the exact details will differ from one flavor of Ubuntu to the next.

The Software Center is just one of many "front end" programs that access the repositories; you can use any of them, or as other posters have mentioned can get programs from other sources also. However when starting out, I strongly recommend that you use only the repositories. These packages have been tested and are guaranteed not to include malware; other sources carry no such warranty. I personally prefer Synaptic Package Manager to the Software Center because it gives more complete information about the available packages; if it's not installed by default, you can install it from the Software Center. However all of the front ends wind up at the same place in the end...

Welcome to the power of the penguins!

---

