---
title: "joystick, no such device"
date: 2006-04-23
forum: General Help
---

### Post by Tommi Viitanen on 2006-04-23
I'v tried everything and cannot do anymore with this problem. Here is everything, I'v done (with sudo):

$ cat /proc/asound/cards
0 [Live           ]: EMU10K1 - SB Live [Unknown]
                     SB Live [Unknown] (rev.10, serial:0x80651102) at 0x2080, irq 5

modprobe emu10k1

mknod input/js0 c 13 0
mknod input/js1 c 13 1
mknod input/js2 c 13 2
mknod input/js3 c 13 3
ln -s input/js0 js0
ln -s input/js1 js1
ln -s input/js2 js2
ln -s input/js3 js3
modprobe joydev
modprobe ns558
modprobe analog

/dev$ joystick-device-check
device files are okay!

And there is still:

$sudo jstest /dev/input/js0
jstest: No such device

Here is some more info:

lsmod
Module                  Size  Used by
emu10k1                68484  0
sound                  70444  1 emu10k1
ac97_codec             17420  1 emu10k1
ns558                   5508  0
joydev                  9280  0
analog                 10528  0
.
emu10k1_gp              3712  0
gameport               14472  4 ns558,analog,emu10k1_gp
.

$ lspci
.
0000:01:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:01:02.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
.

I also tried these with no success:

[http://ubuntuforums.org/showthread.php?t=55173&highlight=device+joystick](http://ubuntuforums.org/showthread.php?t=55173&highlight=device+joystick)

---

