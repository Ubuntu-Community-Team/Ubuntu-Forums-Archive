---
title: "Bricked my laptop"
date: 2011-02-28
forum: General Help
---

### Post by boneslygrifter on 2011-02-28
Howdy. 

So I'm usually a pretty competent Ubuntu power user and like to do compiling and customize on a daily basis. Today I decided the Plymouth splash screen was lame and out of place with the rest of my desktop, so I decided to install Smart Boot Manager (from the terminal), neglecting to configure LILO before rebooting. I realised my mistake as soon as I did but I was too late. SBM wrote over my mbr, not letting me get any farther than the initialbios loading processes. I attempted everything I could think of to try to boot  into Linux or Windows partitions, but since my mbr was doneskies I was stuck with either Windows in a tizzy demanding the CD or a black screen and cursor. 

Even more panicked, I uninstalled SBM from the menu. This only succeeded in getting nothing but the black screen and cursor after I powered on. 

I run 10.04 with a small unused Windows 7 partition on a Dell XPS 1650 with x64 that uses the phoenix BIOS. I do not have any of my LiveCDs laying around because my friends took them. I am also not in the best mindframe because I just quit smoking a pack and a half a day yesterday and I'm running on no sleep. Which is why I made this stupid mistake in the first place. 

Basically what I need is info on how to restore GRUB2/ my mbr when I get  ahold of a disk, and then quickly fix my mistakes because I use my laptop for work which is due this week.

---

### Post by wilee-nilee on 2011-02-28
Three commands from the live cd, the fdisk to identify the partitions and the other two to put grub in the mbr.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You might want to know about super grub as well.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
You can use this to get in and install grub from there as well with
sudo grub install /dev/sdx
x=the hd no partitions.

---

### Post by Hedgehog1 on 2011-02-28
> **boneslygrifter said:**
> 
... I just quit smoking a pack and a half a day yesterday and I'm running on no sleep...

Just a side note: Congrads on quitting.  It isn't easy at all, but so worth it.

:KS

---

