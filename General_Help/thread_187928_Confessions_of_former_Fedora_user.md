---
title: "Confessions of former Fedora user"
date: 2006-06-03
forum: General Help
---

### Post by Pawel Stolowski on 2006-06-03
I had been Fedora user since FC3 through FC4 and FC5 but decided to give the latest Ubuntu a try. I installed a beta release of Dapper a few weeks ago and I have to say - wow, I'm sold! Now, after upgrading to the final release I must say this is the most friendly distro I've ever tried (and believe me I've tried a few in my ~10 years linux experience).  Frankly speaking, each time a new release of Ubuntu was born, I was trying it but with no luck. Not with Dapper  - it will stay on my HDD!
What I like most:
- no single problem with my hardware (except for scanner and minor grub issue - see below): nvidia accelerated driver, printing with hp6540, sound - everything just works. I even gave my wireless Planet card a try (acx-based) and guess what - it was enough to go to GNOME network administration, set SSID and IP and it works! The firmware was already there! But what impressed me most was hibernation - it works too! Amazing.
- large amount of software - non-free software is easily available (e.g. flash, nvidia driver, acrobat, vmplayer, mp3 codecs). This is just soo great - no more looking for external repos! You have a ready-to-use system in just a few minutes.
- software updates with gnome applet - very nice!

As I mentioned, the only issue was with grub. I've two HDDs - one IDE (/dev/hda) and one SATA (/dev/sda). I changed the drive order in BIOS so that sda is first in the boot order (it contains the root linux filesystem) and it worked fine in Fedora. But Dapper installer didn't allow me to change hdd order - it just set root device to (hd1,0)  which made the system unbootable. I had to manually specify the root device when booting the system first and then make the changes permanent in /boot/grub/menu.lst. As on scanner, I needed to manually install the firmware and adjust sane configuration file. Not much hassle, but may be a showstopper for a novice user.

The only thing that I liked in FC was better fonts. I have no idea what the difference is between Ubuntu and FC with regard to fonts, but in FC they just look better. I guess it has something to do with font rendering. Any ideas?
Besides that, Dapper is great distro! Thanks to the developers, goodbye to Fedora! I'm converted ;)

---

### Post by givré on 2006-06-03
Welcome in our community.
If you want to have better font, you should follow this guide [http://www.ubuntuforums.org/showthread.php?t=180647](http://www.ubuntuforums.org/showthread.php?t=180647) 
which is a summary of what we discuss on this guide
 [http://www.ubuntuforums.org/showthread.php?t=178737](http://www.ubuntuforums.org/showthread.php?t=178737)
It works incredibly well with me

---

### Post by Czak on 2006-06-03
Hi Pawe&#322;,

Not only do we come from the same city, but we have similar feelings about Ubuntu as well :)
I've been using FC5 for the past few weeks and I installed Dapper Drake on June 1st. And I don't think I'm coming back to Fedora anytime soon. The way everything works and how everything is packaged and in the repos is just unbelievable. That's a massive amount of work put into the distribution and you can tell.

About the fonts - that's one thing that Fedora does better. I tried the patches mentioned by givré, and they do give a better clarity overall, but they are intended for use with subpixel rendering. In FC, I used standard greyscale antialiasing and it still looked better.
And with some fonts, they don't improve much for me. 

For example, the default fonts in FC are Luxi family (they're in multiverse - package ttf-xfree86-nonfree). However I try, they look gross in Ubuntu :(
Maybe I'm doing something wrong?

---

### Post by caldevil on 2006-06-03
i was using fedora too and my only gripe with ubuntu was 'not so better font'. But after some tweaks as mentioned in the post above, i got almost as good fonts (if not better) as in fedora. Also make sure instead of subpixel smoothing you have best shapes as the option in font rendering.

---

### Post by David Corrales on 2006-06-03
[QUOTE=caldevil]i was using fedora too and my only gripe with ubuntu was 'not so better font'. But after some tweaks as mentioned in the post above, i got almost as good fonts (if not better) as in fedora. Also make sure instead of subpixel smoothing you have best shapes as the option in font rendering.[/QUOTE]

Care to share your solution :)?

---

### Post by nix4me on 2006-06-03
Fedora is a good distro however it is nowhere near as fast and smooth as Ubuntu or Debian.  Granted Gentoo is still my speed king, Ubuntu is the premier desktop Linux OS.

nix4me

---

### Post by caldevil on 2006-06-04
[QUOTE=caldevil]i was using fedora too and my only gripe with ubuntu was 'not so better font'. But after some tweaks as mentioned in the post above, i got almost as good fonts (if not better) as in fedora. Also make sure instead of subpixel smoothing you have best shapes as the option in font rendering.[/QUOTE]
Actually I installed msttcorefonts (search forums, there is a how to for that) and did some tweaks as mentioned in the 2nd posting. After that I am using Tahoma and Aerial fonts which look very good on my computer. Also make sure that your screen is set at 96 dpi.

---

