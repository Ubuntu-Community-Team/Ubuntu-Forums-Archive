---
title: "usb device woes"
date: 2010-11-19
forum: General Help
---

### Post by gbowe on 2010-11-19
ok so here's my issue. 

1. I was running koala for over a year on my pc with no issues.
2. then it stopped recognizing my usb flash drives and started behaving erratically with my hp ss external hard drive storage system.
3. i installed ubuntu 10 using the whole partition of the hard drive, which i thought would erase any previous config settings that koala would have put in.
4. the new ubuntu 10 *still* refuses to recognize the usb devices (flash drives) and still behaves erratically with the external hard drive - sometimes you can mount it and sometimes not, and when you can it runs at extremely low speeds.

in short installing a fresh version of ununtu and erasing the partition did not solve the problem. yet other machines - windows and linux have no issue with the devices that ubuntu on this machine won't recognize...

In windows talk, If I could get to a C prompt on the computer, i would just format the C drive. windows has never been on this system, only ubuntu. 

any ideas?

---

### Post by eatberrys on 2010-11-19
My First thought is maybe it is not an OS problem but a hardware?
  Might not be but came to mind.

Try Running ```
sudo lsusb -v
``` in terminal see if the hardware you plug in (ie: flash drives) are being recognized.

Manpage: [http://manpages.ubuntu.com/manpages/hardy/man8/lsusb.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/lsusb.8.html)

Hope this is helpful.

---

### Post by gbowe on 2010-11-20
thanks for the reply.

lsusb does show some usb storage devices, sometimes but not others, and they act inconsistently. disk utility tries to interact with them but ultimately fails.

things i have done to try and deal with this:

1. installed xp as the sole operating system (to run the windows motherboard bios updates) (flashing inside linux freaks me out -too complicated for me)
2. updated the bios, chipset drivers etc with the cd that came with the motherboard
3. installed ubuntu 10 as a dual boot with wubi
4. result: no functionality of any usb mass storage devices in xp or ubuntu
5. restored backed up old bios
6. fresh install of ubuntu 10 from cd rom
7. no improvement
8. used apt get to replace ubuntu 10 desktop with netbook remix 10 on the desktop

THAT works perfectly - full functionality of all devices! i've no issue with running netbook remix on my desktop - i am a huge fan of ubuntu, but i wonder why netbook remix can do what desktop cant.

I'm posting this because whatever it is about ubuntu 10 (and "Mint 10", which i also tried and with which i experienced the same symptoms as ubuntu 10 dekstop) is not an issue with netbook remix. if i/we? knew what the difference was between ubuntu desktop and ubuntu netbook remix was in this regard, i think it would solve a lot of usb port functionality issues that i've seen on these threads...

---

### Post by gbowe on 2010-12-04
whoa! is this a normal response for typing lsdev?

is there a way to clean this up? i've lost functionality of external storage (pen drives, external hard drives) on usb ports. printer and keyboard hgooked up through usb work fine

Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:02.0                   ff00-ff07
0000:00:1d.0                   fe00-fe1f
0000:00:1d.1                   fd00-fd1f
0000:00:1d.2                   fc00-fc1f
0000:00:1d.3                   fb00-fb1f
0000:00:1f.0                   0400-047f   0480-04bf
0000:00:1f.1                   0170-0177   01f0-01f7   0376-0376   03f6-03f6   fa00-fa0f
0000:00:1f.2                   f500-f50f   f600-f603   f700-f707   f800-f803   f900-f907
0000:00:1f.3                   0500-051f
0000:02:00.0                     ee00-eeff
acpi                      9 
ACPI                             0400-0403     0404-0405     0408-040b     0428-042f
ata_piix              14 15      0170-0177     01f0-01f7     0376-0376     03f6-03f6     f500-f50f     f600-f603     f700-f707     f800-f803     f900-f907     fa00-fa0f
cascade             4       
dma                            0080-008f
dma1                           0000-001f
dma2                           00c0-00df
eth0                     42 
floppy              2     6    03f2-03f2   03f4-03f5   03f7-03f7
fpu                            00f0-00ff
hda_intel                43 
i8042                  1 12 
i915                     44 
IO-APIC-edge            3 4 
keyboard                       0060-0060   0064-0064
parport0                  7    0378-037a
PCI                          0000-0cf7 0cf8-0cff 0d00-ffff   c000-cfff   d000-dfff   e000-efff
pic1                           0020-0021
pic2                           00a0-00a1
pnp                            0290-029f     0290-0297   04d0-04d1   0800-087f   0880-088f
r8169                              ee00-eeff
rtc0                      8    0070-0073
serial                         02f8-02ff   03f8-03ff
timer                     0 
timer0                         0040-0043
timer1                         0050-0053
uhci_hcd                         fb00-fb1f     fc00-fc1f     fd00-fd1f     fe00-fe1f
uhci_hcd:usb2            23 
uhci_hcd:usb3            19 
uhci_hcd:usb4            18 
uhci_hcd:usb5            16 
vga+                           03c0-03df

---

