---
title: "I Can't boot from my cd"
date: 2011-04-06
forum: General Help
---

### Post by manton1263 on 2011-04-06
[SIZE=2]    I have a ThinkPad a22m. I went into the bios and made the cd dive the first boot device. It refuses to recognise the cd drive. I can't get it to boot a Live Ubuntu CD. I tried using drdos and I can see the see the cd drve and its contents, but it wont run under any dos OS.
    I went into the forums and found this message 

“You will not be able to start the live-cd from DOS. The live-cd is a complete operating system, which neither DOS nor Windows will be able to start. It needs to be started by the BIOS boot process.”

    Is there any way that I can create a floppy disk (3 1/2) that would recognize the cd drive using ubuntu (I have it on desktop machine). Or is there a mini linux os that will fit on a floppy that I could use as as a start up boot drive.[/SIZE]

---

### Post by seawolf167 on 2011-04-06
Just want to make sure that the cd was burned properly - did you "write image to disk" or simply burn the iso onto a cd? In order to be bootable, you'll have to actually write the image to the disk.

During POST you should also be able to hit [F12] (or [F10] in some cases) to see your boot options, then you should be able to select the cd drive as your boot device.

---

### Post by Joe of loath on 2011-04-06
According to thinkwiki, your machine only has 64 or 128mb of memory. So, Ubuntu won't work, even if it boots.

---

### Post by manton1263 on 2011-04-06
[SIZE=2]Actions I've taken so far:
I made a Ubuntu live cd at 1X speed (someone in a forum suggested that an old CD-player might read it if it was burned at a slow speed). After creating it I checked it and it seemed to have all the files, so I assumed it burned correctly.
AT post I tried to select the boot device but it ignores it (it won't boot from the CD drive!).
    Additional info: 
When I right click on 'my computer' (win98) and click on properties it says "GenuineIntel" 
"x86 family 6 model 8 stepping 10" "256.0mg RAM" 
    Some where I thought I had a "Pentium III 800MHz" as cpu speed 
So I down-loaded a cpu identification utility (CHKCPU) and I got: 
................................................ 
 CPU Identification utility v2.08                 (c) 1997-2010 Jan Steunebrink 
 
 CPU Vendor and Model: Intel PentiumIII-E 800-1100 (or 600-1000 mobile) D0-step 
 Internal CPU speed  : 797.0 MHz 
 System CPU count    : 1 Physical CPU(s), 1 Core(s) per CPU, 1 Thread(s) 
 CPU-ID Vendor string: GenuineIntel 
 CPU-ID Signature    : 00068A 
 CPU Features        : Floating-Point Unit on chip  : Yes 
  (deleted some info that didn't appear pertinent) 
 Size of L1 cache    : 32 KB    Integrated L2 cache : 256 KB 
................................................. 
Under device manager it shows that I have a CD-ROM, Teac CD-22OEA.

Thanks to for your rapid response!!
[/SIZE]

---

### Post by Joe of loath on 2011-04-06
Firstly, with those specs I'd be running Lubuntu instead.

Secondly, you may have more luck using loadlin or something similar from a freedos floppy.

---

### Post by manton1263 on 2011-04-06
Joe of Loath
Thanks, that was quick! I tried drdos and msdos. I've heard of freedos, but the the comments in forums specifically stated you can only load Ubuntu from a boot device. 
   I never heard of Lubuntu, where would I get it and how would I install it if I can't boot from my CD-drive .
Thanks for the Help!

---

### Post by Joe of loath on 2011-04-06
That's where loadlin comes in ;) It basically loads Linux from DOS, through a rather roundabout way that causes Linux to replace DOS. You might be able to run GRUB from floppy too, but I'm not totally sure how to do that.

Google Lubuntu ;) You install it the same way you would regular Ubuntu, whether that be from boot floppy or otherwise.

---

### Post by manton1263 on 2011-04-06
Thanks Joe of Loath! I guess I'll have to research loadlin to see how to do that! Thats a good start!
If you have any advice on how to do that I would certainly appreciate that. I'm a newbe and any advice would be great! 
Thanks again, there may be light at the end of the tunnel. I've been at for over a week and I had reached the end of my rope.

---

### Post by Joe of loath on 2011-04-06
Actually, scratch that, I forgot the obvious thing.

Do you have an external hard drive caddy you can slot the hard drive into? Because you can install to the hard drive from a more modern computer, and just slot it in.

---

### Post by manton1263 on 2011-04-06
Joe of Loath! I want to thank you for your effort! The answer to your question is no. I do have an external caddy but not for my notebook hard drive. I have gotten more info (loadlin, Etc) that will keep me busy for a couple of days. I'm currently looking at a forum post that tells how to load ubuntu without a CDdrive it requires writing some stuff to the hard drive, which I'm not sure I can do. I need to mull over where I stand and where to go from here. 
    You gave me a lot of insights and I really appreciate your effort. I'm tenacious but slow. so Ill give me (and you) a break while I regroup.
Thanks again!!

---

