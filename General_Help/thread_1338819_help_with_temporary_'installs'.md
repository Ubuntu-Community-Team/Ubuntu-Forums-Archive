---
title: "help with temporary 'installs'"
date: 2009-11-26
forum: General Help
---

### Post by nerdopolis on 2009-11-26
Hi. I am trying to create a recovery CD for Ubuntu here: [http://ubuntuforums.org/showthread.php?t=1254973](http://ubuntuforums.org/showthread.php?t=1254973) . (well actually a script that you run that makes an ISO image of a recovery CD.) The way that it works is that it will mount your file system, chroot into it, and then GUI applications will be able to run in the Live CD's xserver. 

I also want to temporarily provide the chrooted system some programs temporarily, that will aide in system recovery, (for instance bootup manager, or something like that). 

-Installing the programs on to the chrooted system with apt-get is out the question because if there is a broken package, the install will fail, and the idea of the recovery tools will be useless

-I tried to bind the livecd's /usr/ folder to the /media/ChrootMountPoint/opt/recoverytools, and 'install' them by using the LD_LIBRARY_PATH environment variable, but it didn't seem to take. (I'll paste the output of ldd on one of those files when I get the chance), or is there some command I need to run to let it take effect?

-I'm thinking of union mounting the /usr folder with /media/ChrootMountPoint/usr folder, but that may cause library incompatabilites...

-I'm thinking of union mounting /usr with /media/ChrootMountPoint/usr/local, as that folder is a 'search' directory for libraries by default, and may avoid library conflicts, but I don't know if the program will search /usr/lib, then /usr/local/lib

-I want to avoid compiling with configuration. I'll have to pull in many headers upon live cd build, and will make the script way more complex. 

Which of these solutions will be the best?

Any help or solutions or ideas will be appreciated. 

Thanks.

---

### Post by nerdopolis on 2009-11-27
I tried moving some libraries form /usr/lib to /usr/local/lib. It would have worked, but there where some subdirectories with libraries in  /usr/lib, that didn't take when they where in /usr/local/lib.

I have decided to use aufs on /usr. even though it may cause temporary conflicts with existing programs installed, its only temporary during the recovery session. The actual installed files are untouched with an aufs mount.

---

### Post by Sin@Sin-Sacrifice on 2009-11-27
I made a custom live cd that pretty much has my desktop system on it. All of my software, customizations, and scripts on it. I found the best way to do this was chroot manually and use it like it's booted from the terminal. There's a great howto [here]("http://help.ubuntu.com/community/LiveCDCustomization"). Hope this helps.

---

### Post by nerdopolis on 2009-11-28
Thanks for taking the time to reply to my post. 

Unfortunately, my problem is that my live cd chroots a specified installed Ubuntu system when it boots. 

I can install the recovery programs on the live cd with the bash script I made, but I'm trying to find a way to temporarily make the recovery programs available to the chroot jail of the installed system, without using aptitude or apt-get, or writing to the actual file system.

---

### Post by nerdopolis on 2009-12-05
any ideas?

---

### Post by nerdopolis on 2009-12-07
Does anybody know how to do this?

---

### Post by nerdopolis on 2009-12-09
Or can this not be done?

---

