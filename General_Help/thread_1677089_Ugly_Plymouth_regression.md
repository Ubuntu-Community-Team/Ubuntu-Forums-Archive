---
title: "Ugly Plymouth regression"
date: 2011-01-28
forum: General Help
---

### Post by claretsfan on 2011-01-28
Bit of a long story, but I recently reinstalled Pardus 2009, dual-booting with Maverick.  The Maverick installation is an upgraded version from a couple of years ago.  All runs well, but it's never upgraded to Grub2, which suits me, as I just about understand the legacy Grub.

I installed Pardus 2009, also with legacy grub, when it was new- a couple of years ago, and Grub referred to Ubuntu 10.10 and to Pardus 2009.  All was well and the Plymouth screen worked as it should, after tweaking for my nvidia card.

Last week I tried the new Pardus 2011 (with Grub2), but found lots of minor problems, including an ugly Plymouth screen now on Maverick when I boot from Grub.  The word "Ubuntu 10.10" with 4 dots underneath, in a fairly ugly font.

So yesterday I reinstalled Pardus 2009, complete with legacy Grub, hoping that this would fix things.  However, the ugly screen persists.

I've tried endless "fixes" and scripts, but I suppose none of them work, because:

-Both installed distros use legacy Grub
-The installed Grub was installed from Pardus- not Ubuntu

I should say that Maverick does boot up ok, it's only a cosmetic problem, but it's a puzzle!

Thanks in advance

---

### Post by Frogs Hair on 2011-01-28
I also have , ugly splash screen syndrome as a result of my Nividia proprietary drivers . I have tried one of the better know fixes out there to no avail.

Plymouth looks fine without the Nvidia drivers . but I need them for my dock so I live with 5 seconds ugly text. I don't know if Pardus has anything to do with your problem.

---

### Post by claretsfan on 2011-01-28
Hi Frogs Hair

Thanks for your reply.

I guess I can live with it, it's made more annoying by knowing that it used to be fine with my previous Pardus dual-boot, which is exactly the same as my current setup really. 

Yes, I use the nvidia driver for awn.  I know that metacity compositing can also be used, but that gives me some strange behaviour in the remaining panel.

I'll keep investigating and report back if I find a solution.

I guess I could somehow install Grub2 into Maverick and then try some of the tweeks on this forum and elsewhere, but that seems both a bit drastic and a bit tricky.

btw you must have some decent hardware to only see Plymouth for 5 seconds.  More like 30- 40 on my ancient setup!

---

### Post by claretsfan on 2011-01-30
I managed to fix this eventually- thought I'd post back in case anyone else has a similar problem (Frogs Hair?).

Here's the legacy grub entry for ubuntu now:

title Ubuntu 10.10
uuid 7e95ea6f-1c5c-40a3-8695-0fde42ed3daf
kernel /boot/vmlinuz-2.6.35-25-generic root=UUID=7e95ea6f-1c5c-40a3-8695-0fde42ed3daf ro splash=silent quiet vga=0x31a
initrd /boot/initrd.img-2.6.35-25-generic

This "ro splash=silent quiet vga=0x31a" appended to the kernel line seems to have sorted it, with a reasonable resolution (1280x1024 at 16bits).  I just played with the different resolutions until one worked (see URL="http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes" for instance).

---

### Post by tredegar on 2011-01-30
[This link]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") fixed it for me.
As a side effect it also gave me back my VTs, so I am happy.

---

### Post by claretsfan on 2011-01-30
Hi Tredegar

I had a look at that, whilst trying to sort it out.  If I had Grub2, I think that would have done it.

I tried to adapt some of what it said for legacy Grub, but didn't really know what I was doing!  Solved it by back-up, restore, test, backup, restore, test over and over again.

Cheers,

---

### Post by tredegar on 2011-01-30
Your problem is currently solved, and you have a link for what to do when you finally end up with grub2.

Best wishes.

---

### Post by claretsfan on 2011-01-30
Yes, I expect I'll have to reinstall (and get Grub2) eventually!

Maybe 11.04 will be the time, what with Unity, Gnome 3 etc coming in.

Many thanks

---

### Post by nerdy_kid on 2011-01-30
> **Frogs Hair said:**
> I also have , ugly splash screen syndrome as a result of my Nividia proprietary drivers . I have tried one of the better know fixes out there to no avail.

Plymouth looks fine without the Nvidia drivers . but I need them for my dock so I live with 5 seconds ugly text. I don't know has Pardus has anything to do with your problem.

Plymouth can look just as nice with NVIDIA as other cards, I have an NVIDIA geforce 8600M and have the Kubuntu plymouth *not the text version* working just fine @1280x800 -- my native res.

Add these two lines to your grub.cfg:
GRUB_GFXMODE=1280x800
GRUB_GFXPAYLOAD_LINUX=1280x800

run update-grub and uninstall the text version of the ubuntu plymouth theme.

---

### Post by claretsfan on 2011-01-30
Hi Nerdy!

Still using legacy Grub here (see above).  One long upgrade from jaunty (from memory).  I think your suggestion is for Grub2?

Many thanks,

---

### Post by nerdy_kid on 2011-01-30
I am using Grub2, yes, but it should work fine for legacy grub too AFAIK.  Just edit your menu.lst file instead, I think the config lines are the same.  Make sure there are no errors when you run grub-update, or your pc might not boot.

---

### Post by claretsfan on 2011-01-30
That's interesting- I didn't know that!

I'm not on the right machine just now, so I'll have a try tomorrow.  I'll let you know.

Thanks for the advice Nerdy

---

### Post by Frogs Hair on 2011-01-30
> **claretsfan said:**
> I managed to fix this eventually- thought I'd post back in case anyone else has a similar problem (Frogs Hair?).

Here's the legacy grub entry for ubuntu now:

title Ubuntu 10.10
uuid 7e95ea6f-1c5c-40a3-8695-0fde42ed3daf
kernel /boot/vmlinuz-2.6.35-25-generic root=UUID=7e95ea6f-1c5c-40a3-8695-0fde42ed3daf ro splash=silent quiet vga=0x31a
initrd /boot/initrd.img-2.6.35-25-generic

This "ro splash=silent quiet vga=0x31a" appended to the kernel line seems to have sorted it, with a reasonable resolution (1280x1024 at 16bits).  I just played with the different resolutions until one worked (see URL="http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes" for instance).

Thanks for posting !

---

### Post by Frogs Hair on 2011-01-30
> **tredegar said:**
> [This link]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") fixed it for me.
As a side effect it also gave me back my VTs, so I am happy.

That is the method I used , it is better , but the text looks bookman old style fonts.

---

