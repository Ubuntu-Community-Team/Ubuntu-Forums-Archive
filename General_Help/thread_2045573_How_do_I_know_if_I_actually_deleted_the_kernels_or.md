---
title: "*How do I know if I actually deleted the kernels or not?"
date: 2012-08-21
forum: General Help
---

### Post by RONNCC on 2012-08-21
So I first followed this 

[http://ubuntuforums.org/showthread.php?t=1070613](http://ubuntuforums.org/showthread.php?t=1070613)

and via the grub (which said they were on /dev/sda5) I used the livecd, unmounted sda6 and sda7 then deleted /dev/sda5. 

I then tried to boot up again and it said
"/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)."

so then I tried doing this but it didn't work:
[http://robertbeal.com/562/rebuilding-grub2-grub-cfg-from-ubuntu-live-cd](http://robertbeal.com/562/rebuilding-grub2-grub-cfg-from-ubuntu-live-cd)

so then I tried 
[http://www.linuxquestions.org/questions/linux-software-2/grub-probe-error-cannot-find-a-device-for-in-chroot-770865/](http://www.linuxquestions.org/questions/linux-software-2/grub-probe-error-cannot-find-a-device-for-in-chroot-770865/)

but I got an error when I tried that chroot

so then I did this

[http://www.linuxquestions.org/questions/linux-software-2/grub2-rewrite-from-livedvd-878892/](http://www.linuxquestions.org/questions/linux-software-2/grub2-rewrite-from-livedvd-878892/)

one by one (except i did sudo chroot instead of chroot which somehow got me to ubuntu@ubuntu# ?

and then I just tried restarting yet it showed the same menu, so I went into grub command line, and did 
this [http://www.mepis.org/docs/en/index.php?title=GRUB_from_command_line](http://www.mepis.org/docs/en/index.php?title=GRUB_from_command_line)
but I didn't know what that meant, so then I restarted _again_ and 
somehow now it magically shows:

GNU Grub version 1.99-21ubuntu3

Ubuntu, with Linux 3.2.0-generic-pae
Ubuntu, with Linux-3.20.0-23-generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)

without the additional associated
Ubuntu ... 2.6.31-20...
Ubuntu ... 2.6.31-19...
Ubuntu ... 2.6.31-17...

from before.

It should be noted that after the initial deletion of the partition I did update-grub but it didn't update....

So I think it's working as the kernel boots up... but how do I know I actually deleted them and didn't just hide them somewhere in the tree?

Also, how should I delete old kernels in the future?

Thanks!

Additional Question: What exactly can you do in the grub command line ... It didn't even let me use 'cd' :(

---

### Post by JRV on 2012-08-21
Look in your /boot directory to see if the old kernels are deleted.
```

cd /boot
ls

```

Here is mine:> 
jack@manx:~$ cd /boot
jack@manx:/boot$ ls
abi-3.2.0-29-generic         memtest86+.bin
config-3.2.0-29-generic      memtest86+_multiboot.bin
grub                         System.map-3.2.0-29-generic
initrd.img-3.2.0-29-generic  vmlinuz-3.2.0-29-generic
invaders.exec
jack@manx:/boot$ 


The kernel with the highest nunmber is the active kernel.

You have two good options to delete old kernels.

Use Symantic, being careful not to delete the active kernel.

Use the janitor in Ubuntu Tweak.
To install Ubuntu tweak:```

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

---

### Post by claracc on 2012-08-21
Other way to remove old kernels:

In a xterm, you run the command: dpkg --get-selections | grep linux-image

It will list all the kernel you have installed and also the package linux-image-generic

To remove old kernels you run: sudo apt-get remove --purge linux-image-numbers-generic (i.e. linux-image-2.8.24-22-generic )

Not remove the package linux-image-generic since it is neccesary to receive kernel updates

You cannot use cd command in GRUB, it has its proper way to be edited and its proper commands: [http://members.iinet.net/~herman546/p20/GRUB2%20Edit%20Mode.html](http://members.iinet.net/~herman546/p20/GRUB2%20Edit%20Mode.html)

---

### Post by dino99 on 2012-08-21
to know which kernel(s) is installed:

from a terminal:

cat /lib/modules


the easiest way for dealing with installing/purging is to use synaptic:

sudo apt-get install synaptic
sudo synaptic

):P

---

