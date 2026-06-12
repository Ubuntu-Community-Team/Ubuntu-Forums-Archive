---
title: "mounting initrd.img file"
date: 2009-07-27
forum: General Help
---

### Post by dimitriosd on 2009-07-27
Hi there 
 
Because this is my first question here in the forum I would first like to say that this forum is a very helpful site for me testing my ubuntu (and because I am still new in Linux Kernels and Distributions).
 
My Question has something to do with the initrd file (/boot/initrd.img-2.6.24-23-server)
 
I was reading the Debian Linux Kernel Handbook and tried to do the following thing
 
**6.4 Examining the initramfs contents**

Occasionally it is useful to examine the contents of initramfs to diagnose a problem or for educational purposes. The old-style initrds created by /usr/sbin/mkinitrd from initrd-tools package are either cramfs or ext2 filesystem, so they need to be mounted to access their contents. This may be achieved with the commands like 
     # mkdir -p /mnt/initrd     # mount -t cramfs /boot/initrd.img-2.4.27-3-686 /mnt/initrd -o loopNew style initramfs, created by yaird or initramfs-tools are compressed cpio archives, which may be extracted using the command 
     $ zcat /boot/initrd.img-2.6.18-3-686 | cpio -iIt will unpack the contents of the initramfs into the current directory. 
 
(located @ [http://kernel-handbook.alioth.debian.org/ch-initramfs.html](http://kernel-handbook.alioth.debian.org/ch-initramfs.html))
 
I first did the last command $ zcat /boot/initrd.img-2.6.18-3-686 | cpio -i
and then the others above
 
now here is the message from my system after pressing Enter :
 
[ 9904.764797] cramfs: wrong magic
mount : wrong fs type, bad option, bad superblock on /dev/loop0,
            missing codepage or helper program, or other error
            In some cases useful info is found in syslog - try
            dmesg | tail or so
 
I've tried to read different forums and googled the problem without anything usefull to try out :( maybe there is someone here who can help me out with this problem ?
 
thx for listening

---

