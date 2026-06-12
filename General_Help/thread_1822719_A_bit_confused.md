---
title: "A bit confused"
date: 2011-08-10
forum: General Help
---

### Post by new_b on 2011-08-10
I'm gonna bullet point the whole story so you guys don't have to read too much...

1. Installed Ubuntu 11.04 32 bit for my 64 bit laptop to run alongside windows 7. 
2. Installation worked, but had problems booting - it booted sometimes from the grub menu other times didn't
3. Found no solutions for problem so deleted grub and removed the ubuntu OS from disk management. 

Since that time I've been attempting to install the long term support (version 10.04) for a while and nothing's happening. The button to "install" or "try without install" leads me to the ubuntu logo screen with the dots flashing under then a blank screen. The memory stick's light doesn't flash either hence it's not working. I've tried the 32 bit and 64 bit version, downloaded from multiple sources and converted the iso using multiple programs. 

I then tried the 11.04 version again in 64 bit but that didn't work so I tried what I did in the beginning, the 32 bit version and it works. It feels a bit like after the first install my laptop only wants to install the 32bit 11.04 version and is a bit racist (can i say that?) to the other versions so completely rejects them. Why?

Is there any chance if I try to use a cd to boot that version and it may work from there?

And if I can't run 10.04 for some weird reason technical or w.e, can someone reccommend me another REALLY good version for a beginner which is easy to install and doesn't have too many problems. 

Sorry I couldn't make it shorter^^!!

---

### Post by new_b on 2011-08-11
Yeah, it's a 64bit laptop. Here's other details that might be useful :-

64 bit
Toshiba
System model: Satellite Pro C650
BIOS: InsydeH2O Version 1.20
Processor: Intel(R) Celeron(R) CPU 2.20GHZ
2048mb RAM
Directx 11

---

### Post by dino99 on 2011-08-11
you made the good choice (post #1) but if you have tweaked the partitions after installation, then you need to update grub into a terminal :

sudo update-grub

we all have known such troubles when we start with linux (ubuntu), simply take time to understand what is happening, watch the logs (/home/.xserver-errors & /var/log/) to know about errors, read ubuntuforums and check those links below too :)

---

### Post by samigina on 2011-08-11
When you are trying the new install, press Esc right after your Livecd menu selection, this will hide plymouth and will let you see whats going on.

---

### Post by new_b on 2011-08-11
Well, after I deleted it the first time I used EasyBCD to remove grub (As told on a youtube tutorial) then removed the partition which contained ubuntu 11.04 data. That space is currently "unallocated"> 

So I don't understand what you mean by updating the grub :/ The grub menu always looks different anyway each time I reinstall and test a new version from the usb.

**No one has answered my question though - Is there any chance that 10.04 will work from a cd if it doesn't get recognised through the usb? And if not - what are some other good ubuntu versions for a beginner?**

---

### Post by oldos2er on 2011-08-11
What are your system specs? 

Did you run md5sum on the ISOs you downloaded? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Here are some instructions on burning an ISO to CD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by samigina on 2011-08-11
> **new_b said:**
> **No one has answered my question though - Is there any chance that 10.04 will work from a cd if it doesn't get recognised through the usb? And if not - what are some other good ubuntu versions for a beginner?**

Yes, the CD use to be more safe, but slowest.

---

