---
title: "editing an entry in Grub2"
date: 2011-02-19
forum: General Help
---

### Post by adityavpratap on 2011-02-19
Hi,
I have installed Sabayon 5.4 on my laptop besides Ubuntu 10.10. During installation of Sabayon I did not opt for a bootloader as I did not want to disturb the already existing Grub2 on MBR from my Ubuntu installation.

After successful installation of Sabayon, I booted into Ubuntu and updated the Grub which detected Sabayon correctly. Then I rebooted and tried to boot into Sabayon but I could not do so. The booting process stopped with the following error -
```

Activating mdev
Detected real-root as md device. Setting up device node
Scanning for Volume Groups
Reading all physical volumes. This may take a while
Activating Volume Groups
Determining Root Device
Mounting Root
mount: mounting /dev/md0 on /newroot failed Input / Output error
!! Could not mount specified ROOT try again
!! Could not find the root block device in .
Please specify another value

```

From this I deduced that there is something wrong with the Sabayon entry in Grub2. I rebooted and on the Grub screen I selected the Sabayon entry and opened it for editing. Here is the relevant entry -
```

insmod ext2
set root=`(hd0,4)'
search --no-floppy --fs-uuid --set 4a2b695a-1b00-4b63-a45a-2b93e388eee4a

linux /boot/kernel-genkernel-x86-2.6.36-sabayon ro root=/der/ram0 ramdisk=8192 real_root=/dev/md0- dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda2 real_resume=swap:/dev/sda2

initrd /boot/initramfs-genkernel-x86-2.6.36-sabayon

```

The partitioning scheme for Sabayon is 
/ on /dev/sda4
/home on /dev/sda9
/usr on /dev/sda10
swap on /dev/sda8

So evidently, Grub has wrongly taken the values of root as /dev/md0 and swap as /dev/sda2. 

I again went back to Grub2 screen edited the Sabayon entry by replacing /dev/md0- with /dev/sda4 and swap:/dev/sda2 with swap:/dev/sda8 and pressed Ctrl+x. Now I was able to boot into Sabayon.

My question is how do I make these changes permanent. Which files should I edit so that Grub correctly read root as /dev/sda4 and swap as /dev/sda8?
Thanking in advance,

---

### Post by kiyop on 2011-02-19
I suggest you to make custom entry.
$ sudo gedit /etc/grub.d/40_custom

In openned gedit (text editor) window, add the following at the end.
```
menuentry "sabayon" {
insmod ext2
set root="(hd0,4)"
search --no-floppy --fs-uuid --set 4a2b695a-1b00-4b63-a45a-2b93e388eee4a
linux /boot/kernel-genkernel-x86-2.6.36-sabayon ro root=/dev/ram0 ramdisk=8192 real_root=/dev/sda4 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=swap:/dev/sda[FONT=monospace]8[/FONT][FONT=monospace]
[/FONT]initrd /boot/initramfs-genkernel-x86-2.6.36-sabayon  
}
```Save and close gedit.

$ sudo update-grub
changes the /boot/grub/grub.cfg

Please select "sabayon" at boot time.

---

### Post by adityavpratap on 2011-02-21
> **kiyop said:**
> I suggest you to make custom entry.
$ sudo gedit /etc/grub.d/40_custom

In openned gedit (text editor) window, add the following at the end.
```
menuentry "sabayon" {
insmod ext2
set root="(hd0,4)"
search --no-floppy --fs-uuid --set 4a2b695a-1b00-4b63-a45a-2b93e388eee4a
linux /boot/kernel-genkernel-x86-2.6.36-sabayon ro root=/dev/ram0 ramdisk=8192 real_root=/dev/sda4 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=swap:/dev/sda[FONT=monospace]8[/FONT][FONT=monospace]
[/FONT]initrd /boot/initramfs-genkernel-x86-2.6.36-sabayon  
}
```Save and close gedit.

$ sudo update-grub
changes the /boot/grub/grub.cfg

Please select "sabayon" at boot time.

Sorry for responding so late. I followed your instructions and created new entry in Grub, and now I am able to log into Sabayon.  Thank you very much!!

But is there a way I can edit an entry in Grub2?

---

### Post by kiyop on 2011-02-21
I am happy to help you.

The grub configuration file /boot/grub/grub.cfg is generated automatically by grub-mkconfig (update-grub and so forth), according to /etc/default/grub and /etc/grub.d/*.

Please read
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by adityavpratap on 2011-02-21
Thanks once again! :-)

---

