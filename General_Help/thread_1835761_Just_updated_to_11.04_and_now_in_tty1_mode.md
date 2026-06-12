---
title: "Just updated to 11.04 and now in tty1 mode"
date: 2011-08-29
forum: General Help
---

### Post by ksaul on 2011-08-29
I just updated to 11.04 and when i rebooted after the update manager was finished, my computer booted into a command prompt saying it was 'tty1'?

how do i fix this? im not sure what the hell to do at all lol

(my video card is an ATI Radeon series, and i use DVI to connect to my monitor)




--------------
Unrelated but... i have updated from 9.04 and now my grub bootloader has like 15 different ubuntu options - how do i delete the unnecessary options? (i am dual booting with windows 7)

---

### Post by Alwimo on 2011-08-29
I think you need to press Ctrl, Alt and F7. One some computers it's a different F-key, so try the others if that doesn't work.

---

### Post by ksaul on 2011-08-29
i tried to delete the xorg.config file and reboot - well this did nothing for me


and hitting the set of keys you posted (i do not htink will work) because its in a command console not a gui interface

---

### Post by ksaul on 2011-08-30
anything?

---

### Post by seawolf167 on 2011-08-30
Try

```
startx
```or

```
sudo service gdm restart
```or failing those commands

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ksaul on 2011-08-31
> **Alwimo said:**
> I think you need to press Ctrl, Alt and F7. One some computers it's a different F-key, so try the others if that doesn't work.

tried this, no luck ttyX on all screens =(

[quote=seawolf167]Try
```
startx
```
or
```
sudo service gdm restart
```
or failing those commands
```
sudo dpkg-reconfigure xserver-xorg
```
[/quote]

tried all of these, and no luck either.. got the following errors:

**startx**:
9: /lib/i386-linux-gnu/libc.so.6
Segment Fault at address 0x50
Caught signal 11 (seg,emtatopm fault) server aborting
(EE) fglrx(0) firegl_setsuspendresumestart failed 9

xinit: giving up
xinit: unable to connect to Xserver Connection Refused
xinit: server error

------------------

**sudo service gdm restart**
failed to acquire org.gnome.DisplayManager
Could not aquire name; bailing out

-------------------

**sudo dpkg-reconfigure xserver-xorg**
no messages, just didnt fix the problem





When i was switching through alt+Fkeys, a screen had abunch of messages with [OK] next to it, but one of them said:
Starting Load Fallback graphics devices [FAIL]

figure i should post that aswell....

so what the hell is going on, how do i fix it?!!?! ARGGGGG :confused:

---

### Post by ksaul on 2011-09-01
does anyone have any other recommendations?? this is driving me crazy :confused:

---

### Post by ksaul on 2011-09-02
help please!!

---

### Post by Quarkrad on 2011-09-02
Try taking your video card out and booting with your monitor plugged into your motherboard graphics.  You need to set your bios to internal graphics before you do this.  If it boots to the Desktop you can set everything up and once sorted you can put your video card in and load the video drivers for the card.  I found on numerous occasions is is best on a new system to install using the motherboard video first and then inserting 3rd party cards.

---

### Post by ksaul on 2011-09-02
> **Quarkrad said:**
> Try taking your video card out and booting with your monitor plugged into your motherboard graphics.  You need to set your bios to internal graphics before you do this.  If it boots to the Desktop you can set everything up and once sorted you can put your video card in and load the video drivers for the card.  I found on numerous occasions is is best on a new system to install using the motherboard video first and then inserting 3rd party cards.

i dont have onboard graphics card... but i ended up just reinstalling ubuntu all together with an 11.04 disk i downloaded and everything works flawless as is


so problem: solved! (kinda)

---

### Post by Quarkrad on 2011-09-03
Great - one thing I have learned is that when moving from one version of Ubuntu to another it is much better to trash and re-install from scratch rather than upgrading from an existing installation.  I have done this from V8.xxx and have no issue with each version - it is easy to save user data and reinstall after the fresh install.

---

