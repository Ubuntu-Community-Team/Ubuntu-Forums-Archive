---
title: "boot to live cd after full and wubi installation?"
date: 2010-06-29
forum: General Help
---

### Post by sks24 on 2010-06-29
I'm running Windows and 9.04 in a dedicated partition on my HP DV1000 (32bit), and I would like to boot to a 10.04 Live CD to make sure that everything will work with the upgrade.  But, no matter what I try (unetbootin USB, Linux Mint, CDs of both) I can't get the machine to boot to anything other than the HD.

I did a wubi installation of 10.04 on a Compaq CQ laptop and ran into the same problem. I went into the BIOS on both machines and I think I tried all the different settings, but no go.  I must be missing something.  Is working through the BIOS the only way to get one's machine to boot from a usb or optical drive, or is there another trick to it?

Thanks in advance,
Scott

---

### Post by GreenN00b on 2010-06-29
Usually you do it from BIOS.
On some machine there is a key that displays a boot menu where you can select a boot device.

---

### Post by 3Miro on 2010-06-29
The settings should be in the BIOS or alternatively there might be a button that you can press during boot to select "booth device". On several machines that I have seen they use "F12", however, this is not necessarily the case for everyone. You can give it a try.

Another question, are you sure you have burned the CDs properly. What kind of files do you see if you go into the CD from within 9.04 or Windows? How did you make the USB drive?

---

### Post by sks24 on 2010-06-29
It was about a month ago that I last wrestled with this, and your question about burning the CDs raises a point:  I ran checksums from a terminal on the CDs, and got the same bad number on two cds in a row.  But I was able to run the check disc utility on them, they both checked out.  

I used unetbootin, and put the burn with no other files on a 2 GB usb drive

I'll go back and wrestle with the BIOS again.  If I can't figure it out, I'll just write over my 9.04 with the 10.04.  It should be fine, and, if not, I'll fix it.    

Thanks for your help!

Best,
Scott

---

### Post by sks24 on 2010-06-29
re what kind of files I saw: can't remember, and threw away the discs.  My buddy gave me disc with 10.04 on it, and i've yet to try it out.  but I'll get back to you when I do.  

again, 
thanks.

---

### Post by Spr0k3t on 2010-06-29
On a worst case scenario, you could also make a USB boot drive.  Might even be a bit faster to load from going that route.

---

