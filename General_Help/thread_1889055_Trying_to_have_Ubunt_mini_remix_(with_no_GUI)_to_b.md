---
title: "Trying to have Ubunt mini remix (with no GUI) to boot and use 'root' account"
date: 2011-11-30
forum: General Help
---

### Post by greatsouls on 2011-11-30
Hi All,

I have a problem and I am not able to fine answer anywhere. Google it but could not fined much information about it.

I have a SLAX USB key that when booted automatically runs some diagnostic and hardware test, puling out some info (using hdparm) etc. By default SLAX boots and uses root account so no problem mounting, unmounting, kreating folders in / etc. automatically directly from the scripts.

Currently I am trying to switch to Ubuntu Mini Remix 11.04 (i386) as it has better support for the new hardware (example: SLAX does not see HDD when in IDE mode if it is connected to SandyBridge (DQ67SW for ex.) motherboard). I am trying to recreate the bootable USB key using UBUNTU (with no GUI) that will automatically run different scripts and they will call each other. Unforunatelly, Ubuntu is using now dynamically created account ‘ubuntu’ and all the scripts need to be corrected (added sudo in front of commands like mount). Also, I am having hard time to automatically run the first script that will mount the USB itself.

1. Is it possible to modify Ubuntu Mini Remix 11.04 so it will be using ‘root’ account instead?

I tried to run ‘sudo su’, ‘su -s’, ‘su -i’, ‘su -u’ in the very beginning from inside the script, but they switch to a different shell(I guess ?) and my script stops. As soon as I type exit it resumes. How can I overcome this?

2. If I enable 'root' (sudo passwd root) how can I have ubuntu to use the 'root' account instead of 'ubuntu' one?

What I have tried so far (with no luck):

In unpacked squashfs and in chroot I:
- Used ````
sudo passwd root
```' to enable 'root' account.
- Edited `/etc/casper.conf' and changed `export USERNAME="ubuntu"' to `export USERNAME="root"'
- ````
chmod +x /etc/casper.conf
```'
- Used ```
mkpasswd root
``` to get encripted password for 'root'
- Set the encrypted pass in `usr/share/initramfs-tools/scripts/casper-bottom/10adduser' --- line`db_set passwd/root-password-crypted ya4qfs3iQixB2'

Nothing worked!

I googled for days with no luck and the project I am working on is very urgent. 

Could you please point me to a source or give me an advice?

All your advise and help are highly appreciated.

Thank you very much,

---

### Post by greatsouls on 2011-12-04
An update...

I tried to use mingetty to have the system to autologin using root account during Live Session.

I added `exec /sbin/mingetty --autologin root tty1' in `/etc/init/tty1.conf' file. This works on regular Ubuntu installation, but did not work for USB live session. The file tty1.conf was rewritten and 'ubuntu' was set inside.

After checking inside 'inird.lz' I suspect that during Live sessions Ubuntu uses scripts and config files from the ramdisk file. 
Still have not figured out hot how to have Ubuntu to use 'root' account during live sessions...

Any ideas and suggestions are welcom :)

---

### Post by greatsouls on 2011-12-05
Well, here is the solution I found for anyone who is trying to have ubuntu using the root account. This is for Ubuntu LiveCD without GUI (I used ubuntu-mini-remix).

Just as I expected the answer was inside initrd file. I used `uck-remaster' scripts. Here are the steps:

===== Mount and extract the ISO ====
```
sudo uck-remaster-unpack-iso livecdtmp/ubuntu-mini-remix-11.04-i386.iso
```==>  creates `~/tmp/remaster-iso' folder
  
===== Unpack initrd file ====
```
 sudo uck-remaster-unpack-initrd
```==> creates `~/tmp/remaster-initrd' folder

===== Edit `casper.conf' file' ====
```
cd ~/tmp/remaster-initrd/etc/
sudo nano -w casper.conf
```==> change `export USERNAME="ubuntu"' to `export USERNAME="root"'

===== Pack `initrd' ====
```
sudo uck-remaster-pack-initrd
```===== Rebuild ISO ====
```
sudo uck-remaster-pack-iso
```==> creates `~/tmp/remaster-new-files' folder with `livecd.iso' file inside

This worked for me.

---

