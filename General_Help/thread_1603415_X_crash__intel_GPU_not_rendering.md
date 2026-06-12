---
title: "X crash / intel GPU not rendering"
date: 2010-10-22
forum: General Help
---

### Post by gunsten on 2010-10-22
Hi

I had some problems after updating to Ubuntu 10.10 - Maverick Meerkat.

Initially, it seems the X-server didnt start at all - after reboot I just landed in a terminal couldnt reach the GUI. After some trial and error I got the GUI back by removing this from /etc/default/grub:

```
GRUB_CMDLINE_LINUX="nomodeset acpi_backlight=vendor"
```Or more accuratelly, what made the X-server start after boot was removing the "nomodeset" tag.

Now, this was a fix to an older issue with the screen backlights: Before this line in grub config file, I couldnt adjust the screen brightness. Now, without "nomodeset", but with the "acpi_backlight=vendor" left there, I can adjust the brightness slide, but the screen is not reacting. Can someone enlighten me? Why isnt X-server starting when I have the "nomodeset" tag? Why cant I adjust screen brightness without it?

Now, this isnt my main issue at the moment. The biggest problem is that my integrated GPU Intel GMA 4500MHD isnt rendering!

glxinfo returns this:
```
name of display: :0.0
Segmentation fault

```Now this wasnt an issue with 10.04. I've tried a few things by creating an xorg.conf file, trying with both disabling and enabling KMS (sorry, Im not really familiar with this stuff, but I have found out that the KMS is responsible for choosing drivers for the GPU early in the boot process) and now I just deleted it again and have noticed little (or no) effect.

I have tried to make this post as clear as possible, but Im dealing with things I dont really know enough about. I'd appreciate any help you can give me, including some enlightenment about what I have described - especially if it sounds like I have gotten something wrong.

---

### Post by gunsten on 2010-10-23
bump

---

### Post by gunsten on 2010-10-23
Okay, so I found this relevant post: [http://ubuntuforums.org/showpost.php?p=9964283&postcount=6](http://ubuntuforums.org/showpost.php?p=9964283&postcount=6)
(I don't think that my post is an unnecessary duplicate, since my X-server actually starts at the moment)

So this guy has intel graphics and experienced similar problems as I, and solved it by using a *mainline *kernel. 

On the Ubuntu wiki page: [https://wiki.ubuntu.com/Kernel/FAQ](https://wiki.ubuntu.com/Kernel/FAQ)
I read that:

[B][SIZE=2]Does the kernel team support the mainline kernel builds?[/SIZE]

The mainline kernels builds are produced for debugging purposes and therefore come with no support.  Use them at your own risk. [/B]   

Since I know little about kernels, I want to avoid trying this option. Any advice?
Do you think I can expect a fix to my issue in an upcoming kernel update?

Also, I have tried older kernels already installed with no luck.

---

### Post by gunsten on 2010-10-24
bump (and at the moment Im trying to figure out how to configure the driver with KMS instead of through xorg.conf)

---

### Post by gunsten on 2010-10-24
So I found a solution to the hardware acceleration issue: It was a driver ,fglrx, for ATI Radeon GPU's, have no idea when that was even installed, which had interfered with a [I]kernel component.

---"[/I]The -fglrx driver does not always uninstall properly, and leaves bits behind which can cause failures in -ati. " -- [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
So it wasnt currently installed in the system, but since it seemed to be a common problem to some graphics driver issues (not with intel cards though, Im confused) I gave it a shot, following the above guide on purgeing fglrx.

So I conclude this in the case that it can help someone in the future:

[LIST]
[*]I couldnt boot into the gnome-session since X-server wouldnt start properly. This was probably because a flag in grub configuration was conflicting with KMS, resulting in the graphics driver not initialized properly. Removing *nomodeset* in /etc/default/grub on line *GRUB_CMDLINE_LINUX="nomodeset"* let the X-server start properly.
[*]Somewhere when I tried to fix my issue, I must have installed the fglrx package with drivers to a different video card. Even after uninstalling, traces of this conflicting driver was left and disturbed the intel driver. Purging the system from fglrx solved the hardware acceleration issue.
[/LIST]
If in fact this does help someone else, please drop me a line in a pm. I'm just curious.

---

### Post by Bor1s on 2011-01-18
Thank you very much sir. I have been trying to solve my openGL issues for two days now. Finally I asked my roomy to take a look. So he noticed your post and fixed my problem. Thank you very much :)

---

### Post by Bor1s on 2011-01-18
Thank you very much sir. I have been trying to solve my openGL issues for two days now. Finally I asked my roomy to take a look. So he noticed your post and fixed my problem. Thank you very much :)

---

### Post by Bor1s on 2011-01-18
Thank you very much sir. I have been trying to solve my openGL issues for two days now. Finally I asked my roomy to take a look. So he noticed your post and fixed my problem. Thank you very much :)

---

