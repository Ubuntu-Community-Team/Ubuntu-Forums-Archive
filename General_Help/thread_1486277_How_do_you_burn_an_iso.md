---
title: "How do you burn an iso?"
date: 2010-05-17
forum: General Help
---

### Post by harryliddic on 2010-05-17
I am having trouble with my dual-boot and a thread says to fix winXP MBR first and to do that I need the Administrative password,which I haven't a  clue. I download a program call OPHCRACK as an iso into my Download dir. I tried to burn it in CD/DVD Creator but that didn't work I went to the repos and found alot of programs that mount iso's. But I don't know which one to use and if it's effective and once mounted what do I do? I decided it was time for wiser heads to prevail.

---

### Post by cryptotheslow on 2010-05-17
Personally I use Brasero. Not sure if that is installed as standard or you'll need to get it from the Software Centre or via Synaptic.

Once installed it's just a single right click on the ISO file and "Open with Brasero" then hit Burn... job done.

---

### Post by oldfred on 2010-05-17
If you have a secure system that requires a password for the BIOS to update the MBR, I do not think that will work.

If you just want to reinstall a boot loader, only a few systems prevent you.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

this will boot the partition with the boot flag or active partition in windows speak.

---

