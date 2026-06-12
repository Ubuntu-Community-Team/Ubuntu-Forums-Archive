---
title: "Hard Drive Swticher"
date: 2009-09-17
forum: General Help
---

### Post by ade234uk on 2009-09-17
Do you know if its possible to purchase a switch, so instead of dual booting on the same hard drive, you have one OS on each drive.

Before starting your machine, you select using a switch which hard drive to boot.

Hard drives are so bloody cheap you might as well get two.

---

### Post by StuartN on 2009-09-17
> **ade234uk said:**
> Do you know if its possible to purchase a switch, so instead of dual booting on the same hard drive, you have one OS on each drive.

From a simple wiring point of view, you could connect all the +12v rails through a selector switch and choose which drive powers up. Even better, you could split out the drive select signal on IDE cables and switch that.

From a software perspective this would be extremely dangerous setup because switching drives at any point after booting up would either freeze your system or cause severe data loss. It would be possible to disable the switch on a booted-up system, for instance by a relay-control, so it doesn't work when there is power.

Multi-booting is a safe and fairly elegant alternative, although Partition Magic certainly did prettier menus than GRUB.

---

### Post by P4man on 2009-09-17
and then accidentally press the switch while your computer is on, and fry your disks and/or motherboard?  Wouldn't do it. 

Your BIOS probably has a boot device menu (on my machine its F11). You can use that instead. EAch of my drives has its own bootloader (grub and/or windows bootloader). My main drive which holds several ubuntu's, lets me chose all OS's on all drives, but if I disconnect that drive, or pick another drive from the BIOS boot menu, I can boot in to whatever OS is on the next drive..

---

### Post by ade234uk on 2009-09-17
I was actually thinking that, what would happen if you switched hard drives while the machine was on lol, how much damage could you cause.

The problem I have is I still need to use Windows for work. I have both Windows and Ubuntu on one drive, but I will get a second drive put Ubuntu on this and then do it the safest way possible.

---

### Post by P4man on 2009-09-17
> **ade234uk said:**
> I was actually thinking that, what would happen if you switched hard drives while the machine was on lol, how much damage could you cause.

Im pretty sure it could physically kill the drive or motherboard. I once accidentally connected a (pata) drive while the machine was powered on, thinking it was off, and it sent sparks across the room and the drive was bricked. Not recommended!

---

### Post by ade234uk on 2009-09-17
My fear is always screwing the work OS, If I want to reinstall Ubuntu. 

So two drives will be safer, because I can reinstall Ubuntu any time I like, and if she does not boot I only need to make changes to grub.

---

### Post by P4man on 2009-09-17
but you dont need a hardware switch for that.
Just disconnect the windows drive, install ubuntu on the other drive. Both drives will now have their own bootloader (windows bootloader for windows, and grub for ubuntu). Put the ubuntu drive as first boot drive in your bios, add windows to grub menu. Now you can dual boot, but if you screw the ubuntu drive and/or grub, or you remove it, you can simply boot from the other drive, nothing changed there, no risk.

---

### Post by Grenage on 2009-09-17
Generally hard drives are fine when connected or removed and the power is on; hell, SATA is even hot-swap when the board supports it.  I've unplugged and reconnected drives in live systems thousands of times and never had one die.  That said...

If you really need one per OS and only one active at any one time, you can get hot-swap-style caddies that take up a 5" bay.  You just change the drive before you boot up.

I would personally just keep both in the machine and use grub.

---

### Post by P4man on 2009-09-17
> **Grenage said:**
> Generally hard drives are fine when connected or removed and the power is on; hell, SATA is even hot-swap when the board supports it.

I have yet to see a desktop board that supports it. And PATA is very much non hotpluggable. Maybe if you use a removable tray (or switch) chances of frying it are smaller then doing what i did (inserting a pata cable "sideways" which caused massive sparks and killed the drive, on a machine in S4 standby!).

---

### Post by Grenage on 2009-09-17
Indeed PATA is not, but I have connected and removed them from live machines a thousand times and never killed a drive; neither has anyone else I personally know.  I know that it **has** happened to people (as you yourself have said), but it's very rare.

Not that I'm being argumentative; I agree with you and wouldn't recommend it!

---

