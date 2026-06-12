---
title: "I ruined initramsfs"
date: 2010-10-05
forum: General Help
---

### Post by bonixavier on 2010-10-05
Hello forums!

As the title said, I destroyed my initramsfs and would like to know if anyone can help me fix my problem.
Before anyone points me to old threads where they recommend to boot a live CD and update initramfs or reinstall Ubuntu, read on please.

**How did I wreck my system?**

I was trying to get the Nvidia driver to run (I mean the one you get to download from their website), but was not being very succesful. I installed it, it crashed with the drivers Ubuntu makes available, my X stopped working (said that no screens were found and that it conflicted with the other installed driver), I unistalled it and got everything working again. Then I'd read some more online and come back to try again.
Then I figured that I could disable the proprietary drivers, reboot again from shell (recovery mode - telinit 3) and that it would finally work. The problem is that now there was another driver (nouveau) in place. The Nvidia installer volunteered to build a modprobe file for me, but I declined. I read their instructions file and then created the file /etc/modprobe.d/disable-nouveau.conf, which blacklisted nouveau and chose its modeset to zero. However, that didn't disable nouveau - I could tell because bash was operating in the 1440x900 resolution, which it had never done before.
I went back to the readme file and saw that it could be initramfs that was loading nouveau and decided to change its config file, changing the option of most modules to list (IIRC) then typed update-initramfs -u. Goodbye Ubuntu!

**How can I fix my system?**

If everything else fails, I can simply re-install it. I have a separate /home partition so it's not like I'd lose my files or something. That means I'm not really worried about this problem and, as I have other OSs here, my PC is still functional.

**So why the heck am I creating this thread?**

My hope is to get better educated in the inner mechanics of Linux. One of my boots is to Slackware because it forces me to learn how things work (as you can see, I'm still a noob). Ubuntu is my favorite, but it gives me most things ready so I have 100GB to Ubuntu and 15GB to Slack as my Linux elementary.
Ubuntu is now booting directly to initramfs and it's a different shell, called ASH. There must be a way to fix my problems from there or it would simply give me a message saying something like "You have totally destroyed your computer! Contact your friendly nerd ASAP because you have rendered your system inoperable! Mwahahahaha!!!!"
So tell me friends: is it doable to fix the system from there? If so, does anybody care to guide me or post a couple of links so I can educate myself? I don't mind reading and this is the best opportunity for learning that I've had in a while.

Thanks in advance.

PS. Is this the right place to post this thread? If not can anyone tell me where it should be so I can ask a mod to move it?

---

### Post by coffeecat on 2010-10-05
This:

> **bonixavier said:**
> Then I figured that I could disable the proprietary drivers, reboot again from shell (recovery mode - telinit 3) and that it would finally work. The problem is that now there was another driver (nouveau) in place. The Nvidia installer volunteered to build a modprobe file for me, but I declined. I read their instructions file and then created the file /etc/modprobe.d/disable-nouveau.conf, which blacklisted nouveau and chose its modeset to zero. However, that didn't disable nouveau - I could tell because bash was operating in the 1440x900 resolution, which it had never done before.
I went back to the readme file and saw that it could be initramfs that was loading nouveau and decided to change its config file, changing the option of most modules to list (IIRC) then typed update-initramfs -u. Goodbye Ubuntu!

If you disable the proprietary nvidia driver, you need the open source nouveau driver for your nvidia graphics chipset. I do not really follow everything you have done, but you need to undo everything you did to disable the nouveau driver.

If you have been using Slackware, I would guess that uses the older 'nv' open source driver. Ubuntu has deprecated nv for the newer and more capable nouveau.

---

### Post by bonixavier on 2010-10-05
> **coffeecat said:**
> This:



If you disable the proprietary nvidia driver, you need the open source nouveau driver for your nvidia graphics chipset. I do not really follow everything you have done, but you need to undo everything you did to disable the nouveau driver.
My problem is that I don`t even get to bash anymore, just to another shell called ash and I`d like to know how to fix my problems from there. I misconfigured my initramsfs and now it won`t even boot.
Is it clear what is happening? I don`t think I ever had to explain such a problem before and English is my second language so if what is happening is not clear, tell me and I`ll try to explain better.

---

### Post by coffeecat on 2010-10-05
> **bonixavier said:**
> My problem is that I don`t even get to bash anymore, just to another shell called ash

I don't know why you are getting the ash shell. Since it's a limited shell (I believe) it might be better to boot into recovery mode and work from there. Of course, that might also give you the ash prompt instead of bash, so I really don't know whether what I am about to suggest will work. I must emphasise I am theorising here from what you have posted. It's the best I can do and may not work at all.

First, boot into recovery mode. If you are getting the grub menu, choose the second option. If Ubuntu is the only OS on that machine then the grub menu may be hidden and you will have to press the shift key shortly after the POST screen to get the grub menu. After selecting recovery mode, the boot process will start and you will be presented with a small menu. Choose 'drop to root shell'. I don't think you'll need networking for this but if you have an ethernet cable attached, choose the 'with networking' option just in case.

You will be presented with a root prompt - #. Consequently you don't have to use sudo. Be careful, but since you have some Slackware experience you should know about the potential hazards of being root.

Uninstall the nvidia drivers. (They can always be reinstalled later if you want.)

```
apt-get purge nvidia*
```The nvidia driver installer will have created an xorg.conf. We need to remove that so that the nouveau driver is auto-enabled on bootup. Let's simply rename the file to disable it.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```Be sure to type that correctly. Capital-X in X11, and lower-case x in xorg. And that's ELEVEN in X11.

Now remove your /etc/modprobe.d/disable-nouveau.conf file.

```
rm /etc/modprobe.d/disable-nouveau.conf
```Now regenerate initramfs.

```
update-initramfs -u
```Before you update the initramfs, undo any other changes you may have made and forgotten to post. Now reboot:

```
reboot
```And see if you can boot into a GUI desktop. If you can and you want the proprietary nvidia driver, I suggest you use System > Administration > Hardware Drivers. Why were you downloading the driver from nvidia? I know some people do, but the pre-packaged nvidia driver from the Ubuntu repository (which is what you get with the Hardware Drivers utility) seems to suit most people.

**Edit:** sorry, I may have misunderstood you.

> **bonixavier said:**
> I misconfigured my initramsfs and now it won`t even boot.

Can you clarify? When you try to boot, do you just get an ash shell or will it not boot at all? If it won't boot at all, you need to boot from the live CD, chroot into your broken Ubuntu and do the above. If you want to try that, I might be able to help. It will at least be a learning exercise, but no guarantee that it will fix your Ubuntu.

---

### Post by bonixavier on 2010-10-05
> **coffeecat said:**
> I don't know why you are getting the ash shell. Since it's a limited shell (I believe) it might be better to boot into recovery mode and work from there. Of course, that might also give you the ash prompt instead of bash, so I really don't know whether what I am about to suggest will work. I must emphasise I am theorising here from what you have posted. It's the best I can do and may not work at all.

> Can you clarify? When you try to boot, do you just get an ash shell or  will it not boot at all? If it won't boot at all, you need to boot from  the live CD, chroot into your broken Ubuntu and do the above. If you  want to try that, I might be able to help. It will at least be a  learning exercise, but no guarantee that it will fix your  Ubuntu.All I was getting was the ash shell, even in recovery mode. I must have damaged some fundamental configuration file and it blew my system when I told initramfs to update.
It's fixed now, I reinstalled Ubuntu and the installer fixed it for me. :D

As I couldn't start the recovery mode, I couldn't do what you suggested, but I've taken note of your instructions should I ever need them again (and I think I will, this is probably the 4th time I reinstall Lucid - at least I learned to keep a separate /home partition :)).

This is what I did to finally get the driver to work (guess it may help others):
1- Do not install any proprietary drivers from the repository - they will conflict with the driver you downloaded from nvidia's website.
2- Disable nouveau permanently. In a terminal, type:
```
echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u
```*If you can't install the driver, or it doesn't work, you'll have to restore the old xorg.conf file following coffeecat's instructions. You'll just have to edit it to switch to nv until you can get nouveau back.
3- Reboot and start in recovery mode.
4- Type telinit 3 then type your username and pw
5- Run the script you downloaded sudo sh NVIDIA..... and follow the instructions.
6- Startx then reboot just to see if it's working.

> Why were you downloading the driver from nvidia? I know some people do, but the pre-packaged nvidia driver from the Ubuntu repository (which is what you get with the Hardware Drivers utility) seems to suit most people.The pre-packaged drivers from the repositories don't run as smoothly. For example, if I set it to the high graphical settings, all videos start to lag and freeze. This doesn't happen with the driver I downloaded from nvidia site.
> **Edit:** sorry, I may have misunderstood you.No problem at all. I find it amazing how helpful this community is. Good job everyone who is helping us noobs get a better grasp of this wonderful system. Without the community, I guess I'd have reverted back to Windows a while ago (I may not post much, but I lurk).

Edit: How can I change the prefix to SOLVED? Nevermind, figured it out.

---

### Post by coffeecat on 2010-10-05
> **bonixavier said:**
> As I couldn't start the recovery mode, I couldn't do what you suggested, but I've taken note of your instructions should I ever need them again (and I think I will, this is probably the 4th time I reinstall Lucid - at least I learned to keep a separate /home partition :)).

Have a read up of chroot-ing. When all else fails and you want to mend a broken system, this can be a godsend. If you are installing more than one Linux OS on a multiboot system - say Slackware and Ubuntu - you don't even need a live CD. You can chroot from one to the other.

This is the bit I don't understand...

> **bonixavier said:**
> 
2- Disable nouveau permanently.

You certainly don't have to disable nouveau if you use the nvidia driver from the repository. Perhaps the (later) one downloaded from the nvidia site needs this - I do vaguely remember reading something along these lines. Anyway, I'm glad you're sorted.

---

### Post by bonixavier on 2010-10-05
> **coffeecat said:**
> Have a read up of chroot-ing. When all else fails and you want to mend a broken system, this can be a godsend. If you are installing more than one Linux OS on a multiboot system - say Slackware and Ubuntu - you don't even need a live CD. You can chroot from one to the other.

Sure will. I do have Slack and Ubuntu installed. Speaking of which, I've been getting incompatibility with the kernel version when I try to install the driver there. Let's see if I can fix it. At least I know that if I can't, it's still possible to install nouveau there. :D

> This is the bit I don't understand...

You certainly don't have to disable nouveau if you use the nvidia driver from the repository. Perhaps the (later) one downloaded from the nvidia site needs this - I do vaguely remember reading something along these lines. Anyway, I'm glad you're sorted.
You have to disable it if you want to use the driver from their website. They can't work together, I don't know why.

---

### Post by coffeecat on 2010-10-05
> **bonixavier said:**
> At least I know that if I can't, it's still possible to install nouveau there. :D

Slackware is *very* conservative. They may still be using the older 'nv' driver. I have little experience of Slackware, so I can't be sure. For my "difficult" distro I ran Gentoo for about 18 months. :-s That was fun! :|

Good luck with Slack.

---

