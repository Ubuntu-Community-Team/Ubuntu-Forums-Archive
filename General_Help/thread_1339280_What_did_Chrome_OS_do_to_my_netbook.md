---
title: "What did Chrome OS do to my netbook?"
date: 2009-11-27
forum: General Help
---

### Post by murphykieran on 2009-11-27
I downloaded a Google Chrome OS image and followed instructions I found  online to install it to a 4Gb USB memory stick just to check it out.

So I did that, shutdown my laptop, started it up and told it to boot from the USB key, and it booted up into Chrome OS. So I played around with it for a while, just browsing the web and what have you.

I then hit the power switch, and the laptop shutdown as you'd expect.

I removed the USB key, started up the laptop, went into the BIOS and put the boot sequence back as normal so it would automatically boot straight to the hard disk.

And the laptop boots up... to the Chrome OS login screen!  With no USB key attached.  I can only get back into Chrome OS now and there's no sign of Ubuntu anymore on the laptop.

Did I somehow screwup the installation and install it to the wrong drive (the internal 80GB HDD instead of the USB key)?  I'd be very surprised because the instructions I followed showed how to identify USB drives to use in the command line instruction needed to install to a USB key.

I didn't have anything particularly important on the laptop apart from a couple of days worth of personal photos I'd downloaded off my camera that I had yet to transfer to my main PC.

Anyway, I assume if I want Ubuntu back I'm going to simply have to reinstall it from scratch and any files I want off the laptop are gone because I assume the file tables would have been blitzed if a new OS was simply written to the hard disk drive?

---

### Post by Brandon Williams on 2009-11-27
Photos off a camera? Any chance you've got an SD card inserted and that the machines is running off the SD card?

From within Chromium OS, open an xterm (Ctrl+Alt+T) and run mount with no arguments to figure out which device is mounted as the root filesystem. If it's the hard drive, as you suspect, then you're right that you've lost the files on the drive and will just have to reinstall Ubuntu. It might be possible to get some of the files back, but that would be a time consuming and/or costly process.

---

### Post by murphykieran on 2009-11-27
Thanks for the suggestions, but I've just realised what I did wrong.  Looking back at the instructions I used, I obviously screwed up when selecting the drive to install Chrome onto and actually installed onto the internal HDD.

It's okay though, the SD card is still plugged into the laptop's card reader and I hadn't reformatted it yet, so I still have the photos I thought I'd lost. 

Reinstalling Ubuntu is an easy enough job so no long term damage done.

I iz an idiot!

---

### Post by SeanBlader on 2009-11-28
Using virtualbox would've made that easier and safer. I've found building VM's to be fairly easy. In fact I may get around to trying the netbook remix, or chromium os eventually in a VM.

---

### Post by hibliss on 2009-11-30
There is an image of Chrome OS ready to go on The Pirate Bay.

Here it is - [http://thepiratebay.org/torrent/5179139/Google.Chrome.OS.VMDK.2009_ExtraTorrent_-0b5c3n3]("http://thepiratebay.org/torrent/5179139/Google.Chrome.OS.VMDK.2009_ExtraTorrent_-0b5c3n3")

You can just point VirtualBox to the image and it will load as is.

---

### Post by t0p on 2009-11-30
> **hibliss said:**
> There is an image of Chrome OS ready to go on The Pirate Bay.

Here it is - [http://thepiratebay.org/torrent/5179139/Google.Chrome.OS.VMDK.2009_ExtraTorrent_-0b5c3n3](http://thepiratebay.org/torrent/5179139/Google.Chrome.OS.VMDK.2009_ExtraTorrent_-0b5c3n3)

You can just point VirtualBox to the image and it will load as is.

The Pirate Bay is not exactly the best place to get software from.  Don't get me wrong, I think The Pirate Bay is great, I've got a few things from there.  But it would be preferable to get the .iso image from an official source.  And since it's open source, there should be no problem to getting an official image.

I don't have the right download link to hand.  I will repost once I've found it.

**EDIT:** download links and build instructions available [here]("http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions").  But I can't see an image for a virtual machine. There are instructions to *create* a VM image; but no ready-made image.   So maybe The Pirate Bay is the best place after all...

---

