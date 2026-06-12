---
title: "Why is linux so hard for me to install?"
date: 2009-10-31
forum: General Help
---

### Post by Cr0n_J0b on 2009-10-31
Sorry, for the rant, but I'm sitting here trying to install 9.10 on my server/desktop and i can't get the F*#$&ing thing to boot off the install disk.  

I swear this happens every single time i try to load any version of Linux.   It all started with redhat, then fedora, then ubuntu.  every version...every time...I end up making like 5 CDs from the images and after hours of frustration, I finally get one that works.

And just to let you know, I always follow the same process.

download image (check)
verify hash (check)
burn image on slowest speed (check)
verify burn (check)
validate that the CD ROM works (check)
put CD in player and attempt to boot (FAIL!)

I HATE THIS!  It really shouldn't be this hard.  I shouldn't have to even worry about burn speeds and hashes...I burn like 15 CD/DVDs a month with no issues.  I burn Windows all the time with no issues...but not linux!

ARGH!

ok...I feel better now.  Thanks

---

### Post by mebigfatguy on 2009-10-31
> **Cr0n_J0b said:**
> Sorry, for the rant, but I'm sitting here trying to install 9.10 on my server/desktop and i can't get the F*#$&ing thing to boot off the install disk.  

I swear this happens every single time i try to load any version of Linux.   It all started with redhat, then fedora, then ubuntu.  every version...every time...I end up making like 5 CDs from the images and after hours of frustration, I finally get one that works.

And just to let you know, I always follow the same process.

download image (check)
verify hash (check)
burn image on slowest speed (check)
verify burn (check)
validate that the CD ROM works (check)
put CD in player and attempt to boot (FAIL!)

I HATE THIS!  It really shouldn't be this hard.  I shouldn't have to even worry about burn speeds and hashes...I burn like 15 CD/DVDs a month with no issues.  I burn Windows all the time with no issues...but not linux!

ARGH!

ok...I feel better now.  Thanks

Brasero is really flaky for me. I haven't figured out when it will work, and when it won't. There's probably better burning software out there, haven't taken the time to look.

---

### Post by albandy on 2009-10-31
try k3b

---

### Post by SteveMcQwark on 2009-10-31
I don't see how your difficulties is making a valid install CD are in any way the fault of Linux... since, in the end, you end up making a valid disk, it is obviously not a problem with the image. Have you ever considered that your burner/burning software might be junk?

---

### Post by bigtom71 on 2009-10-31
> **mebigfatguy said:**
> Brasero is really flaky for me. I haven't figured out when it will work, and when it won't. There's probably better burning software out there, haven't taken the time to look.

I have had really good results with K3B at burning ISO's and would suggest you try it to see if dosesn't save you CD's.

---

### Post by 3DGE on 2009-10-31
I have had good results with Ashampoo Burning Studio, I suggest you use that and make sure you set the burn type to Burn Disk Image (Iso) also make sure your primary boot device in your BIOS is set to CD/DVD.

---

### Post by efflandt on 2009-10-31
Maybe it is a hardware issue (bad or unusual hardware).  I burned 64-bit Ubuntu 9.04 in Roxio (WinXP), and once that was installed used Brasero to burn gparted-live (to shrink my laptop partition) and 32-bit Ubuntu 9.04.  None of those had any issues.

I did manually set up the partitions myself instead of letting Linux mess with them automatically (since WinXP64 beta messed up my disk geometry, and SuSE tried to, but I stopped it before it did).  For some reason some OS's like to change 240 heads to 255 heads.

---

### Post by Cr0n_J0b on 2009-10-31
Argh!!

Well I think I figured it out...

I just burned the "CD" image to a DVD and it works fine...

If I had to guess, I'd say that the 700MB CD image is pushing the bounds of an 80 minute CD.  

I'm just can't understand why they would not shrink the Installation to say 600MB for compatibility.  or at least recommend that people burn to DVD.

I'll try to remember this for the next time I load Ubuntu.

cheers.

---

### Post by flipper9 on 2009-10-31
Have you tried unetbootin for Windows or Linux?  If your computer can boot from a USB Key (dongle, drive, stick), then use unetbootin to install the ISO (or download it for you) to your USB Key and then boot off the USB Key.  It's really faster during the install and you avoid all of the disk-burning issues in the process.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by SuperSonic4 on 2009-10-31
```
cdrecord --overburn /dev/cdrom image.iso
```

---

### Post by enzomatrix on 2009-10-31
> **Cr0n_J0b said:**
> Argh!!

Well I think I figured it out...

I just burned the "CD" image to a DVD and it works fine...

If I had to guess, I'd say that the 700MB CD image is pushing the bounds of an 80 minute CD.  

I'm just can't understand why they would not shrink the Installation to say 600MB for compatibility.  or at least recommend that people burn to DVD.

I'll try to remember this for the next time I load Ubuntu.

cheers.
I've burned both the CD and the DVD. The CD fits in an 80 min Verbatim disc.
Maybe the brand you are using gives less capacity.

---

### Post by Cr0n_J0b on 2009-11-01
> **enzomatrix said:**
> I've burned both the CD and the DVD. The CD fits in an 80 min Verbatim disc.
Maybe the brand you are using gives less capacity.

This is exactly what I'm talking about.  if you have to worry about the brand of CD you are using to burn the ISO correctly, then it's not build correctly IMO.  If there is ANY question about compatability due to size, then err on the side of caution and use a smaller image.

It's just funny to me that only linux installations have such consistent issues with ISO burned disks...at least for me.

I'm sure that there are people out there that have never had an issue with burning and ISO and having it boot correctly...but I'm not one of them.  It has happened with every ISO i've build since rh6.1 ... again...maybe it's just me, but by looking at the advice in this thread, I'm thinking that a lot of people have had this happen over time.

---

### Post by Fraser1987 on 2009-11-01
I use ImgBurn in Windows XP Professional. It's free and good. Try burning the iso at the speed of x5. Always works quite well for me at this speed for anything.

:D

---

### Post by Jazzy_Jeff on 2009-11-01
I always have problems with the live cd's. Something about my hardware. So I always download the alternate install cd and it works great every time.

---

