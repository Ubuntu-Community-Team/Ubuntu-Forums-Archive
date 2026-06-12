---
title: "Help! My Computer is Broken!"
date: 2011-01-24
forum: General Help
---

### Post by userub on 2011-01-24
Hello all,

I have a major problem with my laptop (a Compaq). I dropped a large hardcover book on top of it earlier. I did not think this would be a problem, but when I opened the laptop later, the screen was blank, even though the power light was on. I restarted the laptop by way of the power button. GRUB came on, but Ubuntu itself didn't load.

What keeps happening is whenever I select Ubuntu, the screen goes black with a blinking cursor (as per normal), then either a blank screen or a screen with strange characters and blinking colors comes on.

I've also tried the Ubuntu recovery feature via the GRUB menu. It scrolls down a list, then hangs. The Ubuntu installation disc (with an older version of Ubuntu than the one on my laptop) doesn't work either; the CD loads fine, and the initial screen with the options for installing Ubuntu comes up OK and the Memory Test option works, but both the Try Ubuntu and Install Ubuntu commands lead to a blank screen.

My laptop is dual-booted with Windows Vista, and it isn't working either. It asks me for the Vista installation disc to try and solve the problem (which I don't have).

However, I seem to have access to the GRUB command line feature and the laptop's BIOS screen. The BIOS screen has an option for checking the hard drive for errors, and it found none.

I don't know if the issue is with the hard drive, or the monitor, or the whole computer.

Is there a way to salvage the data on the laptop, or even the laptop itself?

Is there a way to use GRUB's command line to try and fix the system? Or to back up my files?

I appreciate any help I can get. Thank you for reading.

---

### Post by Halzen on 2011-01-24
Sounds like either your FSB (BIOS) or your hard drive was damaged. If you have an Ubuntu live CD, or can make one with another computer, try booting into it.

---

### Post by HereInOz on 2011-01-24
Sounds a bit terminal to me.  If it was mine (which it isn't), and if I had a spare hard disk (which I do) I would stick that spare hard disk in and see if I could run a successful install of Ubuntu.

If I could, then it points to a problem with the original hard disk.  However, if the install fails, then I would guess that the computer has had a motherboard or other internal issue.  There is not much more I can suggest.  

Forgive me for this one, as I can't resist the temptation to say:
If you dropped a large book on it, perhaps it has been Compaqted.  You may all groan now!

---

### Post by userub on 2011-01-24
> **HereInOz said:**
> Forgive me for this one, as I can't resist the temptation to say:
 If you dropped a large book on it, perhaps it has been Compaqted.  You may all groan now!
 
LOL!

Thanks, I needed a laugh.

The book was a hardcover copy of Stephen King's Desperation, by the way.

I don't have a spare internal drive to test with, but I was mulling over  the prospect of using an adapter to try and hook up my laptop's drive  to my desktop. Like this:  [http://www.techrepublic.com/article/extracting-data-from-a-dead-laptop-with-a-laptop-hard-drive-adapter/5160538](http://www.techrepublic.com/article/extracting-data-from-a-dead-laptop-with-a-laptop-hard-drive-adapter/5160538)

It seems promising, but I'm not sure how risky it is to both computers.  My desktop is several years older than my laptop, and I don't want it  damaged if something goes wrong.  That's the last option I'd be using,  if all else fails.

[quote=Halzen]If you have an Ubuntu live CD, or can make one with another computer, try booting into it. 	[/quote]

An Ubuntu live CD is the same as the installation disc, isn't it? If so, I've already tried using Try Ubuntu and Install Ubuntu. Neither one worked.

I'm still hoping for some kind of option with GRUB's command line to fix or back up my files.

---

### Post by Halzen on 2011-01-25
> **userub said:**
> An Ubuntu live CD is the same as the installation disc, isn't it? If so, I've already tried using Try Ubuntu and Install Ubuntu. Neither one worked.

I'm still hoping for some kind of option with GRUB's command line to fix or back up my files.

If you are straight up unable to load a working Linux GUI either way, your chances of going without a hardware replacement are not good at all. If your laptop is still under warranty, it might be a good idea to send that sucker back to Compaq and see what they can do about it.

Oh, and I highly doubt you'll be able to copy your personal files through any command line without successfully logging in. Although I haven't had too much experience with GRUB's command prompt, I'm almost certain that the functions included there are only really for diagnosing and handling boot/kernel issues. Being able to access user files in any way from that prompt would be a pretty big security hole.

---

### Post by piquat on 2011-01-25
Was the drive actually spinning when this happened?  If it was, and you now have these symptoms, I'd agree with the rest, the drive is probably cooked.

---

### Post by userub on 2011-01-25
My laptop is working fine now. I fixed it last night.

Seems the trouble was with a loose connection. I opened the laptop to get a visual of the internal drive, since I thought I would be buying an adapter for it. While I was looking it over, I noticed that one of the two wires which connect it with the laptop seemed slightly higher than the other. I pushed it back down, replaced the cover, and on a whim decided to try Ubuntu again.

Imagine my relief when it loaded without a hitch! I got my files backed up in a hurry, and here I am now. I suppose the book was heavy enough that the impact could knock loose a wire from inside the laptop.

Thanks for your replies, Halzen, HereInOz, and piquat! 

(And I'm still chuckling over that 'Compaqted' line, HereInOz!)

---

### Post by Halzen on 2011-01-25
Whew! That is a relief, although it doesn't speak well for Compaq's (read: HP's) assembly process - I haven't heard of an internal connection being knocked loose in YEARS.

---

### Post by userub on 2011-01-25
To be fair to HP, I bought this laptop a few years ago, and it's taken a lot of damage in that time. The book was likely just the final straw that knocked the wire loose.

---

### Post by piquat on 2011-01-26
Wow, glad to hear it worked out.  Also surprised that a shock that was enough to loosen a wire didn't take out the drive.

---

