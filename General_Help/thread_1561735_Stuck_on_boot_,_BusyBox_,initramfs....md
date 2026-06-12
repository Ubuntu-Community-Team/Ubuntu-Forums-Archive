---
title: "Stuck on boot , BusyBox ,initramfs..."
date: 2010-08-26
forum: General Help
---

### Post by al1x on 2010-08-26
[IMG]http://ubuntuone.com/p/Dz4/[/IMG]

Every time I open my ubuntu 10.04 the boot stucks to this screen and if I press enter I can write commands like this..  

<initramfs> #command# 

what happened? :-s 
I realy need some help please..

---

### Post by quixote on 2010-08-28
Do you first get an error message saying that it can't find the root device, or something like that?  It sounds like grub (the bootloader) may have somehow lost track of where your ubuntu install is on the drive.  That can be fixed.  But first, so we know what we're actually trying to fix, give us as much of the error messages you're getting as you can.

---

### Post by al1x on 2010-08-30
ok , this is the message I get before the screen roll :

Killed
mount: mounting /dev on /root/dev failed : No such file or directory
mount: mounting /sys on /root/sys failed : No such file or directory
mount: mounting /proc on /root/proc failed : No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootarg

My problem is that when I boot from Live CD although I 've installed Ubuntu 10.04LTS from the same CD now it doesn't proceed to the ubuntu live cd(It's just loading until I see the green light of my dvd drive turning off and I'm getting stuck to ubuntu logo loading screen) and I can't have access to the terminal to fix the problem..So what can I do ? Any grub edit that I can do or something like this without the cd? Plus I have access to some limited commands when the screen stops moving, like this:

<initramfs> #x command#

---

### Post by quixote on 2010-08-30
What's happened is that grub has lost track of where your operating system is located.

You want to stop the process at the initial grub screen that shows you the choices of operating systems.  If you don't see choices, press the Shift key from the beginning of booting until a menu appears.

Press c for command, and then start the process of looking for where the system thinks your OS is located.  (Or, if you're sure you know, you can skip the various "ls" commands at the beginning.)  (This is taken from [Grub2 - Rescue Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode").)

At the grub> prompt, type ```
ls
```That will list all the drives and partitions which grub can look at to find an OS. (hd0) is the first drive. (hd0,1) is the first partition on that drive.  You need to type "ls (hd0,1)" (without quotes) at the grub prompt and see whether there are files called something like "vmlinuz" and "initrd" there.  I don't know what your setup is, so you may have a lot of partitions to check until you find the one you need.

Then go through the following steps:```
1. ls (hdX,Y) *[COLOR="Blue"][replace X,Y with the right numbers, eg (hd0,3) for 3rd partition, 1st drive or (hd1,5) for 2nd drive, fifth partition][/COLOR]*

2. set prefix=(hdX,Y)/boot/grub

3. set root=(hdX,Y)

4. set

5. ls /boot  

6. insmod /boot/grub/linux.mod

7*. linux /vmlinuz root=/dev/sdXY ro  *[COLOR="Blue"][use the usual linux way of referring to partitions: sda1 would 1st drive, first partition; sda3: 1st drive, 3rd partition; sdb5: 2nd drive, 5th partition][/COLOR]*

8. initrd /initrd.img

9. boot 
```

Assuming this works and it then proceeds to boot into your linux install, be sure to do the following *before you reboot*.  It will write the correct values to your grub files.```
sudo update-grub
```

---

### Post by al1x on 2010-08-31
I 've tried them all several times and I'm getting the same screen with the same issues :(
My version of grub is GNU GRUB 1.98-1ubuntu7 if that matters..I 've even tried the 2 other commands(root=(loop0) and vmlinuz=.......) for wubi installs because I've installed the ubuntu 10.04 side by side with winxp.But when I set root=(loop0) then I press ls /boot and I get the message "no such disk".hmm..

---

### Post by hhoyt on 2010-08-31
possibly best to reinstall grub2.
boot your install disk.

from root

1) blkid
< find the partition you installed ubuntu on
2) mount /dev/sdax /mnt      <<< where x is partion # containing ubuntu and 'a' assumes this is your first hard drive (if have > 1)
3) mount --bind /sys /mnt/sys
4) mount --bind /dev /mnt/dev
5) mount --bind /proc /mnt/proc
6) chroot /mnt
7)update-grub 
8) grub-install /dev/sda    <assumes the you want grub to be installed on your first hard drive ('a')
9) reboot

---

### Post by quixote on 2010-08-31
Hmm.  Mysterious.  And frustrating.  hhoyt's suggestions are good ones.  (Note that the smiley face at 8 ) is what happens when you need to write "8" followed by a ")".  They need to come up with a way to have a literal 8 ) without using Code tags!)

The other thing that would be helpful for troubleshooting is if there was complete information on your situation.  The best thing would be if you could [run bootinfo script]("http://ubuntuforums.org/showthread.php?t=1291280"), but that requires at least a LiveCD, which isn't working on your system.  What are all the drives and partitions on your system, which OSes do you have on which one, and which are supposed to the bootable ones?

---

### Post by al1x on 2010-08-31
When you say "from root" what do you mean?When I boot from cd I have some options like "Try Ubuntu without installing,Install Ubuntu,Check disk for defect etc." So what I must choose?

---

### Post by al1x on 2010-08-31
> **quixote said:**
> Hmm.  Mysterious.  And frustrating.  hhoyt's suggestions are good ones.  (Note that the smiley face at 8 ) is what happens when you need to write "8" followed by a ")".  They need to come up with a way to have a literal 8 ) without using Code tags!)

The other thing that would be helpful for troubleshooting is if there was complete information on your situation.  The best thing would be if you could [run bootinfo script]("http://ubuntuforums.org/showthread.php?t=1291280"), but that requires at least a LiveCD, which isn't working on your system.  What are all the drives and partitions on your system, which OSes do you have on which one, and which are supposed to the bootable ones?

Sda1 is my partition of Windows XP (so I can play pc games :P) and sda7 is my partition of Ubuntu 10.04LTS.I only have one hdd.

---

### Post by bcbc on 2010-08-31
If you installed with wubi, then don't reinstall grub.

I have seen problems with the latest kernel dropping people in a busybox prompt. I recommend booting your previous kernel, e.g. -23

I don't know of a fix, but if -23 (or your previous kernel if not -23) works then just remove -24.

---

### Post by al1x on 2010-08-31
> **bcbc said:**
> If you installed with wubi, then don't reinstall grub.

I have seen problems with the latest kernel dropping people in a busybox prompt. I recommend booting your previous kernel, e.g. -23

I don't know of a fix, but if -23 (or your previous kernel if not -23) works then just remove -24.

I have no other kernel, just a recovery mode which is also useless.. ](*,)

---

### Post by bcbc on 2010-08-31
> **al1x said:**
> I have no other kernel, just a recovery mode which is also useless.. ](*,)

Did you do a 10.04.1 install or delete your prior kernels? Either way: Ouch.

I am guessing that the problem is that the initial ram disk wasn't updated correctly with the kernel update. But don't know for sure. Also there is a new -24 update today so hopefully that may fix it???

You could try chrooting in and updating the initrd.img or just trying to update to the latest -24 - which should do it.

Boot from a live CD and connect to internet (in the following instructions replace /dev/sdaX with your ubuntu partition):
```
sudo mount /dev/sdaX /mnt
cp /etc/resolv.conf /mnt/etc
for i in dev proc sys dev/pts; do sudo mount --bind /$i /mnt/$i; done
sudo chroot /mnt
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

# the following updates initrd.img
update-initramfs -u

# if that doesn't work or if you want to try this instead,
# the following should pull in the kernel update and
# run update-initramfs as well
apt-get update
apt-get upgrade

rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in dev/pts dev proc sys; do sudo umount /mnt/$i; done
sudo umount /dev/sdaX

```

No guarantees that will work - but I can't think of any other way to fix this.

---

### Post by al1x on 2010-08-31
Ok thank you all of you :) When I manage to boot from the Live CD (because my pc refuses to do so :lolflag:) I'll try the proposed solutions and I will update you about the issue.

---

### Post by hhoyt on 2010-08-31
Ok.
I don't think this is a WUBI install.
You want 'Try Ubuntu 10.04 LTS'
You can just reinstall, but seems a shame if only your boot is messed up. So go to:

APPLICATIONS/ACCESSORIES/TERMINAL and enter as follows
sudo su << enter superuser mode
blkid   << view partitons (sounds like it is /dev/sda7 ?
mount /dev/sda7 /mnt   < mount your partion
mount --bind /dev /mnt/dev  < bind to your system (symlink)
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/sys
chroot /mnt  <<< ok, change your /root over to the REAL Ubuntu
update-grub  <<< search out any O/S's
grub-install /dev/sda <<< write the boot


Reboot <<3 finger salute, followed by 'restart' or click on icon in right uppermost corner, or alt-sysreq-'b', or p.o.r.

Best of luck,

Howard

---

### Post by mlissner on 2010-08-31
I just had this same problem out of the blue, and I rebooted, switched to a kernel prior to .24, and it seems to be booting fine. 

Really frustrating to have this happen, but using a different kernel seems to have done the trick. Now then...how do I remove a kernel so I never have to see it again?

---

### Post by bcbc on 2010-08-31
> **mlissner said:**
> I just had this same problem out of the blue, and I rebooted, switched to a kernel prior to .24, and it seems to be booting fine. 

Really frustrating to have this happen, but using a different kernel seems to have done the trick. Now then...how do I remove a kernel so I never have to see it again?

You can uninstall it from synaptic. There are three entries - search on 2.6.32-24.

EDIT:
As I said earlier, there is an update to -24 released today - *_maybe_* this will fix the problem. If you try reinstalling -24 and report back then you can give some hope to the OP :)

---

### Post by tomansc on 2010-08-31
Had same issue as OP.

Thank you bcbc: I used your code (post#12) booting from a different Live CD and managed to get it up and running again! Curiously, however, updating the kernel failed...so hopefully this problem won't recur.

---

### Post by quixote on 2010-08-31
It's probably too late to clarify at this point, but what hhoyt means by "from root" is "while you're root" i.e. in a terminal using "sudo" before the commands, like he shows in his clarification.  A wubi install is ubuntu installed from **within** Windows.  You have a dual boot setup, so ignore the wubi stuff.

---

### Post by mlissner on 2010-08-31
> **bcbc said:**
> You can uninstall it from synaptic. There are three entries - search on 2.6.32-24.

EDIT:
As I said earlier, there is an update to -24 released today - *_maybe_* this will fix the problem. If you try reinstalling -24 and report back then you can give some hope to the OP :)
OK it turns out that in my case, initramfs (I think that's its name) was unable to create the proper boot system after the kernel update -- apparently, the update failed for some other reason.

I re-did the update, and the boot system was recreated, and now that kernel is working. I have a handful of other issues as well, but I can't for the life of me figure out which is caused by which, nor what to do about it. In any case, I need my own thread for my problems, so I'm gonna spin them off elsewhere -- don't want to hijack things here.

---

### Post by randyklein99 on 2010-09-19
> **hhoyt said:**
> possibly best to reinstall grub2.
boot your install disk.

from root

1) blkid
< find the partition you installed ubuntu on
2) mount /dev/sdax /mnt      <<< where x is partion # containing ubuntu and 'a' assumes this is your first hard drive (if have > 1)
3) mount --bind /sys /mnt/sys
4) mount --bind /dev /mnt/dev
5) mount --bind /proc /mnt/proc
6) chroot /mnt
7)update-grub 
8) grub-install /dev/sda    <assumes the you want grub to be installed on your first hard drive ('a')
9) reboot

I was having the same problem.  The above method worked for me.  Thanks.  

Edit: Problem has cropped up again, solution worked again.  Wondering why it keeps recurring though.

---

### Post by FNoo on 2010-10-26
I am having the same problem with a twist.

I got an old computer working and decided to install Ubuntu 10.04 on it having been given a LiveCD/Install CD.

The computer has an Asus A7A266 motherboard (c 2001) with an AMD Athlon 1.4GHz CPU and 512 Mb memory

The LiveCD worked fine and I decided to do an install which terminated in lots of 'disk sector' error messages.

On reboot I got the Busybox, initramfs prompt. 

By typing 'run-init' followed by 'enter' and then 'exec run-init' followed by 'enter' I can get it to boot up to windows. Obviously I would prefer if it would boot up directly.

I tried to update the GRUB as described in post #6 as I have GRUB1.98 and although it reported a successful upgrade once the PC rebooted it still showed GRUB1.98 and the problem continued.

I then tried the solution in mail #4 which identified two harddisk partitions (hd0,1) EXT4 and (hd0,5) SWAP as well as identifying (hd0).

I followed the instructions until at step 6 I got an error message 'error file not found'.

Any suggestions on why I cannot update the GRUB and secondly why I get the error message 'file not found'?

Thanks in advance

---

### Post by al1x on 2010-10-27
Finally , for me , it was a motherboard problem..my laptop was pretty old :p

---

### Post by randyklein99 on 2010-10-28
Finally figured out why it kept ocurring.  I had the graphics setting on normal when only None works on this laptop.  I don't know why that was corrupting the boot, but it all went away when I downgraded the graphics for all users.  Been rock steady since.

---

### Post by FNoo on 2010-10-31
I solved this problem on my computer by adding 'rootdelay=165' to the grub sequence (apologies if my terminology is wrong) having read a number of threads on the topic of being stuck on/in boot.

I guess this thread can be marked as 'solved' as the originator, al1x, has proved his fault to a motherboard problem?

Thanks to the forum for providing such a wealth of information, a little daunting at first due to the sheer volume but very interesting and very absorbing.

---

### Post by rcrath on 2010-11-10
I had this busybox problem and could not do the grub purge because mounting the sda2 partition where linux resides would not happen from the maverick live CD.  Trying to mount them gave a busy signal, saying another process already had hold of it, and umount showed it as not mounted yet.  

Elsewhere I read that booting with a slax live cd, the partitions would not be automatically mounted and I could run e2fsck -y -f -v /dev/sda2 from a root text prompt.  once I did that, I got my system back.  Very easy solution once I found it, unfortunately finding it took 8 hours.

---

### Post by xenorealm on 2010-12-08
I also faced with the same problem yesterday.
It started with a file that can be copy paste anywhere suddnely become locked( read only), and then one of my application crashed..and i thought maybe i need to restart my window and press ctrl+alt+backspace...and suddenly poof ...it shutdown..and then the fuking busybox appear...

Thank god i dual-boot my PC, so i went back to my Windows Vista (uwekkk!) and go to the folder I previously installed my ubuntu using wubi..and it wasn't there!! shocked!!

I thought to myself....**** I have to re-install all my files and configurations again..so I installed again my ubuntu...and then restart...

It's a miracle my previous Ubuntu( that has crashed) is back with all the configuration and apps installed!!...sweet!!

I don't know what happen and how it become like this..but I thank god !!

---

### Post by pedropimenta89 on 2010-12-15
sorry but when I mount the partition(mount /dev/sdax /mnt), it don't do nothing. I wait a lot of time.

---

### Post by akzouu on 2010-12-29
I found a solution to solve this problem [http://ubuntuforums.org/showpost.php?p=9863783&postcount=20](http://ubuntuforums.org/showpost.php?p=9863783&postcount=20)

---

### Post by darknum on 2011-01-02
try this:

in grub loading screen press e to enter edit screen.

add "rootdelay=90" without "" to the end of  line with UUID=blabla 

it will cause a longer boot but most probably will fix your problem.

---

### Post by JauntyJack on 2011-02-23
> **hhoyt said:**
> possibly best to reinstall grub2.
boot your install disk.

from root

1) blkid
< find the partition you installed ubuntu on
2) mount /dev/sdax /mnt      <<< where x is partion # containing ubuntu and 'a' assumes this is your first hard drive (if have > 1)
3) mount --bind /sys /mnt/sys
4) mount --bind /dev /mnt/dev
5) mount --bind /proc /mnt/proc
6) chroot /mnt
7)update-grub 
8) grub-install /dev/sda    <assumes the you want grub to be installed on your first hard drive ('a')
9) reboot

This worked for me the last few times my ubuntu laptop crashed and had this problem.

---

### Post by JauntyJack on 2011-02-24
> **hhoyt said:**
> Ok.
I don't think this is a WUBI install.
You want 'Try Ubuntu 10.04 LTS'
You can just reinstall, but seems a shame if only your boot is messed up. So go to:

APPLICATIONS/ACCESSORIES/TERMINAL and enter as follows
sudo su << enter superuser mode
blkid   << view partitons (sounds like it is /dev/sda7 ?
mount /dev/sda7 /mnt   < mount your partion
mount --bind /dev /mnt/dev  < bind to your system (symlink)
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/sys
chroot /mnt  <<< ok, change your /root over to the REAL Ubuntu
update-grub  <<< search out any O/S's
grub-install /dev/sda <<< write the boot


Reboot <<3 finger salute, followed by 'restart' or click on icon in right uppermost corner, or alt-sysreq-'b', or p.o.r.

Best of luck,

Howard

Howard, you're brilliant! This worked today. 

BTW, I read about [ALT+SysRq + R,S,E,I,U,B] Next time my screen goes black and blank, maybe using this will allow me to reboot safely? Rather than power off and end up with the problem this thread responds to? Will try, but have saved your fix offline for emergencies! Thanks again!

---

### Post by phoet12a on 2011-03-14
> **pedropimenta89 said:**
> sorry but when I mount the partition(mount /dev/sdax /mnt), it don't do nothing. I wait a lot of time.

same with me. Is there any other solution for me??
can't mount my harddisk

---

### Post by crunchytheory on 2011-03-16
This may be helpful as I had similar symptoms... where the kernel doesn't finish loading and I get stuck on the initramfs prompt with BusyBox.

The source of the problem was that I was installing Ubuntu 10.10 on one older Dell machine, then moving the SATA drive (installation target) to a newer Dell Precision T3500 workstation.

I guess the RAID configuration must have been different on the older machine, as I solved the problem by going into the System Setup>Drives>SATA Operation and selecting RAID Autodetect / ATA ..... (default was: RAID Autodetect / AHCI)

Again, not sure if it's the same problem, but hopefully someone will find this that's looking for an answer...

---

### Post by baha'a on 2011-03-28
I have the same problem (busy box, initramfs, ubuntu 10.10) and I've tried the [commands](http://ubuntuforums.org/showpost.php?p=9786657&postcount=4) [quixote]("http://ubuntuforums.org/member.php?u=133668") have suggested and they didn't work ( I've noticed that my grub knows all the info that he suggested to supply, when I tried to edit the grub) and then tried to do as "hhoyt" suggest but when I run:
```
mount /dev/sda6 /mnt 
```
the terminal gives nothing as it's still working and it never finishes!!

what should I do?

---

### Post by baha'a on 2011-03-28
my problem seems to be as [this](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html) guy says.
I did a system update before the problem and I belive I downloaded a new kernal and it looks like initrd didn't rebuild right.
the guy solved the problem by copying a file from another installation on the same computer (as he has 4 different installations with the same kernal). but I don't have a different installation and I have no idea what to do.

---

### Post by baha'a on 2011-03-28
but there is some difference
the problem didn't start at the first reboot after the update
it started after a system freez and a force reboot:
I was using the computer then I tried to "switch the user" after I choosed "switch user" button the screen gone "black blank" with the mouse pointer, I didn't know what to do so I went to tty1 and logged in and (killed the X :confused:) after I killed the X the system frooze so I made a force reboot and went into the busybox initramfs prompt :(

I hope I find a soulution.
thanks for any help.

Edit: I've noticed that the alarms in my computer are different and they are as [this](http://ubuntuforums.org/showthread.php?t=1633183) thread
it's because of force reboot. I've read that I can fix it from a slax live cd so I'm downloading one :)

---

### Post by BlkRhinoAK on 2011-04-03
> **rcrath said:**
> I had this busybox problem and could not do the grub purge because mounting the sda2 partition where linux resides would not happen from the maverick live CD. Trying to mount them gave a busy signal, saying another process already had hold of it, and umount showed it as not mounted yet. 
 
Elsewhere I read that booting with a slax live cd, the partitions would not be automatically mounted and I could run e2fsck -y -f -v /dev/sda2 from a root text prompt. once I did that, I got my system back. Very easy solution once I found it, unfortunately finding it took 8 hours.
 
This method absolutely worked for me. Had to run the option 2 times before it fixed everything. Thanks dude!!!

---

### Post by rettsin on 2011-04-09
Quixote, I just wanted to say a hearty "thank you" for your posted solution! It worked perfectly for me and barely took any time at all. Smooth like butter.

---

### Post by 4udi on 2013-01-03
Hi,

this problem keeps recurring for me. I had it on ubuntu. Made a fresh install to Mint and it is there again. Everything can work ok for couple of boots and then it is there again. I have used boot-repair +Unetbooting+usb-stick to repair it. Any ideas what I must do to get rid of it permanently? 

-4udi

---

### Post by mdalacu on 2013-03-14
I have this problem after upgrading to 13.04. The good news is that the installer kept he old kernel (from 12.10), and i can select it form grub., which is working great.
How can i make the new kernel boot? How can i reinstall it , or should i wait for a kernel update?
Thank you.

---

### Post by wildmanne39 on 2013-03-14
Old thread closed! Please start a new thread. 
Thanks

---

