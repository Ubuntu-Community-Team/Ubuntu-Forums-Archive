---
title: "[video content] boot issues. help!"
date: 2009-11-04
forum: General Help
---

### Post by Poyntz on 2009-11-04
Hi folks,

The following is a video URL depicting my problem (better than any of my words can describe)

[http://www.youtube.com/watch?v=nfHEx6k08SQ](http://www.youtube.com/watch?v=nfHEx6k08SQ)

Essentially it's an infinite loop of garble in grub (when it starts loading AppArmour profiles), which renders me incapable of logging in and therefore accessing the system.

Actually, I can bypass this situation by entering recovery mode. Unfortunately, however, apt-get update && apt-get upgrade aren't installing any updates/programs which rectify this problem. Also, I can't start X server, even with the startx command in recovery mode. It fails to locate my nvidia graphic driver (which I know exists because I've purged and installed nvidia-glx-173, 180 and 185 separately from the repos to no avail.

The problem is of course compacted by the fact I can't update the kernel to the latest version which could potentially partially rectify the issue. Assuming that it's a result of a partial dist-upgrade (no idea why this is the case given I upgraded the distro via the gnome update manager).

I know you're probably going to label it as an nvidia issue, but that doesn't explain why the boot console text (which isn't rendered by the graphics card) is flashing ballistically on boot. 

Judging by what you see in the video. Please offer a solution on how I can rectify this issue. 

Thanks in advance.

---

### Post by P4man on 2009-11-04
Does your bootloader show unbuntu 9.04 there? Are you sure grub is correct and loading the right kernel?

---

### Post by Poyntz on 2009-11-04
I can guarantee it's loading the old kernel, but I don't know how to fix this :???:

---

### Post by scouser73 on 2009-11-04
Try this and see if it helps you.

Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by Poyntz on 2009-11-04
anything in relation to gnome you mentioned I can't do because my x server is borked. i'll try what you said using aptitude... I have already once tried to install the linux-image packages and failed, but i'll try again.

---

### Post by P4man on 2009-11-05
are you using grub 1 legacy or grub 2 ? Actually it look like you're not using grub at all? I dont know what bootloader that is, but its your problem.

Try installing grub2 in recovery mode if you can access ubuntu's recovery mode from that bootloader. Or install grub from a livecd:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Poyntz on 2009-11-06
ok people. it's working. the sneaky little devil, menu.lst, was configured to load the old kernel. grub obviously wasn't very happy about this and decided to go nuts.

if anyone has the same problem as me (as depicted in the YouTube video), I'd definitely recommend you do this:

1. Grom the grub menu select the Ubuntu 9.10 recovery mode option
2. Select the shell option with networking
2. Enter the following into the shell:
```
sudo apt-get install linux-backports-modules-2.6.31-14-generic linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic 
```
This should give you the applications you need to stop Grub having an epileptic fit
3. Now,
```
sudo vim /boot/grub/menu.lst
```
You may not like this text editor, but it's the only shell compatible one I use and no of (or care about)
*Inside Vim*
4. Click i to enter **Insert** mode
5. Tap the "/" key and enter "Ubuntu 9.10, kernel 2.6.27-7-generic", tap the "Enter" key
it should highlight a line:
"title          Ubuntu 9.10, kernel 2.6.27-7-generic"
6. Tap i to enter Insert mode again
7. Next to where you see "kernel" change the "vmlinuz-2.6.27-7-generic" string to read "vmlinuz-2.6.31-14-generic"
8. Do this again for "initrd" and change the "initrd.img-2.6.27-7-generic" string to read "initrd.img-2.6.31-14-generic"
9. <IF THERE'S SOME STEP THAT I MISSED, CAN SOMEONE PUT IT HERE> (in a reply of course)
10. Tap the keys : followed by w followed by ! then "Enter" (this will save)  [ie, :w!]
11. Tap the keys : followed by q followed by ! then "Enter" (this will exit vim)   [ie, :q!]
*In the shell*
12. Type ```
sudo init 6
```, followed by "Enter", followed by your password to restart
13. After restart, select the Ubuntu 9.10 option

Good luck, folks!

(Sorry for wasting the time of all those that know how to use vim. And yes, I know there's an easier way to replace 2.6.27-7 with 2.6.31-14, but I showed how to do it manually just in case something changes that shouldn't. Just taking illogical precautions here.)

---

