---
title: "One last plea for help!"
date: 2006-06-08
forum: General Help
---

### Post by canadianwriterman on 2006-06-08
When I try to install Dapper, during the install, and after the hardware detection, I get an error message that says: "The CD-ROM drive contains a CD which cannot be used for installation."

I have tried the desktop, alternate and server CDs. I have also tried F4 and selected a low screen resolution, all with the same result. I am using a new machine as described in my signature.

I love Ubuntu, but if can't install it, I will have to give up on it. Any help or ideas will be very welcome. Thanks a million.

---

### Post by aysiu on 2006-06-08
Maybe it's a bum CD? Did you do a checksum on the ISO?

---

### Post by slimdog360 on 2006-06-08
[QUOTE=aysiu]Maybe it's a bum CD? Did you do a checksum on the ISO?[/QUOTE]
Unlikely if he has tried a few different cds, but sorry I cant think of any reason why it would be doing that. Maybe you were just very unlucky with the cd burning and should try the md5sum.

---

### Post by canadianwriterman on 2006-06-08
The checksums are fine and the CD-ROM is detected enough to start the install, just not after the hardware detection stage.

---

### Post by aysiu on 2006-06-08
Or you could be burning at too fast a speed. Try 4x.

---

### Post by elamericano on 2006-06-08
I had the same thing happen on Mandrake 10.1, when it finished uncompressing the linux image, it starts booting that up and failed to detect the CD, thus terminating my installation efforts. It was a very new laptop at the time, with a SATA bus that wasn't fully supported. I never got Mandrake onto that machine.

If you *really* love ubuntu, there might be a way to copy the installer to a second partition and boot it from there. The CD still wouldn't be recognized, but your installation would complete anyway. Then you could then try to fix the problem.

Have you never had ubuntu on that machine? If Breezy works, you could install and upgrade (although I wouldn't expect it to work where Dapper failed.) As for knowing if it's a good CD, just select verify in the burning software and wait the extra time.

---

### Post by canadianwriterman on 2006-06-08
Thanks, elamerican for the idea. This is a brand new HP Media Center. I had Breezy on my old machine, but this new one has SATA and an onboard ATI video card... both fairly deadly to Ubuntu. I have not tried installing Breezy on this machine, but I'll give it a whirl and see what happens.

---

### Post by murataht on 2006-06-08
if you have windows on that machine, try to copy the iso on the hard disk first, on the windows partition. and boot from the alternative cd, go into the expert mode, and you can show the installer the iso file. this worked for me, when my burned cd is corrupted, but enough to boot. good luck.

---

### Post by thingy on 2006-06-08
Hi CWM,

I did a little googling and came across this:

[http://www.unixadmintalk.com/linux-setup/problems-installing-fedora-core-4-hp-4791.html](http://www.unixadmintalk.com/linux-setup/problems-installing-fedora-core-4-hp-4791.html)

After reading all the posts in that URL, can you let us know:

1) If you've got PNP disabled in the BIOS
2) If typing in the noprobe kernel boot parameter during the CD startup has an effect.

I think the problem is that the probing of your IDE/SATA hardware is not working correctly. This could be a kernel bug and distributions/users can prob. work around it via boot parameters/selective loading of modules and such but to figure those out you need to experiment.

Also, can you try the Knoppix cds to find out if they work ok on your Media centre PC.

regards

jin

---

### Post by canadianwriterman on 2006-06-08
Thanks, Thingy. I'll try that tonight.

---

### Post by beerorkid on 2006-06-08
I had this happen a few times.  It was a brand new plextor DVD writer and breezy.  Use an old CD burner and it worked like a charm with the same disk.

Did not have the issue with dapper though.

---

### Post by canadianwriterman on 2006-06-12
Thanks everyone for your help. The issue was that Dapper doesn't support by ATI Radeon Xpress 200 onboard video to the extent that it interferred with the install. I have since installed a GeForce 7400 graphics card with nvidea drivers and the install worked fine.

---

