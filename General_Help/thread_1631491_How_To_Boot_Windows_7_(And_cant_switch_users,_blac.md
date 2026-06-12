---
title: "How To Boot Windows 7? (And cant switch users, black screen)"
date: 2010-11-26
forum: General Help
---

### Post by HaGGardSmurf on 2010-11-26
Ok, my first and most important problem:

when I turn on my computer, this is what I see:

[http://i140.photobucket.com/albums/r28/HaggardSmurf/IMAG0051.jpg](http://i140.photobucket.com/albums/r28/HaggardSmurf/IMAG0051.jpg)

when I click on windows 7 boot loader, nothing happens my screen goes black then it just reload's the boot loader...

Now my second problem:
I have dual monitor's I had it set so they both displayed different images, and had my panels all setup nicely, I rebooted into ubuntu and now my screen's are mirrored and when I try and change them it tells me I need to logout then login. When I try this, I logout and all I see is a black screen nothing happens so I need to reboot.

---

### Post by HaGGardSmurf on 2010-11-26
I should add, windows is installed I have not deleted the partition or anything, I've watched a couple movies from my win 7 partition. I think I overwrote the windows boot loader?

I need to get into windows 7 as I use it for school work and I need to get some work done.

[COLOR=Magenta]I think I know what I did wrong while installing ubuntu, the device for bootloader installation that I selected was windows 7 loader. I though I selected my primary HDD as the device, but thinking back now I selected my windows 7 boot loader. How can I fix this?

[COLOR=Black]I was reading around and found out I need to use my windows 7 disk, then select repair and use dos to repair my MBR. I want to repair this, but I still want to be able to boot ubuntu. I have a feeling repairing this through windows will make it so win 7 automatically boots.[/COLOR]
[/COLOR]

---

### Post by xXPetabyteXx on 2010-11-26
you aren't supposed to click Windows 7 Boot Loader, pick the top one :)

---

### Post by emoguitarist06 on 2010-11-26
> **HaGGardSmurf said:**
> 
[COLOR=Magenta]I think I know what I did wrong while installing ubuntu, the device for bootloader installation that I selected was windows 7 loader. I though I selected my primary HDD as the device, but thinking back now I selected my windows 7 boot loader. How can I fix this?
[/COLOR]

You can reinstall grub2 using a live CD
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2")
see if that fixes the problem

---

### Post by HaGGardSmurf on 2010-11-26
Well I just figured this out.

I have windows XP listed, and thought how can that be if windows xp is not on this hard drive, so I selected it and it boot my windows 7.

Now I was initially going to install ubuntu on a different computer, and was just installing on this to test it out, so how do I remove ubuntu from this HDD without effecting my windows install?

---

