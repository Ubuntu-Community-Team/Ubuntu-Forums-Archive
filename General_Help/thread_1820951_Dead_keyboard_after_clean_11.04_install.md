---
title: "Dead keyboard after clean 11.04 install"
date: 2011-08-08
forum: General Help
---

### Post by reedplayer on 2011-08-08
Running Acer Aspire One D250 - had keyboard issues on a previous install so I wiped the drive and started from scratch.  Still no response from the keyboard.  To perform the clean install I mounted the Acer hard drive to a MacBook Pro and installed directly to the drive - couldn't install using the Acer because the keyboard wouldn't work.

Any ideas here?  The hardware connection is fine and the keyboard has worked for a couple years.  I saw a bunch of posts about keyboard issues in 11.04 but no general consensus about what to do...

---

### Post by SalHelder on 2011-08-08
Does it work with older versions like 10.04 or 10.10 ?

---

### Post by reedplayer on 2011-09-05
Yes, and it works off and on in 11.04.  For instance, last week it worked for about 2 hours and then cut out, and stayed out after multiple reboots.  Today I turned it on and it's currently working.  I'm guessing in a couple hours it'll be dead again.  Not a hardware issue - I've replaced the keyboard, just in case.

---

### Post by reedplayer on 2011-10-03
Any help out there?

---

### Post by kurt18947 on 2011-10-03
It sure sounds like a hardware issue to me.  Do you happen to have another keyboard you could try?  It could also be an issue with the computer itself. I'm not familiar with Acer at all but does the BIOS or setup screen(s) or whatever have a keyboard setting of some sort? Something along the lines of "Set keyboard to legacy mode" or "enable USB keyboard" or something along those lines?  If so , you could try changing that setting and see if it helps.

---

### Post by seawolf167 on 2011-10-03
Does it work full-time in the other operating systems? Or does it cut out there too? If you boot off a live cd of 10.04 LTS and run that for a number of hours does it ever cut out?

My first thought is a loose or bad connection connecting the keyboard to the motherboard since you mentioned that you replaced the keyboard.

If you plug in an external keyboard via the USB port does that keyboard work full-time or does it cut out intermediately?

---

### Post by reedplayer on 2011-10-03
It doesn't cut out at all with a USB keyboard, but works intermittently with both the original OEM keyboard and a replacement keyboard.  I'd be surprised if it's a hardware issue, given that it always works on startup, and cuts out after that (if it were a hardware problem, it should be independent of startup).

I'll check if there are any related BIOS settings, and try booting to another OS to see if the problem persists.

Thanks.

Sam

---

### Post by seawolf167 on 2011-10-03
Maybe there is a package that needs updating because of a known issue? (just a guess)

```
sudo apt-get update
sudo apt-get upgrade
```or a new[er] kernel that would have the components required to work? [How-to]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/"). Make sure to make a backup with something like [Clonezilla ]("http://www.clonezilla.org")before you update *just-in-case.*

---

### Post by reedplayer on 2011-10-07
ok-

Kernel was up to date, along with all packages.

I didn't see a setting in the BIOS for keyboard.

I installed a copy of Lubuntu 11.04 alongside Ubuntu and the keyboard didn't work in that either.  I suppose I could try installing a copy of 10.10 and try that too...

Short of doing that, does anyone have any ideas?  I checked the hardware connection and it's clean and tight.

---

