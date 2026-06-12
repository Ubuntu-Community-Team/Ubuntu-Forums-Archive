---
title: "(Lucid) Refuses to boot - WiFi-Stick responsible?"
date: 2010-07-04
forum: General Help
---

### Post by HeartAttack on 2010-07-04
So... I've been on XP for some time to play a little and when I wanted to reboot into Lucid, for some reason it got stuck at that awful purple boot screen, not doing anything. Trying different kernel versions did not do anything.

Recovery mode revealed these three messages:
```
rt2500usb_init_eeprom: Error - Invalid RT chipset detected
rt2x00lib_probe_dev: Error - Failed to allocate device
rt2x00lib_probe_dev: Error - Failed to initialize hw.
```
Now, considering I've used Karmic/Lucid for half a year, but never even got a tiny little bit into what is behind the pretty outside, everything I could find out is that the rt2500-something is my WiFi-stick - so far, so good. But it still doesn't work if the stick is not plugged in and thus I am all out of ideas. It worked fine until, well, just like an hour ago and there's two other computers here, both with the very same WiFi-stick and Lucid, both work.

Help!

P.S.: In the last few days I also had problems with Rhythmbox not saving any configurations and bein unable to mount the NTFS and FAT32 partitions. Might be related?

---

### Post by HeartAttack on 2010-07-05
I'm disappointed.
I thought there'd be someone around here who could help me, but apparently, I was wrong.

Though, I have new information:
Without the WiFi-Stick plugged in, it still crashes (as I said), but for some reason without *any* error messages. If I don't receive any help within, let's say, four days from now, I shall reinstall. Karmic. Because I can't stand having to use Windows XP any longer.

---

### Post by philinux on 2010-07-05
Could be a faulty dongle, can you get into recovery mode with it unplugged?

---

### Post by HeartAttack on 2010-07-05
> **philinux said:**
> Could be a faulty dongle, can you get into recovery mode with it unplugged?

In recovery mode, everything I get is a blinking cursor which vanishes into nothingness after some time. No user interaction whatsoever.

---

### Post by philinux on 2010-07-05
You could use the livecd to chroot in and try to do an update of the system.

```
sudo apt-get update && sudo apt-get upgrade
```

This shows how to set up a chroot.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Have you got home on it's own partition?

---

### Post by HeartAttack on 2010-07-05
> **philinux said:**
> You could use the livecd to chroot in and try to do an update of the system.

```
sudo apt-get update && sudo apt-get upgrade
```

This shows how to set up a chroot.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Have you got home on it's own partition?
Well... no. Home is in /home/*username/, on the same partition as everything else. Except for the stuff I occasionally use on Windows, like music. The update thing... might work. I don't know. Will try it before considering to format the partition, that's for sure.

---

### Post by philinux on 2010-07-05
> **HeartAttack said:**
> Well... no. Home is in /home/*username/, on the same partition as everything else. Except for the stuff I occasionally use on Windows, like music. The update thing... might work. I don't know. Will try it before considering to format the partition, that's for sure.

If you end up reinstalling I would recommend /home on it's own partition. Makes a reinstall so much easier.

I have 12gig for /, 2gig swap as I've got 2 gig of mem and the rest of the drive is /home

From the chroot you can do anything you like to the system as if you were logged in in recovery mode.

---

### Post by HeartAttack on 2010-07-05
> **philinux said:**
> If you end up reinstalling I would recommend /home on it's own partition. Makes a reinstall so much easier.

I have 12gig for /, 2gig swap as I've got 2 gig of mem and the rest of the drive is /home

From the chroot you can do anything you like to the system as if you were logged in in recovery mode.

Certainly sounds promising, as soon as I find time for it I will try. (Which will be wednesday). Thanks a lot, mate.

---

### Post by HeartAttack on 2010-07-05
One more question, for I did not find the link you posted too conclusive on that matter:
I only have a Karmic LiveCD, does it work with that one or do I need to download a Lucid LiveCD?

---

### Post by HeartAttack on 2010-07-05
Triple post! (I wonder... had I read the forum rules, would I still be doing this?)

Whatever.
Since I had nothing better to do, I popped in my Karmic LiveCD and did everything as you said (and of course I also followed the instructions on the Ubuntu Blog), but it did not work. I, however, am currently copying the entire /home folder to my Windows partition so that I do not lose anything when reinstalling. It just copies really, really, REALLY slow. Also, I think I will reinstall Karmic and stay with it, considering the amount of problems I had with Lucid compared to the problems with Karmic. Maybe I will give Maverick a shot, we will see.

Still you provided valuable information (because without your help, the copying wouldn't have worked either), thank you, kind sir, live long and prosper.

---

