---
title: "Booting from Ubuntu live USB"
date: 2010-01-03
forum: General Help
---

### Post by do_the_ron on 2010-01-03
OK, I'll try and give you as much info as I know.  I have a live USB of 9.10 "Karmic".  I downloaded the live cd, booted it and used the live USB creator inside Ubuntu to make it.  Then I found that my computer is too old to boot from USB, and so after googling some, ran into this guide: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB).  When attempting to follow the instructions found in the "Booting the kernel from a bootable CD" section, I realized that they had been written for Ubuntu 9.04 "Jaunty".  As they are not completely current, I ran into the following three problems (please keep in mind that I am doing all of this from a live CD):
 
1.  The second step commands you to copy "initrd.gz" to the boot folder with
```
cp /cdrom/casper/initrd.gz iso/boot/
```.
When attempting that code, I got an error that "initrd.gz" did not exist.  When I navigated to /cdrom/casper, I found an "initrd.**lz**", not an "initrd.**gz**".  I decided that maybe I should copy that file instead, so I did.  This leads to the first problem.  Later you are instructed to run ```
sudo mkinitramfs -o iso/boot/initrd.gz <kernelversion>
```
and later still another command mentions .gz.  I did run those commands as is, resulting in my final folder "iso" containing BOTH initrd.gz AND initrd.lz.  This CANNOT be right.
 
I also did a search of that site I linked above, and did find in the "Booting the kernel from an internal hard drive", several mentions of "initrd.lz" in the SAME COMMANDS as those found in the section I was using.  And at the end of that section "tested with Karmic Koala Alpha 3" is found, so my theory is this, and let me know if this is right.  I think that the section I am using has just not been updated even though one of the other sections has.  **SHOULD I JUST REPLACE ALL OF THE "INITRD.GZ"'S WITH "INITRD.LZ"'S?  WOULD THAT BE THE SOLUTION?**
 
2.  This has already been solved, but I had to do some independant research for it.  One step requires you to input the linux kernel version that you have installed on your computer.  Thanks to google I figured out that 9.10 uses kernel 2.6.31-14-generic, so that problem is solved.
 
3.  The last command that was giving me problems is this:
```
cp /usr/lib/grub/i386-pc/stage2_eltorito iso/boot/grub/
```.
 
"stage2_eltorito" does not exist.  Sure enough, when I navigated to that directory, there was no stage2_eltorito to be found...so I downloaded "grub-0.97.tar.gz" from [ftp://alpha.gnu.org/gnu/grub/](ftp://alpha.gnu.org/gnu/grub/), and as per the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=237022"), I opened (but not extracted) the gz archive, opened (not extracted) the tar archive, then opened the grub-0.97 folder, opened the stage2 folder,** and copied the start_eltorito.S file to my HD...will this work as stage2_eltorito?**
 
Thanks for any help you can offer.

---

### Post by do_the_ron on 2010-01-03
p.s. If I do not get a reply by about 3 or 4 hours from now, I'll just try what I have above.

---

### Post by DZ* on 2010-01-03
edit: Oops, missed the most important part: "my computer is too old to boot from USB" :-)

I've been using Ubuntu on USB sticks or drives since Hardy. The way I've always been making these is by doing a regular install on a USB drive, as if I were installing to an internal hard drive. It works very well.

Full-disk encryption (luks, using the "alternate CD" iso) proved to be too slow on a flash, especially when multiple programs access the flash simultaneously.

"Encrypted home" option (ecryptfs) works much better and is fully usable, but I had to disable swap in 9.10, because the crypttab swap entry no longer works by specifying the UUID (it has to be /dev/xxx, but that can change depending which computer you boot from). The reason the UUID method doesn't work is because the 9.10 erases the UUID of the encrypted swap partition once you boot the system.

---

### Post by do_the_ron on 2010-01-03
nevermind.  I have the kernel no., I am going to replace all gz with lz, and I found a copy of stage2_eltorito...wish me luck, and thanks.

---

### Post by tea for one on 2010-01-03
Good evening

Here is a web link which will provide instructions to create a bootable CD for your USB karmic installation:-

[http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/)

Good luck

---

### Post by do_the_ron on 2010-01-03
Spot on, tea for one!

Thanks a million, I'm booted from the usb right now, took out the cd and now I'm in live USB with a free cd drive!

---

### Post by tea for one on 2010-01-03
Splendid - I'm glad that it was successful

---

