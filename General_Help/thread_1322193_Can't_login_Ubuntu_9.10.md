---
title: "Can't login Ubuntu 9.10"
date: 2009-11-10
forum: General Help
---

### Post by anberside on 2009-11-10
After installing 9.10 and using it for a while, i tried to login one day and after i put in my username and password the login stops and there is a small white terminal in the upper left hand corner of my screen. 

I couldn't figure out the problem and reinstalled ubuntu, but this problem happened again the first time i tried to restart. 

Does anyone know how to fix this? Thanks for any help!

---

### Post by garvinrick4 on 2009-11-10
contrl/sys rg/b   will reboot.

when system is in boot sequence. Boot in same kernal in safe mode.
There should be a fsck  option. Use it.
If does not work boot safe mode and get into a shell and type "fsck" in terminal.
Without quotes.   All we are trying to do is the simplest method of repairing kernel
if that is the problem.  Post results, there is always an answer.

---

### Post by anberside on 2009-11-10
i put fsck into a shell in recovery mode (i think that is the same as safe mode?) and the results were:

/dev/sda5: recovery journal
Clearning orphaned inode 18 (uid=0, gid=0, mode=0100600, size=0)
/dev/sda5: clean 129689/5726208 files, 992875/22876552 blocks

---

### Post by garvinrick4 on 2009-11-11
Does it say tty1 or tty2 or something of that nature.

If it doe's alt/cntl/f7  should give you a desktop.

---

### Post by anberside on 2009-11-11
i put it tty1-tty6 and they are the regular black terminals, but tty7 is just a small white terminal in the top left of the screen

in one of the terminals i tried "sudo apt-get install gnome"

and i got this:

The following packages have unmet dependencies:
    gnome: depends: gnome-desktop-environment (= 1:1.22.2~4 ubuntu8) but it is not going to be installed
    depends: gnome-vfs-obexftp but it is not installable
E: broken packages

any thoughts? does that have anything to do with it?

---

### Post by chichopep on 2009-11-11
> **anberside said:**
> After installing 9.10 and using it for a while, i tried to login one day and after i put in my username and password the login stops and there is a small white terminal in the upper left hand corner of my screen. 

I couldn't figure out the problem and reinstalled ubuntu, but this problem happened again the first time i tried to restart. 

Does anyone know how to fix this? Thanks for any help!

I have exactly the same problem. I installed Ubuntu 9.10 on my desktop and at first everything was all right. Then at some point, I couldn't log in normally any more. When I put my username and password in the login screen, I'm just given it back once and again. At the bottom of the login screen I can switch between "Gnome" and "xterm". When I select "xterm", I can login, but I only receive that small white terminal at the top left. If I boot in safe mode, and I chose the first option given, which I think it is called "resume normal boot proces", I am given the command line. Then I can log in with my username and password and startx, and everything works fine, except that I have to mount manually the extra partitions like the windows partitions or those in an external hard drive. That's the situation.

I've been using ubuntu for a long time, and I always found solutions to any little problem in some forum, without the need to post myself. It is the first time I do so. I would gladly follow any indications anyone may give, so I can perhaps this time contribute to find a solution to this little issue.

Thanks in advance

---

### Post by garvinrick4 on 2009-11-11
sudo apt-get clean

sudo apt-get ubuntu-desktop

sudo apt-get update && sudo apt-get upgrade


sudo apt-get -f install


First one cleans out cache of packages and you can fetch new.

second one installs ubuntu-desktop

third one updates and upgrades packages

fourth will fix any broken prackages if there are any

---

### Post by Guilden_NL on 2009-12-13
> **garvinrick4 said:**
> sudo apt-get clean

sudo apt-get ubuntu-desktop

sudo apt-get update && sudo apt-get upgrade


sudo apt-get -f install


First one cleans out cache of packages and you can fetch new.

second one installs ubuntu-desktop

third one updates and upgrades packages

fourth will fix any broken prackages if there are any

Will not pull desktop, apt-get ubuntu-desktop results in "Invalid operation ubuntu-desktop"

---

### Post by Guilden_NL on 2009-12-13
Have been through the suggestions on this thread, most didn't work and now am in worse shape than when I started.  Am now hung in recovery boot at a script failure, 
chroot:cannot execute /etc/apparmor/initramfs: nosuch file or directoru
Failure: AppArmor profiles failed to load
Done.

Any ideas of what I can do next without reformatting ala Windows' favorite fix, and reloading Ubuntu?

---

### Post by KingRadical on 2009-12-14
> **Guilden_NL said:**
> Will not pull desktop, apt-get ubuntu-desktop results in "Invalid operation ubuntu-desktop"

try this:

```
apt-get *install* ubuntu-desktop
```

---

### Post by AP Muhammed Afsal on 2009-12-19
Tomorow night I tried to change my desktop password which was set when I installed Ubuntu 9.10. I'm a non-technical person and absolute new beginner. I went to PREFERENCE > ABOUT ME > CHANGE PASSWORD route. Twice or thrice I tried, but the HOUR CLOCK-like thing in the UBUNTU continued to "roll" for hours. I don't know wheather the Ubuntu recognised my attempt. Today morning when I did a RESTART, things took a disastrous turn. I couldn't login. I tried more than a hundred times. Most of time I tried with my old password. At least in one attempt I think the computer refused my new password (I'm not sure). I went to some forum and noted down almost all solutions offered by community members. Nothing works. I have some documents and some video stored in my Ubuntu hard disk. Please help me.

---

### Post by QKC on 2009-12-22
Dear All,
I got log in problem also.My errors as below.My ubuntu 9.10 is running all right when I change the Login Screen from System,Adminstration.After that I have got the below error once restart the system and unable to log in

Error:Could not update ICEAuthority file /home/jq/.ICEAuthority
Error:There is a problem with configuration server (/usr/lib/libgconfig 2-4/gconfig-sanity-check-2 exited with status 256

Nautilus could not create the following required folders:/home/jq/desktop,/home/jq/.nautilus

Before running Nautilus,please create these folders,or set permission such as Nautilus can create them

Then they ask to do encryption of the folder which I did and I have noted down the passphrase password.


Please help as I have tons of important docs,picture and video in it.

Appreciate all the help given
Thanks
JQ

---

