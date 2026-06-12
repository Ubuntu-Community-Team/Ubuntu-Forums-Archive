---
title: "&quot;Booting Ubuntu from RAM&quot; - Guide fails on my eeePC 1005P &amp; Lucid"
date: 2010-05-21
forum: General Help
---

### Post by Daniel-G on 2010-05-21
Hi everyone,

*I use an eeePC 1005P and Lubuntu 10.04*

I'm currently stuck with a problem I cannot handle myself. I followed this guide ( [http://ubuntuforums.org/showthread.php?t=707230](http://ubuntuforums.org/showthread.php?t=707230) ) to create a RAM-only Filesystem. It worked like a charm, except for linux-ubuntu-modules-2.6.32-21-generic not being found. I continued anyway...
Everything worked fine, until #9, where I should create the GRUB-Entry. Because Lubuntu uses Grub 2, I changed it a bit. I created a script named "50_RAMSESS", made it executable and stored it in */etc/grub.d/*. 

```
#! /bin/sh -e

cat << EOF
menuentry "Ubuntu, Linux $(uname -r) to RAM" {
        insmod ext3
        set root='(hd0,1)'
        search --no-floppy
        linux   /boot/vmlinuz-$(uname -r) boot=live toram nosudo noxautoconfig noautologin quickreboot ro
        initrd  /boot/initrd.img-$(uname -r)
}
EOF
```After updating everything, I rebooted my eeePC...  

I selected the "... to RAM" Entry and it booted up. The SQUASHFS was loaded to Ram. After that, it breaked, showing the following output:

```
[  3.241864] composite sync not supported
[ 61.980620] [drm] Big FIFO is enabled
No supported filesystem images found at /live

(initramfs): _
```So I took a look with "tail" at "live.log":

```
Begin: Running /scripts/live-premount ...
Done.
Begin: Copying live media to ram ...
Begin: mount -t tmpfs -o size=537898k /dev/shm /live/image_swap

rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: write failed on "/live/image_swap/live/filesystem.squashfs": No space left on devices (28)
rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.7]
rsync: connection unexpectedly closed (103815 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

```I don't know what went wrong. Any ideas anyone? :(

*//EDIT: *The filesystem.squash is about ~500MB, and I have 2 GB of RAM... That shouldn't be the problem... theoretically

---

### Post by Daniel-G on 2010-05-24
Found the solution myself at ubuntuusers.de.

Original Link: [http://forum.ubuntuusers.de/post/2498944/](http://forum.ubuntuusers.de/post/2498944/)
Google Translation: [http://translate.google.de/translate?u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Fubuntu-server-to-ram-9-10-mit-grub-2%2F&sl=de&tl=en&hl=&ie=UTF-8](http://translate.google.de/translate?u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Fubuntu-server-to-ram-9-10-mit-grub-2%2F&sl=de&tl=en&hl=&ie=UTF-8)

---

### Post by terminator14 on 2010-05-27
I just stumbled upon the guide you linked to myself a few minutes ago, and was wondering: since it was written back in 2008, did you have to change much to get it to work? The part about grub2 immediately came to mind when I was looking over the guide - your solution for that will likely be very helpful when I try this in a few days so thanks for that. Anything else different?

And which parts did you use from 

> Original Link: [http://forum.ubuntuusers.de/post/2498944/](http://forum.ubuntuusers.de/post/2498944/)
Google Translation: [http://translate.google.de/translate...n&hl=&ie=UTF-8](http://translate.google.de/translate...n&hl=&ie=UTF-8)

to get it to work? Google's translated page is not all that easy to follow... Maybe it will become more clear when I start messing with it, but for now if you could point me in the right direction that would be great.

---

### Post by terminator14 on 2010-05-27
I had some time so I went ahead and tried this. The steps all went fine except for 9 where you originally got stuck. I tried your grub2 script:

> #! /bin/sh -e

cat << EOF
menuentry "Ubuntu, Linux $(uname -r) to RAM" {
        insmod ext3
        set root='(hd0,1)'
        search --no-floppy
        linux   /boot/vmlinuz-$(uname -r) boot=live toram nosudo noxautoconfig noautologin quickreboot ro
        initrd  /boot/initrd.img-$(uname -r)
}
EOF

and hit the same problem you originally did where after booting, it spends a while copying files to RAM and gives me the (initramfs) prompt. Now I'm going through the links you posted trying to figure out how to fix this.

When using the line:

> /sbin/hdparm -Y /dev/sda

what does it actually do? It seems to disable the /dev/sda disk completely. Why would you need to do this and what disk would you need this to point to? I have 3 different disks.

Also, what does your final 50_RAMSESS file look like?

---

### Post by terminator14 on 2010-05-27
For anyone curious, I finally got this to work, and here's how:

The 50_RAMSESS file in /etc/grub.d/ should read something like:

> #!/bin/sh -e

cat << EOF

menuentry "Ubuntu, Linux $(uname -r) to RAM" {
        set root='(hd0,1)'
        linux /boot/vmlinuz-$(uname -r) boot=live toram=filesystem.squashfs
        initrd /boot/initrd.img-$(uname -r)
}
EOF

Run: 
```
sudo update-grub2
```

to update the grub menu.

Also, if you boot into the new RAM OS and you have no internet, as stated [here]("https://bugs.launchpad.net/ubuntu/+source/fsprotect/+bug/477012") by jesbecker:

> apparmor does not work well with stacked and read only files systems. A work around for this bug is to either disable for remove apparmor.

Disable:
You can disable by adding apparmor=0 and security="" as kernel options in your grub boot configuration.

Remove:
You can also choose to remove apparmor by executing: sudo apt-get remove apparmor

This issue seems to affect any program that is protected/enforced by apparmor.

I have not tried to disable apparmor (the first option) but removing it worked immediately.

Oh yeah and I never did use:

> /sbin/hdparm -Y /dev/sda 

Works fine without it, and I have no idea why you would need it.

---

