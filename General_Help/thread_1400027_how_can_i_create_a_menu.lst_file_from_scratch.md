---
title: "how can i create a menu.lst file from scratch?"
date: 2010-02-06
forum: General Help
---

### Post by aviramof on 2010-02-06
i have just installed ubuntu 10.04 dvd version and ho and behold grub error 15 just amazing any way i enter the partition via live cd thinking i edit the menu.lst file and that it but the folder grub it completly empty what is going here and how can i fix this?

thanks in advance.

---

### Post by howefield on 2010-02-06
Are you sure you want a menu.lst ? ;)

You'll be wanting a read here...

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by aviramof on 2010-02-06
ok i want grub 2 now how do i install it via live cd and make him recognize my operating systems?

---

### Post by oldos2er on 2010-02-06
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ubuntu 10.04 questions/problems should be posted to [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by aviramof on 2010-02-06
Thank you for the help but i think i'm about to give up on ubuntu at all till version 10 will go out i have worked here for hours trying to install this version and no luck first
i installed it via the option install ubuntu in the cd and got error 15 so i said why not 
reinstall from live cd including updating the installer and etc so i again formated and 
tried to install installer got stuck in 85%.
 
so i tried again formated again to make sure no problems would happen from perviouse installation again got stuck in 80% even that i left it working for two hours nothing again i restarted the computer went into install ubuntu option formated again but here i had another problem my computer is
connected via dvi hdmi to my tv the live cd must have noticed that so he extended the
screen and all the options went there i said ok switch to the hdmi channel and so nothing but pink ha ha ha the hall screen was pink barely could see the options there.
 
but i'v managed to run the installer any way and install but i already knew i would get error 15 from before so i shut down the tv after it had finished installing and the next time i ran the live cd it did not extend the screen and by the way loading the live cd here takes a hugh amount of time something like five minutes or something like this. 
 
after entering live cd again i tried all sort of methods describe here 
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) and here [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) to install grub 2 and etc but still no luck still grub 1.5.
 
eventually i tried the last solution i could think of i'v removed grub completly enterd windows 7 cd botrec.exe /fix boot botrec.exe /fixmbr grub vanished windows 7 up so far so good restaretd enterd live cd again mounted the partition via some of the commands from here [https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD all 
the way to chroot and extually now that i think about it might be the reason it didn't
worked maybe you should add to the guide how to mount from live cd any way tried to install grub again restatred the system nothing happen meaing windows 7 started alone no grub no nothing so just consider all of this problems in your final version.
 
and now i'm going to do what i just thought of reinstall grub 2 via noraml mount option and see how it works wish me luck.:):):)

---

### Post by mushwars on 2010-02-06
I find it funny that debian prides itself on stability and making sure things work before putting them out there and are way behind cutting edge.

In gentoo you are guarenteed to be on the bleeding edge yet when you install grub, unless you are running an unstable ~x86 system you get grub (GNU GRUB 0.97) by default when you emerge grub.

Am I missing the reason why debian has decided that it would be good to put an unstable release on the main line of releases?

---

### Post by samantha_ on 2010-02-06
this is why its called lucid lynx **beta**

p.s. if it gets stuck at 85%, try unplugging your internet before installing.

p.p.s. please consider filing a bug report.

---

### Post by aviramof on 2010-02-06
i would fill a bug report later now what i need is help how to install grub i'v just read that grub 2 doesn't support ntfs is that true?

i need ntfs for my windows 7 so what can i do to solve the problem how can i install grub 1.5 without getting grub 1.5 error 15 again?

thanks in advance.

---

### Post by dcstar on 2010-02-07
> **aviramof said:**
> i would fill a bug report later now what i need is help how to install grub i'v just read that grub 2 doesn't support ntfs is that true?

i need ntfs for my windows 7 so what can i do to solve the problem how can i install grub 1.5 without getting grub 1.5 error 15 again?

thanks in advance.

You should **not** be posting anything related to development software in the forums that are solely for released version.

The conditions of using pre-release software clearly state that all issues are to be posted in the appropriate development forum.

If you do not post these issues where they are supposed to go, then the chances of them being fixed before release are diminished and **you** are contributing to poorer quality software.

---

### Post by aviramof on 2010-02-07
i already posted there i just posted here long before that and wanted to close this thread in a good way.
 
and by the way take a look at the thread i opened there nobody botherd to really try to help me there so if i can get an answars here that is 
 
much more important for me that what the developers would do or not but like i said it really of no consoqwences so to speak because i gave up
 
8.10 is a good version but too old for me i love new software and 8.10 compare to ten is a world apart and 9.04 and 9.10 are not much diffrent
 
then 8.10 except thet there not at all stable i can't even connect via pppoeconf and with 10 and 8.10 i can.

---

