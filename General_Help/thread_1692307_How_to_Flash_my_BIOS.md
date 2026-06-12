---
title: "How to Flash my BIOS?"
date: 2011-02-21
forum: General Help
---

### Post by uaebuntu on 2011-02-21
If I need to flash my BIOS how do I do it in Linux with no floppy disk?

Manufacturer's notes (AMI) says "on a windows machine download and run the .exe file and create a floppy disk, reboot with floppy in place"

I have VMPlayer with Windows XP on it so could run the .exe, but no floppy, only a DVD writer

Any ideas?

---

### Post by Frogs Hair on 2011-02-21
The only other option would be update from USB. Unless the new bios directly affects your hardware or ability to use your computer don't bother with it.

Read the release notes and see if there are any benefits to updating. I have found that bios updates for my mobo are for hardware I have no intention of using.

---

### Post by seawolf167 on 2011-02-21
> **Frogs Hair said:**
> I have found that bios updates for my mobo are for hardware I have no intention of using.

Basically this - the only time I reflash is if it fixes something that currently isn't working or is driving me crazy. If you are updating just to update and keep it current, I wouldn't bother.

---

### Post by Roasted on 2011-02-21
> **seawolf167 said:**
> Basically this - the only time I reflash is if it fixes something that currently isn't working or is driving me crazy. If you are updating just to update and keep it current, I wouldn't bother.

^^^^^^^^^^^

If it ain't broke, don't fix it. I can only think of one occasion where I *had* to flash the BIOS, and that was on Dell Optiplex 740 systems. I was having trouble getting PXE boot to work with that particular Dell BIOS for use with FOG system imaging. What's ironic, is I had to BACKTRACK the version of the BIOS. Example - 2.1.9 didn't work, but 1.1.8 did. Go Dell!

---

### Post by psusi on 2011-02-21
The exe is probably a self extracting archive that also writes the image to a floppy.  It probably has a command line switch you can use to tell it to only extract and not write.  If you can extract the floppy image, then you can burn it to a bootable cd and use it that way.

I'm very pleased with recent Asus boards because they include a flash utility built into the bios.  You just download the rom image and drop it on a cd or usb flash stick, go into the bios, and point it to that file and it flashes.  No need for windows or dos.

---

### Post by uaebuntu on 2011-02-21
Thanks, no intention of playing for the sake of it, have a suspected H/W problem (on a different thread) and if I HAVE to flash the bios I was curious how to do it. Supermicro test the board and declare it compatible with Ubuntu, at the last LTS 8.04 version, however as this has been upgraded to the latest and greatest I now have a problem.

---

