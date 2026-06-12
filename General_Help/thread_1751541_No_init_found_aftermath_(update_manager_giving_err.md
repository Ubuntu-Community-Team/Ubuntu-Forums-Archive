---
title: "No init found: aftermath (update manager giving errors)"
date: 2011-05-06
forum: General Help
---

### Post by astrobob.tk on 2011-05-06
Hey there,

Just a an hour or so ago I put my 10.04 into Hibernate mode & then booted from my Knoppix 6.5 usb; after logging out & removing the usb (seems i removed it sooner than I should though Knoppix has powered off already). Not eactly sure what happened after that but i remember it hanged, manually powering off the system & then booted the hibernated system but directly after grub, I get the error msg

```

No init found. Try passing init= bootarg
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```I passed ```
init= bootarg
``` but nothing happened

I tried the "recovery" from the grub menu but problem persists (isn't recovery supposed to fix the problems by going back to an earlier point before the problems arise ?)

Anyways, I logged in to Knoppix again & browsed online & this forum for a solution; apparently no standard solution exists & many guys are facing this problem.

Just when I though to try to run
```
sudo fsck/dev/sdaX
``` after rebooting & arriving at the shell again, the system was able to boot again on its own (:D). It was checking the disk for errors & found some (it seems), I waited a while for the /tmp to be mounted & then i was promoted to login which of course i did.

I am writing this now while i copy my home directory just in case of any further issues that might arise.

In this thread i therefore request help in the aftermath of this.

What should I do now ? Am I prone to further problems as a result of this ?

I note that i tried updating the system (in terminal, update-manager & synaptic) but i get the error(s) as seen in the attached screen shots.
The last screen shot shows the error i get when I try to collect data for a bug.

Your help is appreciated

==Update==
Regarding
> 
I note that i tried updating the system (in terminal, update-manager  & synaptic) but i get the error(s) as seen in the attached screen  shots.
The last screen shot shows the error i get when I try to collect data for a bug.

This has been solved by simply renaming /var/lib/dpkg/status-old to /var/lib/dpkg/status

---

### Post by Bearly Able on 2011-05-07
I have a similar problem, for no apparent reason.  The system was fine when I shut down, but when I tried to restart, I had the same error message as Astrobob.  I also tried passing ```
init= bootarg
```without success.  I've made several attempts at rebooting but the result is always the same.  I'm using a live CD to search the forums, but I can't find any kind of solution.

It looks as if I'll have to do a fresh install, which is a bit of a pain. :(  I'd also like to know why the problem arose in the first place.

[Edit] I've just tried to mount my Ubuntu drive, and I'm getting the following error:

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

I don't know if that is relevant; my other drive will mount OK.

---

### Post by Bearly Able on 2011-05-08
I burned a Natty CD on my laptop and found I could mount the Ubuntu drive using that.  I then did a fresh install using Natty - and still have more or less the same problem.  I've started a fresh thread [here]("http://ubuntuforums.org/showthread.php?t=1752770").

---

### Post by astrobob.tk on 2011-05-08
It seems its not just an Ubuntu [https://answers.launchpad.net/ubuntu/+source/grub/+question/63005](https://answers.launchpad.net/ubuntu/+source/grub/+question/63005) problem but also a linux problem [https://bugzilla.redhat.com/show_bug.cgi?id=643320](https://bugzilla.redhat.com/show_bug.cgi?id=643320)

> **Lesley Lutomski said:**
> I burned a Natty CD on my laptop and  found I could mount the Ubuntu drive using that.  I then did a fresh  install using Natty - and still have more or less the same problem.   I've started a fresh thread [here]("http://ubuntuforums.org/showthread.php?t=1752770").

In case your system is still there try using the shell to do what I've done; that is,
> by simply renaming /var/lib/dpkg/status-old to /var/lib/dpkg/statusNote that the file might be name differently; run ```
ls
``` to check what files are listed in the ```
/var/lib/dpkg/
``` directory. There should be a "status" something file which should be renamed to "status"; otherwise if there isn't any such files, try googling about it. I passed on some cases where this file did not exist.

---

### Post by jadon on 2011-07-10
I just upgraded from 10.10 to 11.04 (Ubuntu server 64-bit)

I had the issue of "no init found" etc, so what I did was boot into a live CD (I used kubuntu 32-bit desktop) and in terminal:

```
FSCKFIX=yes
```

then

```
sudo shutdown -F -r now
```
Fixed it :D

---

### Post by astrobob.tk on 2011-07-12
> **jadon said:**
> I just upgraded from 10.10 to 11.04 (Ubuntu server 64-bit)

I had the issue of "no init found" etc, so what I did was boot into a live CD (I used kubuntu 32-bit desktop) and in terminal:

```
FSCKFIX=yes
```

then

```
sudo shutdown -F -r now
```
Fixed it :D

I do not think am gona try what you did now as things seem to go fine after last weeks' return of the problem which i solved (& which was more persistent than b4) w/ the command

```
sudo fsck/dev/sdaX
```

& rebooting.

Do you have any idea of why it is not being solved by the Ubuntu community (not to say the Linux community) ? It seems to be a kernel problem!!! :S

---

