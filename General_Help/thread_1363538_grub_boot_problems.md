---
title: "grub boot problems"
date: 2009-12-24
forum: General Help
---

### Post by SchizmWolf on 2009-12-24
I'm running Kubuntu Jaunty 9.04 and I tried to fix a problem with my sleep mode by adjusting the kernel in /boot/grub/menu.lst this way:

```
[FONT=Arial][SIZE=2][COLOR=Black][COLOR=#990000]/boot/vmlinuz-2.6.15-23-686 root=/dev/sda1 ro quiet splash resume=/dev/sda[/COLOR][/COLOR][/SIZE][/FONT]
```[FONT=Arial][SIZE=2][COLOR=Black][COLOR=#990000]

Well, needless to say it borked my boot. Now every time I startup my system it runs Grub1.5, then spits out a hell of a lot of code onto the screen, and then goes to a blue-and-white backup screen that gives me options to Resume Normal startup, fix broken packages, free up space, etc... I tried to copypaste the kernal line from the recovery mode back into the normal file, but it doesn't do anything (this is the line):
```
/boot/vmlinuz-2.6.28-11-generic root=UUID=2edc2cdd-0002-4290-940f-594c8576f57b ro  single
```It never used to do that. After grub initialized it'd just give me the kubuntu load screen and be ready to go. I want to go back to that. Please help, this is REALLY annoying me and I don't want to have to reinstall Kubuntu.

EDIT: I adjusted the kernel to read: 
[/COLOR][/COLOR][/SIZE][/FONT]```
[FONT=Arial][SIZE=2][COLOR=Black][COLOR=#990000]/boot/vmlinuz-2.6.28-11-generic root=UUID=2edc2cdd-0002-4290-940f-594c8576f57b ro  quiet[/COLOR][/COLOR][/SIZE][/FONT]
```Now it'll boot without having to go to the backup screen, but the Kubuntu loading screen is still dead. At this point it's mostly a cosmetic fix, but I'd like to have it back. The new problem I noticed is now whenever I send the shutdown command it'll go to blackscreen with the mouse still visible indefinitely; ie, it WON'T SHUT DOWN T.T (without hard closing, but I hate doing that). Any ideas???

---

### Post by SchizmWolf on 2009-12-30
Please don't leave me hanging guys, this is really aggravating me =(

---

### Post by SchizmWolf on 2010-01-05
meh, fixed it.

---

