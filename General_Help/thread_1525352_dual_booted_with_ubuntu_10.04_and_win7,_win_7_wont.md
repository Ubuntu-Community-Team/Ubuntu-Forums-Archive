---
title: "dual booted with ubuntu 10.04 and win7, win 7 wont boot please help"
date: 2010-07-06
forum: General Help
---

### Post by Owen2410 on 2010-07-06
when i try to boot seven a black dos screen with a- flashs for a couple of seconds and then comp crashes and restarts i have no idea since im new to linux but i think it may have something to do with grub 

any help would be great please help

---

### Post by Rubi1200 on 2010-07-06
> **Owen2410 said:**
> when i try to boot seven a black dos screen with a- flashs for a couple of seconds and then comp crashes and restarts i have no idea since im new to linux but i think it may have something to do with grub 

any help would be great please help

Did you install Ubuntu from a CD or via Wubi?

What are your computer specs.; RAM, graphics etc.?

Do you have an Ubuntu CD or can you get one?

---

### Post by drs305 on 2010-07-06
If it crashes and eventually returns to the Grub menu this sounds like Grub was installed on the Windows partition. Here is a link which describes the problem and provides a solution:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

If this is not the problem, please run the boot info script and copy the results here (between "code" tags which you can generate by pressing the **#** icon).
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Owen2410 on 2010-07-06
i installed from a cd i do have the cd and my specs are as follows
1.67ghz processor intel core 2 duo 
2gb ram
NVIDIA GeForce 8400M GS 256mb graphics
its a laptop if that helps and any more specs you want just ask

---

### Post by Rubi1200 on 2010-07-06
> **Owen2410 said:**
> i installed from a cd i do have the cd and my specs are as follows
1.67ghz processor intel core 2 duo 
2gb ram
NVIDIA GeForce 8400M GS 256mb graphics
its a laptop if that helps and any more specs you want just ask

Thanks for providing us with this information.

I defer to the advice provided in the post above by drs305.

Look at what is posted there and if you have any further questions, feel free to ask.

---

### Post by Owen2410 on 2010-07-06
hmm just thinking does it change anything if win7 was working coz it sounds to me like you think i only just tried to boot seven just wondering...

---

### Post by Rubi1200 on 2010-07-06
> **Owen2410 said:**
> hmm just thinking does it change anything if win7 was working coz it sounds to me like you think i only just tried to boot seven just wondering...

Sorry, but could you please clarify what you mean?

In your original post you said:

 > i think it may have something to do with grub 

Can you boot into Windows yes or no?

Can you boot into Ubuntu?

You need to explain what went wrong as clearly as possible because we were not there when it happened and only you know the events that were involved.

---

### Post by Owen2410 on 2010-07-06
sorry i reread it and it does sound confusing mybad ill clarify what i meant was i used to be able to boot seven and as of today it stopped working and i can use ubuntu and ill try to explain what went wrong when i boot seven a little better i turn on my computer it loads grub i select windows seven and literally a black dos screen with a dash- flashes about three times then the computer crashes and restarts-goes back into grub 

p.s sorry if this is a bit of a mouthful i am trying to explain as best i can im not very good with dos hope this helps clarify

---

### Post by Rubi1200 on 2010-07-06
If I understand you correctly, the problem is with Windows, not Ubuntu.

In other words, you can get into Ubuntu, read emails, browse the web etc.

From Ubuntu, click on the link at the bottom of my post and follow the instructions there before posting back here so we can see what kind of setup you have.

If this is a Windows only issue you will need to wait for others to advise you on the next step (I only use Linux, so I am not really in a position to help you there; sorry).

---

### Post by DWade on 2010-07-06
Boot into Ubuntu go to applications and select Ubuntu software center and download gparted. thats Gnome partition editor

When you loaded Ubuntu did you divide the hard drive or did you allow automatic? if automatic do the  below item.

If you allowed automatic resize and install, then you will need to download Ubuntu 10.04 alternate CD from this link  [http://ubuntu.cs.utah.edu/releases/lucid/](http://ubuntu.cs.utah.edu/releases/lucid/)
I like the University of Utah so I supplied that link. i386 or 64 bit alternate install cd.

If you set up the partitions yourself then the only thing you should need to do is insure with running Gparted and once up by selecting the windows partition, like mine reads /dev/sda3 and check that the flag for windows is boot. If not right click on the that partition and select manage flags and change it to boot. Once done reboot and see it it loads.

If not what computer do you have. My new computer is a gateway laptop that has a restore partition as number 1, a boot partition as number 2,  and windows in the 3 rd partition.  I changed the 3rd shrank it and made an extended partition, then a data drive and then a ubuntu partition and swap partition.  So to boot windows the boot partition must be the boot flagged partition. which on mine is the second partition.

Next for auto install you must do the same thing insure the windows is boot partition and then run the alternate install cd.  run it through the repair settings and re-install Grub boot loader only.  You have to go through several steps.

Some of the updates may have included a new kernel which cause a grub to re-run. and if the boot changed then windows won't load.  If worse come to worse, you may have to put your windows disk in repair the boot then using the alternate cd re-install grub.

---

### Post by Zorgoth on 2010-07-06
If nothing else fixed your problems, this will, but it will kill your grub.

Run super grub disk to boot into windows (or maybe it has to be auto super grub disk) and then download a program called mbrfix online.  It is a command line utility that will restore your Windows bootloader.  IF YOU ARE USING A 64-BIT OS USE THE COMMAND mbrfix64, not mbrfix.  it is pretty well documented and not too hard to figure out.  if you need help ask and I Can try, but right now I don't have a windows system to work on.

---

### Post by wilee-nilee on 2010-07-06
**Post the bootscript** mentioned multiple times, without this bit of information we are just flailing in the dark. As drs305 said it sounds like grub got deposited in the windows partition. The script is also in my signature with a description how to post it in code tags.

---

