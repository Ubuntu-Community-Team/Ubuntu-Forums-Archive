---
title: "gfceu problem 9.1"
date: 2010-05-25
forum: General Help
---

### Post by PerfectReign on 2010-05-25
I'm having an issue with gfceu.

I've got a collection of NES rom files, which correspond with my actual NES unit in my attic.

Running gfceu under 10.04 was no issue. (Aside from the whole x server freezing sporadically.)

I was just trying to run gfceu under 9.1 and am having issues.

If I run with sound, the sound is sketchy - almost like a scratched up CD - and the video is very slow.

If I turn off sound, I can sort of play, however, I want the sound.


Running from the command line I get the following:

> kai@kai-laptop:~/apps/nes_roms/USA$ gfceu
gfceu message:  Using: /usr/games/fceu
/usr/bin/gfceu:510: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.widgets = gtk.glade.XML(glade_file)
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 0 -opengl 0  "/home/kai/apps/nes_roms/USA/Super Mario Bros - Duck Hunt (U).nes"

Starting FCE Ultra 0.98.12...
Loading /home/kai/apps/nes_roms/USA/Super Mario Bros - Duck Hunt (U).nes...

 PRG ROM:    4 x 16KiB
 CHR ROM:    2 x  8KiB
 ROM CRC32:  0xd26efd78
 ROM MD5:  0xd821fb982ce47299fdb08a027ec0b8be
 Mapper:  66
 Mirroring: Vertical

Initializing video... Video Mode: 512 x 448 x 32 bpp 

Initializing sound...
 Bits: 16

 Rate: 48000
 Channels: 1
 Byte order: CPU Native
 Buffer size: 1024 sample frames(21.333333 ms)
Taking the "G" out and just runnning fceu, I get the following: 

> kai@kai-laptop:~/apps/nes_roms/USA$ fceu "/home/kai/apps/nes_roms/USA/Super Mario Bros - Duck Hunt (U).nes"

Starting FCE Ultra 0.98.12...
Loading /home/kai/apps/nes_roms/USA/Super Mario Bros - Duck Hunt (U).nes...

 PRG ROM:    4 x 16KiB
 CHR ROM:    2 x  8KiB
 ROM CRC32:  0xd26efd78
 ROM MD5:  0xd821fb982ce47299fdb08a027ec0b8be
 Mapper:  66
 Mirroring: Vertical

Initializing video... Video Mode: 512 x 448 x 32 bpp 

Initializing sound...Error opening a sound device.I searched here and see a few threads, which are both unresolved:

[http://ubuntuforums.org/showthread.php?t=1334842](http://ubuntuforums.org/showthread.php?t=1334842)

and

[http://ubuntuforums.org/showthread.php?t=1447850](http://ubuntuforums.org/showthread.php?t=1447850)

Any ideas anyone?

---

### Post by PerfectReign on 2010-05-26
Oddly enough, for some reason it works - when run from Nautilus.

I double-click on the .nes file and it loads just fine.

Still running from gfceu I get the wierd behavior, but at least I have my fix for now.

---

