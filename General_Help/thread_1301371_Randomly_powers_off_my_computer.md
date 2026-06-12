---
title: "Randomly powers off my computer"
date: 2009-10-26
forum: General Help
---

### Post by Earl-Grey on 2009-10-26
[FONT=Verdana][SIZE=2][COLOR=Gray]I recently tried Linux Ubuntu for the first time and I have to say I was presently surprised. Graphically compared to the Windows I am running at the moment it is very fast and pleasing to the eye.

  Unfortunately I did have a few problems and I hope that some cleaver person out there can give me a hand.

  Firstly I am installing Ubuntu from within Windows, I am not able to burn a CD, as my drive has not been happy for quite a few years now. Reads disks fine, but doesn’t recognise blank CD’s or DVD’s. So, I installed Ubuntu from a virtual drive.

  When installing it I get my first problem, I didn’t want to install Ubuntu on my default windows drive as it lacks space. I would like to install it on my external drive which has over 50GB free. When installing on my external drive it takes about 10 times and seems to hang on the `Creating Virtual Disks` screen. After the installation is complete I reboot and it come up with an error, something about the disk not being a NTFS disk. So I presume that Ubuntu doesn’t like my drive as it is FAT32.

  Second attempt, I installed it on my default drive where I have Windows installed. It was a lot quicker to install and booted up fine. After successfully loading up the main window, an option pops up the get the latest updates a believe. I click to download the new updates and I hear a system beep then another and the computer switches off. I thought it was quite strange and was just one of those things, but now when I try it, sometimes it makes the beep when type in my password on the log in screen. It starts to load the main desktop and beeps again then switches off. If I am luck, I can use it long enough to get the internet set up and start browsing, but then I hear the dreaded beeps and power turns off.

  The worse thing is that, if the power is cut when I am installing a program, it doesn’t allow me to reboot Unbuntu and I have to go back into Windows, delete the installation and then reinstall it.  

  It’s the first time my computer has simply powered down out of the blue. It doesn’t say ‘now saving or anything’ just beeps and then nothing. It works fine in windows and I feel it must be something to do with how I have configured the installation.

  I have tried changing the installations size and language settings but it still powers off. Could it be something to do with my CD/DVD drive not working? Windows seems to be happy for it not to work but maybe Linux wants me to fix it ](*,)


Also tried different versions   [/COLOR][/SIZE][/FONT]                              [FONT=Verdana][SIZE=2][COLOR=Gray]Including the beta version, but the same problems occurs.[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Gray]


I really would like to use ubuntu and any advice would be great.[/COLOR][/SIZE][/FONT]

---

### Post by martrn on 2009-10-26
You can install ubuntu using [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")  UnetBooIn can be used to run utilities such as **_[Parted Magic]("http://partedmagic.com/")_**, where you can create your own partition to install Gnu/Linux/Ubuntu to.  Ubuntu partitions should be ext3 or ext4 which can be on your main disc or your external drive with over 50GB free.

Sorry your Wubi-buntu Cooperative Virtual Machine (CVM) Didbn't work. What do you know about system software which allows Microsoft Windows and the Linux kernel to run simultaneously in parallel on the same machine ?

Anyhow I sugest UnetBooIn for simplicity's sake.
Good Luck.

---

### Post by Earl-Grey on 2009-10-26
> **martrn said:**
> You can install ubuntu using [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)  UnetBooIn can be used to run utilities such as **_[Parted Magic]("http://partedmagic.com/")_**, where you can create your own partition to install Gnu/Linux/Ubuntu to.  Ubuntu partitions should be ext3 or ext4 which can be on your main disc or your external drive with over 50GB free.

Sorry your Wubi-buntu Cooperative Virtual Machine (CVM) Didbn't work. What do you know about system software which allows Microsoft Windows and the Linux kernel to run simultaneously in parallel on the same machine ?

Anyhow I sugest UnetBooIn for simplicity's sake.
Good Luck.

Thank you very much for the advice. I will try it out tonight. :KS

---

