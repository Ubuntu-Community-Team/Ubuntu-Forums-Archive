---
title: "Trouble mounting MP3 player"
date: 2006-04-20
forum: General Help
---

### Post by andypaxo on 2006-04-20
I have just purchased a Philips PSA 610 (3GB MP3 / WMA player), and I'm having trouble accessing it with Breezy.
When connecting it to the computer via USB, the camera 'wizard' appears. After closing this, there is no further sign of the hardware. (No icon on desktop or folder in /media).
If I do attempt to import photographs, I get the message "An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device."

I do have a USB memory stick which works - but no such luck with the MP3 player - any help would be very gratefully received. :)

---

### Post by marks_linux on 2006-04-20
is the 'disk' on the mp3 player formatted? normally there needs to be a filesytem such as fat (vfat).

Assuming gnome go to system -> Administration -> disks

what do you see there?

M

---

### Post by andypaxo on 2006-04-25
Ah, didn't see your reply - thanks for helping out.
It turns out that the mp3 player isn't one that can be mounted as a disk at all. It uses something called MTP - A fairly new system that's only designed to be used with WIndows Media Player 10 :S
But there are people working on hacking this stuff - so there is hope :)

---

