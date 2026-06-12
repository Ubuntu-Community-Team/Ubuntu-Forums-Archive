---
title: "Running Ubuntu 10.10 from a jump drive"
date: 2010-12-17
forum: General Help
---

### Post by thedesk on 2010-12-17
I have an old acer aspire one that the hard drive has been cooked. the computers fine other then that, so what I'm trying to do is run it using 10.10 net book installed(not installer but actually installed) on a usb drive. I've created the installer on another jump drive and installed it onto the 8 gig using the aspire. everything goes fine, it tell me to reboot so i do and all i get is a black screen with the curser.It responds to nothing and never moves. Any assistance would be awesome thanks.

---

### Post by MooPi on 2010-12-17
You may have to designate the drive to boot from again. I had a similar issue because the install drive was no longer present and that is what my bios was trying to boot from.

---

### Post by thedesk on 2010-12-17
If you mean the boot order, then it's set to go through usb first. And ya if i leave the install plugged in it goes straight to that, if i take it out is when i get nothing at all.

---

### Post by MooPi on 2010-12-17
Switch usb ports.

---

### Post by thedesk on 2010-12-17
I just tried all 3 usb ports both auto run and manually selecting the right drive and same result. is there something i need to do to the usb to make it bootable maybe?

---

### Post by Failboat88 on 2010-12-17
Leave it on the screen for 15-20mins. I bet it will boot up. I've done it like that and it takes for ever to load. It's really not viable.

---

### Post by akand074 on 2010-12-17
You have it installed on just any USB drive? A lot of them are super slow. You should probably use a high speed one. Though at that, you might as well buy a new hard drive. Here in Canada I can get a decent 320GB 2.5" internal hard drive for 55$.. probably cheaper if your in the US.

---

### Post by thedesk on 2010-12-17
I've had it running for about 1.5 hours and no change yet, i'll just leave it over night and see if it does work. As for replacing the hard drive, it's not worth spending money on. just an oldy i could use for very basic stuff. Had a couple jump drive around so figured this would work.

---

### Post by akand074 on 2010-12-17
> **thedesk said:**
> I've had it running for about 1.5 hours and no change yet, i'll just leave it over night and see if it does work. As for replacing the hard drive, it's not worth spending money on. just an oldy i could use for very basic stuff. Had a couple jump drive around so figured this would work.

Well, it still should work. How did you install it? Perhaps do a manual install. Once you get to that step in the installer, it will open up a partition editor. Select your USB stick from the drop down box (probably would be sdb but you can tell by the size) Just delete the whole disk and then edit it and choose to set it as EXT3 or EXT4, as a primary partition with mount point "/" without the quotations. Click next and it will install it. You could always try an older version of Ubuntu as well.

---

### Post by C.S.Cameron on 2010-12-18
Yes, once you get to Partitioning with a Full install, you need to go to Manual, once there make sure that the bootloader is pointed toward the correct drive.

---

### Post by thedesk on 2010-12-18
Finally working. Did a manual install using ext 3 and put in a swap(over my head but it was complaining about it). what i think was happening is I'd set the boot loader to the usb then do the partitioning. I realized that it reset the boot loader to the internal(dead) hard drive.
Thanks for all your help everyone.

---

### Post by akand074 on 2010-12-18
> **thedesk said:**
> Finally working. Did a manual install using ext 3 and put in a swap(over my head but it was complaining about it). what i think was happening is I'd set the boot loader to the usb then do the partitioning. I realized that it reset the boot loader to the internal(dead) hard drive.
Thanks for all your help everyone.

Glad it worked out. I forgot to tell you to make a swap, you don't really need one but the installer usually complains. You could have just used a small amount of space for it, which I assume you did. 

You should mark the thread as 'SOLVED' using the thread tools at the top, to make it easier for people to find solutions in the future if they have a similar problem.

---

