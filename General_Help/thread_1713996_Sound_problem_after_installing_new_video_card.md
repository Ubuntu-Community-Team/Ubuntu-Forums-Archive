---
title: "Sound problem after installing new video card"
date: 2011-03-24
forum: General Help
---

### Post by bowens44 on 2011-03-24
I am using maverick 64 bit.

I have two sound cards.

I have an Audigy2 - SB Audigy 2 ZS
and nvidia on-board sound.

They were both working fine until I installed a new video card. I used the audigy for music, system sounds etc  and used the on-board sound only for skype.

Now when I boot I get see a message flash up that says something about cannot find slot index out of range or something like that , it's too fast to read. 

when I do a cat /proc/asound/cards I get this:

bob@net23-admin:~$ cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - SB Audigy 2 ZS [SB0350]
                      SB Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xe880, irq 20
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf8000000
 3 [U0x46d0x807    ]: USB-Audio - USB Device 0x46d:0x807
                      USB Device 0x46d:0x807 at usb-0000:00:12.2-6, high speed

  In my trouble shooting efforts, I decided to boot with a fedora 14 live CD. When I do 
cat /proc/asound/cards from fedora I get this:

$ cat /proc/asound/cards
 0 [U0x46d0x807    ]: USB-Audio - USB Device 0x46d:0x807
                      USB Device 0x46d:0x807 at usb-0000:00:12.2-6, high speed
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf3ff4000 irq 16
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf6cfc000 irq 19
 3 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf8000000
 4 [Audigy2        ]: Audigy2 - SB Audigy 2 ZS [SB0350]
                      SB Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xe880, irq 20

As you can see, it sees both sound cards, my tv card and my web cam.

I really have no idea how to trouble shoot this.

Any help will be appreciated.

---

### Post by bowens44 on 2011-03-24
forgot to mention that when I put the old video card back in both sound devices work.

---

### Post by bowens44 on 2011-03-24
Additional info;

If I boot with an ubunutu 10.10 live CD all cards are available

Errors from dmesg:

[   22.583176] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   22.833402] cannot find the slot for index 0 (range 0-1), error: -16
[   22.833474] EMU10K1_Audigy: probe of 0000:05:05.0 failed with error -16
 0-1), error: -16

Either card works by itself. If I disable the internal card the audigy works.
If I remove the audigy, the onboard sound card works.

---

