---
title: "Grub error.......help for newbie"
date: 2010-04-28
forum: General Help
---

### Post by dkdias on 2010-04-28
I'm new to Ubuntu.  I tried to set up an older computer to dual boot windows xp and Ubuntu 10.04 Beta.  On the machine at the time  I had two hard drives. I removed one of the drives recently and put the second drive (200 gig) onto another computer.  I currently have one 60 gig drive on this machine. The error message has always been the same, even after I removed the second hard drive. When I boot the machine I get an error message of:

"error: fd0 cannot get c/h/s values"
"grub rescue>"

The computer is obviously waiting for an input from me? I had partitioned the harddrive during the install process for the dual boot, but I think(?) accidently partitioned the 200 gig hard drive I moved to the other computer?  When I partitioned it, it only let me partition the 200 gig drive?? Anyway what I would like to do is just boot to windows XP.  Windows XP was on the 60 gig hard drive previous to my screw up. If I have to I am willing to reinstall windows xp on this machine if I have to,but I'd rather just make this machine 100% Ubuntu 10.04.... I just have to get there. I have put in a Ubuntu LIve Cd but it doesn't boot when I restart the computer?
Thank you for any and all assistance.......

---

### Post by munky99999 on 2010-04-28
In the grub config it's pointing to hd0,1 or hd1,1 or such.

Swapping around the hard drives can leave you in a sitatuon with it being pointed to the wrong one.

grub 1.5 or 2.0?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You might also want to go into the bios and order your drives.

---

### Post by dkdias on 2010-04-28
> **munky99999 said:**
> In the grub config it's pointing to hd0,1 or hd1,1 or such.

Swapping around the hard drives can leave you in a sitatuon with it being pointed to the wrong one.

grub 1.5 or 2.0?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You might also want to go into the bios and order your drives.

If I need to I can put the hard drive back into the computer, I will gladly do whatever needs to be done. I believe it would have to be 2.0 Grub, because I tried to dual boot Ubuntu 10.04?

---

### Post by Leppie on 2010-04-28
boot off a Ubuntu livecd, download the image here if you don't have any: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
in the live environment, open a terminal and issue these commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
rebooting should take you straight into windows if that is the windows drive.

---

### Post by dkdias on 2010-04-28
> **Leppie said:**
> boot off a Ubuntu livecd, download the image here if you don't have any: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
in the live environment, open a terminal and issue these commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
rebooting should take you straight into windows if that is the windows drive.

I already tried to boot from a live cd and it did not work.  I put the live cd in for Ubuntu 10.04, restarted and the cd did not boot.  I've checked my boot sequence in the bios and the cd is listed as the first one to boot from?

---

### Post by itsjustarumour on 2010-04-28
> **dkdias said:**
> I already tried to boot from a live cd and it did not work.  I put the live cd in for Ubuntu 10.04, restarted and the cd did not boot.

What error message did you get when you tried that bit?  

Reason I ask, is that there is a known bug at the moment thats stopping some people being able to boot from the 10.04 Live CD (see [https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/567899](https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/567899))

---

### Post by Leppie on 2010-04-29
so if there's an issue with the lucid livecd, why don't you try for example the karmic one?

---

### Post by dkdias on 2010-04-29
> **Leppie said:**
> so if there's an issue with the lucid livecd, why don't you try for example the karmic one?

I got it mostly figured out.  Apparently for some reason the master boot record got corrupted.  I reset the MBR by using my original xp install disk. Now I am able to boot into Windows xp or ubuntu.  I haven't had a chance to check on everything else, but my computer is speaking to me again.  :)

I will see if any Ubuntu live cd boots tonight and let ya know.  Thank you everyone for your help!!

---

### Post by dino99 on 2010-04-29
as i understand your first post, fd0 drop grub into trouble, so disable floppy into bios or remove it from the MB plug

---

### Post by dkdias on 2010-04-29
> **dino99 said:**
> as i understand your first post, fd0 drop grub into trouble, so disable floppy into bios or remove it from the MB plug

I disabled the floppy drive in the bios and rebooted with the live cd for 10.04, 9.10 and 9.04 Ubuntu.  The only one that booted from the live cd was the 9.04 Ubuntu?

---

### Post by nitstorm on 2010-04-29
the new ubuntu 10.04 LTS final release is out. Download the torrent and burn it on to a disc and then boot into the live version. once inside the live version you can follow this [link]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")  to restore ur grub2. You should be able to boot back into the beta2. But instead you could check out the final release. That would be my advice since the final release has most of the bugs from beta2 and the RC cleared...

---

### Post by dkdias on 2010-04-30
> **itsjustarumour said:**
> What error message did you get when you tried that bit?  

Reason I ask, is that there is a known bug at the moment thats stopping some people being able to boot from the 10.04 Live CD (see [https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/567899](https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/567899))

Does anyone know if the boot error for 10.04 Ubuntu has been fixed?  I have the beta version 10.04 as of 04/26/2010.  Thanks for your help!!

---

### Post by dkdias on 2010-04-30
> **itsjustarumour said:**
> What error message did you get when you tried that bit?  

Reason I ask, is that there is a known bug at the moment thats stopping some people being able to boot from the 10.04 Live CD (see [https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/567899](https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/567899))

No error whatsoever.  It just goes to the screen that lets a person pick which operating system to boot into. In my case it has Win Xp and Ubuntu as choices, with the Win xp highlighted.  After about 30 seconds it will automatically boot into Win xp.

---

### Post by itsjustarumour on 2010-04-30
> **dkdias said:**
> Does anyone know if the boot error for 10.04 Ubuntu has been fixed?  I have the beta version 10.04 as of 04/26/2010.  Thanks for your help!!

The main bug with booting from the live CD has now been resolved I think - the Ubuntu guys did a last-minute re-spin of the image before releasing Lucid yesterday.  I'd recommend downloading the image again to make sure you're OK.  The other bug (that I referred to earlier on in the thread) was where some people were getting the error message "The installer encountered an unrecoverable error, A desktop session will now be run so that you may investigate the problem or try installing again" when they tried to boot from the live CD - that bug is still outstanding I think, but seems to have just affected people who didn't have a floppy drive, although the installer was still looking for one and then giving up when it couldn't find it.  The solution for people affected by this bug is to go into their BIOS and disable the floppy drive.

Looks like you've maybe been having a different problem anyway, so thats not really relevant to you.  But yeh, I would definitely download the newest ISO image and burn the disc again :)

---

