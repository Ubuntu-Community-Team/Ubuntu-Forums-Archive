---
title: "Live Disk WIth GUI Recovery Tools"
date: 2009-08-31
forum: General Help
---

### Post by nerdopolis on 2009-08-31
Hi. I am trying to create a livecd armed with many useful GUI recovery tools (and some command line ones) to recover broken Ubuntu installations, as I don't think there are any live disks that do that. 

I currently have a script based on remastersys that creates a live cd based on a chroot install (it only creates a basic live cd, and not the planned recovery disk just yet) (its attached)

I have a few questions:

1. How do you avoid unnecessary dependencies?  On the chrooted system, I have to install remastersys so that I can have it make a custom backup of the chrooted system (not the full system), and as it was installing, I noticed it pulled in gstreamer. I am sure it also pulled in some other stuff I don't need on this Live CD.

(I do need remastersys though, and even if I did find a different way to make live CD's, I bet the next gtk/gnome app I pull in, will ask for gstreamer, and other ones I did not catch).


      On top of the base install, I install xserver-xorg, linux-generic, and remastersys from the remastersys repository (plus dependencies), and I am already up to 283MB in an iso.
     Knowing that the recovery tools I install are probably going to pull in megabytes worth of stuff, how do I keep this under 650MB? (some disk drives only support 650MB, I don't know how many people have 650MB drives, as they're probably rare, but its good to be compatible)

2. When my live CD boots, its going to chroot into the target system. Its also going to pull a few tricks with mount to make it seem like the tools the CD ships with are on your install probably a using unionfs mount. Whats the best way to allow a chrooted system access the xserver? I know the -ac flag, but that seems a little too insecure as it disables access control to the xserver

3. What are good system/data recovery tools?

Thanks.

---

### Post by madjr on 2009-09-01
> 3. What are good system/data recovery tools?

you may get some ideas from these:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

[http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/](http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/)

---

### Post by nerdopolis on 2009-09-17
How do I make xhost accept any user for 127.0.0.1 only? It seems like I have to define the user that can access the x server, not just the IP.

---

### Post by nerdopolis on 2009-09-30
I solved the xhost problem with 
```
xhost +local:
mount --bind /tmp/.X11-unix /choot_jail/tmp/.X11-unix
```I have union mounts working with aufs. This example is what I used to test it out. I used a system folder in my experment, so be wary if you run it before you change the folders.

```
sudo mount -t aufs -o br:/bin:/media/cdrom none /aufs
```*for anyone curious about union mounts note that **/bin** was read/write folder and **/media/cdrom** was my read only folder. If you had duplicate file names in each union branch (/bin/bash and /media/cdrom/bash, it favors reading the one from the first branch I had (/bin) once I mount it.*


For pulling in less dependacies I found
```
sudo aptitude install <package> --without-recommends 
```EDIT:  --without-suggests seems to be outdated...I also found out that the remastersys script itself pulls in a huge number of packaged when I run it, as it installs Ubiquity. 

What are some good system recovery tools that you like to use, (or wish you could use when your system breaks?) right now I'm looking for tools that can bring a broken system back up more than file system recovery ones. Theres already a live CD for broken file systems I beleive. 

Thanks in advance.

---

### Post by nerdopolis on 2009-10-17
I have the latest live CD making script attached. Its makes an image about 184mb, with a kernel and an x-sever, (and some remastersys tools). The image it creates boots, but it jumps to a login prompt, with no user accounts on the system, so currently its useless.

My question is how to disable the login prompt that appears in the terminal, and replace it with a bash shell. I can't seem to find which init script calls up login.

Another question is there a way to make apt or dpkg have some packages install to the /opt/(programname)/ folder? I'm not going to use the union mount with the whole FS because I thought it over, and the libraries on the two file systems might  become inconsistent with it. 

Lastly what kinds of tools should I stuff the remaining 466mb with? I though of one, and that's bootupmanager, but what are some others?

Thanks.

---

### Post by nerdopolis on 2009-10-28
My script finally creates a live CD that boot to a root shell. Right now, it doesn't create the repair programs, someone who wants to create a totaly customised Live CD may find it useful.

Its attached.

---

### Post by nerdopolis on 2009-11-09
I have the latest script file. This one using remastersys, creates a live cd with a LXDE desktop, and autostarts a few programs (the web browser it calls is the only program that doesn't run as root, but a very important recovery tool ), and creates a 217MB iso.

I have the script file attached, but its nothing to burn a CD yet over as none of the recovery script is in there yet.

I have 433MB left to fill on this ISO, and that 433MB is compressed. can anybody suggest some system configuration/recovery tools should I fill the 433MB with?

Thanks.

---

### Post by t0p on 2009-11-09
> **nerdopolis said:**
> 
I have 433MB left to fill on this ISO, and that 433MB is compressed. can anybody suggest some system configuration/recovery tools should I fill the 433MB with?


There's a bunch of Linux recovery CDs listed here.  Check them out for lists of the tools they include.  You might get some inspiration from their choices.

---

### Post by nerdopolis on 2009-11-23
**t0p**: I looked at those tools, and they all seem to be data recovery tools, or networking tools. I'm looking more for tools that will fix a broke GRUB, Xserver, and things of that nature. Thanks for the suggestion though;-).

Anyway, I have my latest script attached. It now makes a Live CD, that once it boots, you can pick a system to enter, and it goes about mounting it and entering it (with chroot). However, all it does is load xeyes as a test once its in, so its still not anything worth burning. Thats because I mount --bind in the recovery tools into the target system into /opt/recoverytools, and I still don't know all of the environment variables I should set to let the system know they're there. ( [http://ubuntuforums.org/showthread.php?t=1324865](http://ubuntuforums.org/showthread.php?t=1324865) ) 

Currently this test won't work on a 64 bit install, as it's all 32 bit. Making a 64 bit version should be ***very*** trivial, but all I have is 32 bit processors, so I can't test it. ( I would test it on QEMU, with emulated 64 bit, but its understandably too slow. (I tried it.)).


Any help with the environment variables will be appreciated, as thats the last thing I need to know how to do before I can install some recovery tools working.
Thanks. 

Thanks


EDIT: None of these script files above are going to work any more as the remastersys repository I was using went down.

---

### Post by nerdopolis on 2010-02-26
[LEFT]Hi. I finally have the latest Live CD making script attached. It can now import programs into the system now (which opens many doors).

However its only 32 bit, as I have no 64 bit processor to test it on, and currently English only (but I'll try to see what I can do to make the job easy as I can for possible future translators)

It will not detect Wubi installs, and I dont think it can see encrypted installs either.

Lastly there aren't many apps that it has that aids in system repair. I only know of bootup-manager. Does anyone know of any others? thanks.
[/LEFT]

---

### Post by nerdopolis on 2010-02-26
Hi.
Is there a chance that a moderator could move this thread from 'general help' to 'the community cafe' instead? 

Thanks.

---

