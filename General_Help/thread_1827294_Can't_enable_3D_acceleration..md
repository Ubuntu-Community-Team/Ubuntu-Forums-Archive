---
title: "Can't enable 3D acceleration."
date: 2011-08-17
forum: General Help
---

### Post by Suushi on 2011-08-17
I do apologize for this thread being created, seeing as how my question  is splattered across the internet. However, i have yet to find an answer  to my dilemma (and i've tried checking everywhere!).

Firstly i'm very new to Linux and i'm currently running Ubuntu 11.04.

Heres my problem. Everytime i try to run Compiz and apply some of the fantastic effects none of them seem to work. 

So  this tells me that something is either wrong with my graphics driver  (because upon a clean install of Ubuntu it says i don't have a graphics card  that can supoort Unity) or i've just simply missed a step in adding one.

I've  checked Nvidia X server only to get the message "You do not appear to  be using the NVIDIA X driver Please edit your x configuration file (just  run `nvidia-xconfig as root)"

I would love to run it in root if (and don't laugh) i only knew how :\

From  the many commands i've found online i've tired to either get to or find  xorg.conf and if i'm mistaken doesn't exist for some reason.

In a nutshell. I can't enable 3d acceleration, i can't find xorg.conf, and i'm a newb.

I currently have 325m Nvidia card on my laptop, if it helps :\ I can give a ton of other information in necessary. 

Any help would truly be appreciated.:grin:

---

### Post by pqwoerituytrueiwoq on 2011-08-17
i assume the driver is installed but not active
use nomodeset in your kernel's boot line
> **P4man said:**
> 
     ```
gksudo gedit /etc/default/grub
```a text editor will open with  the grub configuration file. Near the top of that file you will see  something very similar to this:
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
GRUB_CMDLINE_LINUX=""
```add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**
GRUB_CMDLINE_LINUX=""

```Save the file and exit gedit. 


---

### Post by Suushi on 2011-08-17
Hi and thank you for the quick response. I tried what you said but when i type gksudo gedit /ect/default/grub. A text editor does open however it's blank. 

And on my terminal the response i get after entering that command is "(gedit:1559): GtK-DEBUG: No tracker backend available".

Not sure if any of this seems right (doesn't seem right to me), i didn't want to start copying your solution in to the editor till i confirmed it with you.

Thanks again!

---

### Post by Suushi on 2011-08-17
Anyone with anymore suggestions? I would truly undoubtedly appreciate it.

---

### Post by pqwoerituytrueiwoq on 2011-08-18
```
ls /etc/default/
```post the output

did you update to natty from something before 10.04
if so 
find [I]
# defoptions=quiet splash[/I]
in /boot/grub/menu.lst
and make a similar edit

---

### Post by Suushi on 2011-08-18
Hey there. 

I again tired to type in what you suggested and i get nothing in return. The only thing i get back is "no such file or directory".

It was a clean install.

Some background information that might help you help me.

I downloaded the OS to a USB drive and ran it threw Windows 7(dual boot).

Not sure if it matters but alot of videos i've seen (it could just be movie magic) already seem to have Unity from the get go on their desktop. 

I have it aswell when i launch the demo version of ubuntu. It just seems to no be there after the full install is done and i have to get it from Synaptic. 

Is it possible i have a bad version of ubuntu on my USB? At times it just feels like things are missing, and considering i'm not linux pro, i've been playing with computers for ages.

I've also tried reinstalling about 4 times now.

Thanks again for your continued efforts. :)

---

### Post by mastablasta on 2011-08-18
did you enable the proprietary drivers in the system -->admin -->hardware drivers menu?
 
also carefull what you type in the terminal. in linux files and folders are case sensitive. the easiest way to avoid mistake is to simply copy command from forums and paste it into the terminal. ofcourse it would be nice if the one giving command gave at least brief description of it :-)
 
if you had unity in live mode it should also be installed. it just that the propper graphcis card driver has to be enabled.
 
but there is always a chance that there is an error in your downloaded file that only appeared upon install. to check if this is the case you can verify the donwloaded ISO file like this: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by CatKiller on 2011-08-18
> **Suushi said:**
>  
I downloaded the OS to a USB drive and ran it threw Windows 7(dual boot).

Running it in Windows isn't a dual boot install, it's using Wubi. It's possible that that complicates things, but I don't know because I've never used Wubi.

Have you run the command the error message said to?```
sudo nvidia-xconfig
```

---

### Post by cottfcfan on 2011-08-18
Suushi..
The reason you're having a problem after reading post 3, you are typing:

gksudo gedit /ect/default/grub
instead of
gksudo gedit /etc/default/grub

etc not ect.
Thats why your file isn't coming up.

---

### Post by Suushi on 2011-08-18
> also carefull what you type in the terminal. in linux files and folders  are case sensitive. the easiest way to avoid mistake is to simply copy  command from forums and paste it into the terminal. ofcourse it would be  nice if the one giving command gave at least brief description of it :smile:> Suushi..
The reason you're having a problem after reading post 3, you are typing: 
gksudo gedit /ect/default/grub
instead of
gksudo gedit /etc/default/grub

You know, i realized that when i went to work this morning. Totally my fault. Once i get back home i'll actually type it in correctly this time and post my results.

Thank you again for helping me out guys!

---

### Post by Suushi on 2011-08-19
Alright, i retyped  both of your suggestions pqwoe.

I was able to save the first one however, after closing out of gedit i did get afew GTK-Warrnings in the terminal. Again i'm no linux pro so i'm not sure what to assume with that.

Heres the output from the second suggestion.

```
acpid         bootlogd       cups    irqbalance  ntpdate     saned
acpi-support  brltty         dbus    kerneloops  pulseaudio  speech-dispatcher
alsa          cacerts        devpts  keyboard    rcS         tmpfs
apport        console-setup  grub    locale      rsync       ufw
avahi-daemon  cron           halt    nss         rsyslog     useradd
```Not sure if i'm posting the proper information :X

---

### Post by realzippy on 2011-08-19
I hope you have not set "nomodeset"...
It makes no sense at all here,your problem is a totally different one:
Guess you have optimus graphics.
Please post output from
```
lspci | grep VGA
```

---

### Post by Suushi on 2011-08-19
> **realzippy said:**
> I hope you have not set "nomodeset"...
I did. Should i revert it back to what it was?

And yes it does support optimus.

Heres the output.
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 325M] (rev a2)

```

---

### Post by realzippy on 2011-08-19
Yes,revert it.
You cannot install the nvidia driver,maybe you can install bumblebee
successfully.
Read this:
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by Suushi on 2011-08-22
Hi there. I install Bumblebee however i'm not quite sure where to go with it after the installation completes. Everything still seems the same.

I did a clean install of Ubuntu but like i said, everything still seems the same. Any ideas or advice on what else i need to do with it?

Thanks again for your help! :)

---

### Post by realzippy on 2011-08-22
Check your battery capacity,it should have increased drastically.
Then run any application and check if the nvidia card kicks in;eg:

```
optirun glxgears
```

---

### Post by Suushi on 2011-08-25
Hi, sorry for the lack of updates. I've been quite busy this week.

But everything seems to work as it should now. I can actually see the effects on compiz working. I did notice too that my battery life did go up abit.

You have been a fantastic help to me realzippy! 

Your suggestion with bumblebee was perfect!

Thank you so much, maybe i'll have more lame questions down the road to ask and i hope your on that thread giving those respones :D

Thanks again!

---

### Post by Suushi on 2011-08-25
Btw, is there a way i can change the tags for this thread and add "Bumblebee" and Optimus" I'm sure it would help alot of people out who have my problem. 

Thanks.

---

### Post by realzippy on 2011-08-25
Thread title is ok.Someone (also not aware of optimus linux problem) who can't enable 3Daccel might find it.With Optimus or Bbee as title he won't,'cause he doesn't know about...*if* he knew about,he wouldn't search.
Sometimes it is useful to change title;had to ask a mod,only they can.
Have fun!

---

