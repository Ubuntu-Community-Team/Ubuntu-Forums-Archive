---
title: "&quot;udevadm trigger is not permitted while udev is unconfigured.&quot;"
date: 2010-09-03
forum: General Help
---

### Post by SonicLizzz on 2010-09-03
Hello, I have suddenly gotten a huge problem with my Ubuntu (Studio). 

After I shut it down two days ago, I have been unavailable to get into it again. The only thing I can think of having done during that session, was to update things with apt-get update and apt-get upgrade. The error message I get is "udevadm trigger is not permitted while udev is unconfigured." with a black background. After a few seconds, it says it is not able to boot up, and gives me the option of a few commands which I can see by typing "help" (if you need to know what it says to help me, let me know and I will take a picture of it and write down what it says).

I can boot up with my Live CD, but I am not permitted to use root user and I can only run a few of the commands which I have read others having used in my position (and yes, I remember to put "sudo" in front of the command).

Any suggestions of what I should do?

---

### Post by RufusVS on 2010-09-03
I have the same problem with my Ubuntu Studio.  I was able to boot into a prior
version, but I am a clueless noob about how to fix the damage (or configure udev,
as it seems to be asking...)

---

### Post by SonicLizzz on 2010-09-03
> **RufusVS said:**
> I have the same problem with my Ubuntu Studio.  I was able to boot into a prior
version, but I am a clueless noob about how to fix the damage (or configure udev,
as it seems to be asking...)

Let me know if you find a solution to the problem, then :)
I've concidered deleting Ubuntu Studio and then install Ubuntu again instead, but the problem is that there's so many configurations and files and such on Ubuntu Studio that I just don't want to leave, so I'd rather like to recover the system

---

### Post by RufusVS on 2010-09-03
It wasn't easy to find, but quite easy to do.

I was able to boot up into another version of the Linux kernel.  If you don't have
the option, you might need to boot off a Live CD.  I'm not sure if you'll need
extra steps with Live CD.

But all I had to do was type:

sudo update-initramfs -u -k 2.6.32-24-generic

(the 2.6.32-24-generic was my "problem kernel",  do a:

ls /boot

 to see what versions you have)

The idea is, there is a special ram-based file system used during the bootup
process (ramfs) that is a special image attached to the kernel.  If it's not
created properly, this error occurs.

Let me know if this works for you!

Rufus

---

### Post by SonicLizzz on 2010-09-03
> **RufusVS said:**
> It wasn't easy to find, but quite easy to do.

I was able to boot up into another version of the Linux kernel.  If you don't have
the option, you might need to boot off a Live CD.  I'm not sure if you'll need
extra steps with Live CD.

But all I had to do was type:

sudo update-initramfs -u -k 2.6.32-24-generic

(the 2.6.32-24-generic was my "problem kernel",  do a:

ls /boot

 to see what versions you have)

The idea is, there is a special ram-based file system used during the bootup
process (ramfs) that is a special image attached to the kernel.  If it's not
created properly, this error occurs.

Let me know if this works for you!

Rufus

How did you boot up into the other Linux kernel? My terminal would not let me execute the command through Live CD, but it seems like a good command, so it will probably work if I get into that. I'm a bit of a beginner, so I'm not completely sure what "kernel" is yet though

---

### Post by Audi200Q on 2010-09-03
RufusVS's solution worked for me. The difference is that I had to use the liveCD. Here are the steps I took (learned most of the trick here: [http://georgia.ubuntuforums.org/showthread.php?p=9798322](http://georgia.ubuntuforums.org/showthread.php?p=9798322)).

1. Boot liveCD
2. "sudo fdisk -l" to find your boot disk, in my case it is /dev/sda1.
3. "sudo mkdir /media/newroot"
4. "sudo mount /dev/sda1 /media/newroot", change sda1 to whatever your boot disk is.
5. "sudo chroot /media/newroot"

Now follow RufusVS's suggestion,

6. "ls /boot" to find your latest kenel. Mine has both 2.6.32-24-generic and 2.6.32-24-386. I don't know which one is causing the problem, so I updated both.
7. "sudo update-initramfs -u -k 2.6.32-24-generic"
8. reboot and smile.

Thanks Rufus.

---

### Post by SonicLizzz on 2010-09-03
> **Audi200Q said:**
> RufusVS's solution worked for me. The difference is that I had to use the liveCD. Here are the steps I took (learned most of the trick here: [http://georgia.ubuntuforums.org/showthread.php?p=9798322](http://georgia.ubuntuforums.org/showthread.php?p=9798322)).

1. Boot liveCD
2. "sudo fdisk -l" to find your boot disk, in my case it is /dev/sda1.
3. "sudo mkdir /media/newroot"
4. "sudo mount /dev/sda1 /media/newroot", change sda1 to whatever your boot disk is.
5. "sudo chroot /media/newroot"

Now follow RufusVS's suggestion,

6. "ls /boot" to find your latest kenel. Mine has both 2.6.32-24-generic and 2.6.32-24-386. I don't know which one is causing the problem, so I updated both.
7. "sudo update-initramfs -u -k 2.6.32-24-generic"
8. reboot and smile.

Thanks Rufus.

Weird thing is, this time I could become root with these codes and stuff. The only thing that seems to be a problem is the last bit, because it says:
sudo: unable to resolve host ubuntu
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
grep: /proc/modules: No such file or directory

And it says the grep-part three times in a row, before leaving me to it as root@ubuntu:/#

BUT IT WORKED! SO I'm currently following your 8th step and is VERY thankful! :D

---

### Post by Audi200Q on 2010-09-03
Yes, I forgot to mention the error messages for the last step. Just like what you did, I ignored them and it worked.

---

### Post by ric_h on 2010-09-03
This looks perfect - does anyone know how to boot a live CD in a Parallels Virtual Machine?

Richard

---

### Post by Motomouse on 2010-09-04
I had the same problem with the 2.6.32-24-generic on a regular Ubuntu 10.04 after I run the updates yesterday. Perhaps the problem is related to the latest updates? 

Regards
Ralph

---

### Post by SonicLizzz on 2010-09-04
> **Motomouse said:**
> I had the same problem with the 2.6.32-24-generic on a regular Ubuntu 10.04 after I run the updates yesterday. Perhaps the problem is related to the latest updates? 

Regards
Ralph

I think it is, because updating is the ONLY thing I can think of that could've caused it for my situation

---

### Post by illgoten on 2010-09-04
Hi there guys. I'm a newbie to Ubuntu, almost in despair haha..
Anyway, I tried to update the kernel, that is:

root@ubuntu:/# update-initramfs -u -k 2.6.32-24-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory

What am I supposed to do now?

---

### Post by illgoten on 2010-09-04
Certainly I had all these problems and I'm trying to boot again, cos after updating some libs I got the message "udevadm trigger is not permitted..".

---

### Post by stevenwscott on 2010-09-05
:)
update-initramfs as specified fixed me up right nice. Thanks a million! 

SWS

---

### Post by JTZ on 2010-09-05
@illgoten

I followed the instructions and couldn't get it to work either. But I eventually did get it to work. For the sake of posterity, I'll include what I did.

First I tried to reboot, holding down the shift key so I could choose a different kernel from Grub. That didn't work at all after trying a bunch of different things.

Next off, I had a Ubuntu 10.04 Desktop CD handy (I'm running a server system), so I booted my machine from this disk with the Live CD option (Try Ubuntu w/o installing). I followed the instructions and tried to do a "sudo update-initramfs –u -k 2.6.32-24-generic-pae" after chrooting and got the same result as I was supposed to, but alas, rebooting left me with the same error message

So I booted again into the live CD, chrooted again, and since it was during an update that failed, I ran "dpkg --confgure -a". It finished the failed update and fixed my problem. I rebooted and everything worked fine.

HTH

-JT

---

### Post by rossoneri711 on 2010-09-05
hello,

I am getting the same error, and i tried following the procedure you mentioned.

1. Boot liveCD
2. "sudo fdisk -l"
3. "sudo mkdir /media/newroot"
4. "sudo mount /dev/sda1 /media/newroot"
5. "sudo chroot /media/newroot"
6. "ls /boot" to find your latest kenel. 
7. "sudo update-initramfs -u -k 2.6.32-24-generic"
8. "dpkg --configure -a" as JTZ mentioned in the last post

I also tried 

sudo apt-get update
sudo apt-get dist-upgrade

but i get 0 packets to be installed.

I really dont know what else to do..please help

---

### Post by rossoneri711 on 2010-09-05
anyone guys? i am really desperate to get this working again...

---

### Post by illgoten on 2010-09-05
Hi there dudes.
Thanks to all of you for replying. After rebooting some times, and trying all procedures, 
I got to boot my system, sounds kinda 'spiritual' sometimes hahaha.. 
But, actually after updating the kernel I received three subsequent error  messages, of paths that didn't exist.
I mean, after mounting, chrooting and trying to update, I got the errors. 
So I just rebooted like other member said and now I'm on my Ubuntu writing on this post.

Here is what I've done:

1. Boot liveCD
2. "sudo fdisk -l" to find your boot disk, in my case it is /dev/sda5.
3. "sudo mkdir /media/newroot"
4. "sudo mount /dev/sda5 /media/newroot", change sda1 to whatever your boot disk is.
5. "sudo chroot /media/newroot"

6. apt-get update
7. apt-get dist-upgrade

Otherwise, if you are more lucky than me, try:

'6. "ls /boot" to find your latest kenel. Mine has both 2.6.32-24-generic  and 2.6.32-24-386. I don't know which one is causing the problem, so I  updated both.
7. "sudo update-initramfs -u -k 2.6.32-24-generic"
8. reboot and smile.'

---

### Post by tkoco on 2010-09-05
> **illgoten said:**
> Hi there dudes.
Thanks to all of you for replying. After rebooting some times, and trying all procedures, 
I got to boot my system, sounds kinda 'spiritual' sometimes hahaha.. 
But, actually after updating the kernel I received three subsequent error  messages, of paths that didn't exist.
I mean, after mounting, chrooting and trying to update, I got the errors. 
So I just rebooted like other member said and now I'm on my Ubuntu writing on this post.

Here is what I've done:

1. Boot liveCD
2. "sudo fdisk -l" to find your boot disk, in my case it is /dev/sda5.
3. "sudo mkdir /media/newroot"
4. "sudo mount /dev/sda5 /media/newroot", change sda1 to whatever your boot disk is.
5. "sudo chroot /media/newroot"

6. apt-get update
7. apt-get dist-upgrade

Otherwise, if you are more lucky than me, try:

'6. "ls /boot" to find your latest kenel. Mine has both 2.6.32-24-generic  and 2.6.32-24-386. I don't know which one is causing the problem, so I  updated both.
7. "sudo update-initramfs -u -k 2.6.32-24-generic"
8. reboot and smile.'

Don't make the mistake which I made. I had copied the kernel filename in step 7. Step 7 needs the kernel version, not the filename. After I figured out what I was doing wrong, the fix worked like a champ! From what I can see in the google searches, this particular problem has occurred several times in the past. Thanks to everyone who responded to this thread!

Also, the version of the LiveCD MUST match the version of the system which you are trying to fix. Initially, I tried using an older 9.10 I386 LiveCD to fix a 10.04 X64 Desktop. Step 5 of the procedure failed miserably!

---

### Post by rossoneri711 on 2010-09-06
> **tkoco said:**
> Don't make the mistake which I made. I had copied the kernel filename in step 7. Step 7 needs the kernel version, not the filename. After I figured out what I was doing wrong, the fix worked like a champ! From what I can see in the google searches, this particular problem has occurred several times in the past. Thanks to everyone who responded to this thread!

Also, the version of the LiveCD MUST match the version of the system which you are trying to fix. Initially, I tried using an older 9.10 I386 LiveCD to fix a 10.04 X64 Desktop. Step 5 of the procedure failed miserably!


hello,

you are talking about the version and not the filename, so what should be the command?

Is this wrong? "sudo update-initramfs -u -k 2.6.32-24-generic"

I tried the procedure mentioned 3 times and still i get the same error.

---

### Post by idistech on 2010-09-06
same issue..solution worked for me....booted to an earlier verision and ran the update-initramfs

nothing to do with those of us still on grub 1.5 as a result of the 9.10-10.4 upgrade?...most of mine are still on grub 1.5 and had the broken with two so far.

G

---

### Post by rossoneri711 on 2010-09-07
i finally found out why mine wasnt working.

i  saw that i had a lot of kernels in ls/boot so as advises in bugs i did

sudo update-initramfs -u -k all

and finally it worked!!!!

thank god

do i need all those or not?

---

### Post by noodletaboo on 2010-09-08
It worked for me too!!!
Thanks a lot =))

---

### Post by MarseHole on 2010-09-08
I encountered the same problem after updating a few days ago on my  Ubuntu 10.04 system, however my 'problem kernel' was 2.6.32-24-386.

I booted another kernel from my grub menu (2.6.32-24-generic, somewhat ironically) and used RufusVS'

```
sudo update-initramfs -u -k 2.6.32-24-386
```

to update the kernel image.
Job done.

As tkoco said, similar issues have previously been observed after system updates (e.g. [http://bit.ly/nlJg7]("http://bit.ly/nlJg7")). Looks like it might have something to do with a prompt to reboot the system before it's been fully configured...?

In any case, thanks to all for a quick fix :D

MA

---

### Post by sobolosrios on 2010-09-09
RufusVS' steps worked for me as well.  I love this place.


(Toshiba nb305 netbook)

---

### Post by CT Husky on 2010-09-11
Re the boot-up error  “udevadm trigger is not permitted while udev is unconfigured”

Thanks to all.  From the perspective of a total noobie-boobie, here are the steps:

1.Turn off and restart your computer, while keeping your finger on the “ESC” button.
2.When “GRUB” comes up on the screen while booting, hit ESC to get to the GRUB menu
3.Your current kernel will be highlighted (in my case it was 2.6.32-24-386); use the up/down arrow keys to pick another kernel to use temporarily to boot (in my case, I chose 2.6.32-24-generic)
4.Then press “enter”; the machine should continue to boot up somewhat normally, though it may look a little funny.
5.Log in.
6.Go to a terminal (Applications>Accessories> Terminal)
7.Type in Rufus's command “sudo update initramfs -u -k 2.6.32-24-386” (Note: you should substitute whatever the numbers of the bad kernel are, mine happened to be 2.6.32-24-386)
8.When it finishes, X out of the terminal, go to the shut-down menu, and choose “RESTART”;
9.That should do the trick.

---

### Post by AKnightintheDesert on 2010-09-14
I am trying to do this on a Ubuntu server that has a software raid.  It is not letting me mount the drive because the partitions are raid members.  Is there a way to do this??

(Solved) Not sure if this is a server thing or a Grub2 thing but you have to hold down "Shift" to get the Grub menu to show.

---

### Post by arno_de_Parno on 2010-09-15
> **RufusVS said:**
> It wasn't easy to find, but quite easy to do.

I was able to boot up into another version of the Linux kernel.  If you don't have
the option, you might need to boot off a Live CD.  I'm not sure if you'll need
extra steps with Live CD.

But all I had to do was type:

sudo update-initramfs -u -k 2.6.32-24-generic

(the 2.6.32-24-generic was my "problem kernel",  do a:

ls /boot

 to see what versions you have)

The idea is, there is a special ram-based file system used during the bootup
process (ramfs) that is a special image attached to the kernel.  If it's not
created properly, this error occurs.

Let me know if this works for you!

Rufus
Where is the karma +1 button? (I guess I would register 16 different accounts on this forum to give you what you deserve) 
This Did it For Me!

Because I work with LVM, I had to boot from the 10.04 alt. CD, select repair, mount /dev/mapper/*systemboot* as `/´-partition, and entered into a shell. 
First i mounted /dev , /proc and /sys
Then I mounted /dev/sda1 to `/boot´ - LVM needs a boot partition

I followed your hints and now I have a working terminal server as well as 16 happy colleagues. 

Did I already give you Karma?

---

### Post by gotsanity on 2010-10-01
For those of you using hardware raid (fakeraid) just boot into your alt CD and when you get into a root shell follow the following:

```

# mount /dev
# mount /proc
# mount /sys
# sudo update-initramfs -u -k all

```

then reboot

worked great for me

---

### Post by kapcom01 on 2010-10-09
hello, I'm just adding my experience.

In my case I had BURG instead of GRUB and it seems that it doesnt update automatically..

from the boot menu:
-I pressed "e" to edit the boot entry manually
-I changed the kernel version number to the new one (..24 to ..25)
-Then ESC or CTRL+X to take me back to the menu
-and finally ENTER to boot.

Then from within ubuntu i replaced BURG with GRUB because i dont want this to happen again (although burg was beautiful).

-Just type sudo install grub /dev/sdX (replace X with yours..)

---

### Post by randomlysid on 2010-10-10
Hi,

I have the same problem, 
"Udevadm trigger is not permitted while udev is not configured"

I tried some of the methods explained in this thread, but my netbook doesn't have a disk drive, hence I can't use a liveCD. I tried booting from USB, but I get the same error. 

I am open to a solution that will wipe all my data of this machine, as long as I can get back to using it!

Thanks!

---

### Post by RoyStrachan on 2010-10-21
> **RufusVS said:**
> It wasn't easy to find, but quite easy to do.

I was able to boot up into another version of the Linux kernel.  If you don't have
the option, you might need to boot off a Live CD.  I'm not sure if you'll need
extra steps with Live CD.

But all I had to do was type:

sudo update-initramfs -u -k 2.6.32-24-generic

(the 2.6.32-24-generic was my "problem kernel",  do a:

ls /boot

 to see what versions you have)

The idea is, there is a special ram-based file system used during the bootup
process (ramfs) that is a special image attached to the kernel.  If it's not
created properly, this error occurs.

Let me know if this works for you!

Rufus
Thanks RufusVS.  Worked like a charm; you saved quite a bit of my hair!

---

### Post by javawarrior on 2010-10-22
I got this error today after accepting a bunch of updates to ubuntu 10.04.1 on my dell inspiron 1721 laptop. Let me summarize the full story for anyone else who may be trying to get ubuntu working on this machine. 

Initial attempts to install ubuntu 10.04.1 using the live desktop CD failed with this error:

"Failed to create file system. The ext4 file system creation in partition #n of serial ATA RAID pdc_babiiij (stripe) failed."

I googled about and found the solution was to use the 10.04.1 alternate live CD, which would cope with the RAID setup. So I tried this and got to the GRUB boot loader stage before it failed again. After more googling and sifting I eventually found this thread, and ended up being able to boot ubuntu 10.04.1 on my inspiron 1721:

[http://ubuntuforums.org/showthread.php?t=1574765](http://ubuntuforums.org/showthread.php?t=1574765)

(Great work xenton. Huge thanks.)

Having managed to boot I then updated the system. After a post update reboot I then ran into the "udevadm trigger is not permitted while udev is unconfigured" error. Good grief. Quick beer and cigarette, more googling and sifting, and finally I found this thread. But the instructions did not work for me because of the my fakeraid setup. So, if you area also experiencing this problem on a fakeraid machine, here is what I did:

[LIST=1]
[*]Follow the instructions in xenton's excellent tutorial ([http://ubuntuforums.org/showthread.php?t=1574765](http://ubuntuforums.org/showthread.php?t=1574765)) up to the point where you run the "sudo chroot /mnt" command.
[*]Then follow steps 6, 7 & 8 from Audi200Q's summary ([http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9802683&postcount=6](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9802683&postcount=6)) for each of your kernels.
[/LIST]

I have waited a long time to get ubuntu onto this laptop (so long vista) and would never have gotten there on my own. Thanks all.

---

### Post by kingster80 on 2010-10-23
worked like a charm for me too. Mine is running 2.6.32-25. Thank you:guitar:

---

### Post by Seamyst on 2010-10-25
I just installed Lucid on a brand-new Toshiba Satellite C655 (lovely acpi problems...) and rebooted to the udevadm error. Searched, found this thread, followed all the instructions pertaining to LiveCDs. The kernels are 2.6.32-21-generic and 2.6.32-25-generic.

I got to the update steps and ran into problems. When doing "apt-get update" I get a bunch of error messages like this: 
> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname) 
When doing "sudo apt-get dist-upgrade", it says that it was unable to resolve host ubuntu, there are 4 not fully installed or removed, then some errors. > "Can not write log, openpty() failed (/dev/pts not mounted?)"
> "dpkg: error processing grub-pc (--configure): subprocess installed post-installation script returned error exit status 10"
The last error is the same for samba-common. Then it mentions several dependency problems.

The latter two errors also come up if I try "dpkg --configure -a".

All around, it says that errors were encountered while processing: samba-common, smbclient, grub-pc, and samba-common-bin.

Then I try "sudo update-initramfs -u -k all". I get the same "unable to resolve host ubuntu" error, plus this error message for both kernels (32-21-generic and 32-25-generic):
> grep: /proc/modules: No such file or directory
This is repeated three times for each kernel.

Sooooo.... now what?

**Edit:** I reinstalled the OS, since it was new anyway, and installed kernel 2.6.32-36, and presto!

---

### Post by missmoondog on 2010-10-28
haven't been here in ages and don't really even like ubuntu myself, but a friend wanted to install it alongside his windows 7.

he had tried doing the wubi install himself the first time and got this error, udevadm trigger is not premitted while udev is unconfigured, also.

i have since retried uninstalling and reinstalling it twice now. both times, immediately after getting recommended updates, ubuntu becomes hosed! nothing new with that as that is half of why i quit using this bloated thing a long time ago. often wonder if they ever test this crap out before issuing updates?

anyway, way to many changes to have to go through for something that obviously wasn't properly tested and is such an issue as a search on any search engine finds.

have since talked friend into not wanting ubuntu on his system and to just stick with windows as they at least half way test their updates before hand.

sorry about the rant, but every time i've ever used ubuntu this is exactly what has happened (hosed) in a very short amount of time using it.

edit:
just for the heck of it, i tried installing ubuntu using wubi on one of my systems. installed and all just fine, but within 5 minutes of being online, internet would just quit working. logout and back in would get it working again. for the heck of it, downloaded seamonkey. it continuosly crashes! went back into synaptic and suddenly have 115 repository places it checks for updates and i haven't changed a thing there. log out and back in again. go straight to update manager, get updates, and get this udevadm error on my machine!! what a pos!! like i said, no wonder i quit using this garbage!!

will stick with zenwalk, at least it works!! must make a mental not to NEVER try this POS distro again!!

in fact, can an admin delete my account so i won't be able to login to this slow a** forum also!! sheesh!!

good-bye!!

---

### Post by AlexanderDGreat on 2010-11-05
Worked for me, I have a separate /boot partition here's what I've done:

1. sudo mkdir /media/newroot/
2. sudo mount / /media/newroot/
3. cd /media/newroot/
4. sudo mount /dev/sda1 boot
5. sudo chroot /media/newroot/

Then proceed with the rest of the fix.

Thanks for all who's helping and building our wonderful community and distro.

---

### Post by Seamyst on 2010-11-05
Since I updated to the 2.6.32-36 kernel, an older kernel (32-25, I believe) still comes up in the Update Manager. If I go ahead and install it, does anyone know if my computer will (possibly) have this problem again, when I still boot into the newer kernel?

Or if that's not a good idea, is there any way to remove the older kernel from UM?

---

### Post by AlexanderDGreat on 2010-11-06
@Seamyst - Hey man LOCK the VERSION of your kernel!

System > Administration > Synaptic Package Manager:

Type:

```
linux-headers
```

Highlight something like:

linux-headers-2.x.xx-x
linux-headers-generic
linux-headers

```
linux-image
```

Highlight something like:

linux-image-2.x.xx-x
linux-image-generic

```
linux-server
```
^ If you're using a server.

Then Package > Lock Version. Now Update won't ask you for NEW INSTALL of kernels which you don't need in the mean time.

Let me know if this works.

---

### Post by Seamyst on 2010-11-06
> **AlexanderDGreat said:**
> @Seamyst - Hey man LOCK the VERSION of your kernel!

System > Administration > Synaptic Package Manager:

Type:

```
linux-headers
```

Highlight something like:

linux-headers-2.x.xx-x
linux-headers-generic
linux-headers

(snip)

Then Package > Lock Version. Now Update won't ask you for NEW INSTALL of kernels which you don't need in the mean time.

Let me know if this works.

When I searched for linux-headers, it came up with a crapload of headers - all of them like "linux-headers-2.6.32-21" and such. It also includes what I already have installed. So my next question is, do I follow your instructions for what *is* installed, or what *isn't*?

---

### Post by AlexanderDGreat on 2010-11-06
You should lock what is INSTALLED:

I locked mine to, please see attached pictures:

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/linux-headers.png[/IMG]

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/linux-image.png[/IMG]





Since I'm using 4gb of ram I installed Ubuntu PAE that's why I also have linux-server, in your case, you might not have one.

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/linux-server.png[/IMG]

Hope this helps.

---

### Post by AlexanderDGreat on 2010-11-06
Take note: this will only lock your kernel forever, that is, Update Manager won't ever ask to NEW INSTALLS of kernels.

It's always a good practice to leave at least 2 versions of kernels in case something goes wrong with your current kernel, you can just as easily switch to other ones, by holding right shift key during boot.

Locking a kernel simple means, you won't be asked to NEW INSTALL any other kernels forever. :)

---

### Post by kedacheng on 2010-11-12
Thank you for you guys, this really saved my life when i busted the computing workstation in the office.:P

---

### Post by chek2fire on 2010-11-20
Hello guys :)
After the last kernel update i cant boot to my system and i have this error message

> nit: Failed to spawn hostname main process: unable to execute: No such file or directory
init: Failed to spawn mountall post-stop process: unable to execute: No such file or directory

i try your guide to fix the problem but when i give 

sudo chroot /mount/newroot/ 

in step 5 

returns


chroot: cannot run command ' /bin/bash' : No such file or directory

and then i cant give update-initramfs because it say is  disable since is runing on read-only media.
What i am doing wrong?

---

### Post by chek2fire on 2010-11-20
i have find this

[http://www.computing.net/answers/linux/the-chroot-nightmare/4588.html](http://www.computing.net/answers/linux/the-chroot-nightmare/4588.html)

and this

[http://serverfault.com/questions/162362/chroot-fails-cannot-run-command-bin-bash-no-such-file-or-directory](http://serverfault.com/questions/162362/chroot-fails-cannot-run-command-bin-bash-no-such-file-or-directory)

but i dont know what to do to work chroot

---

### Post by AlexanderDGreat on 2010-11-21
@chek2fire - first of all, do you have a separate boot partitions? How many partitions do you have? You can see them type sudo fdisk -l in a live cd.

Chroot - simply means creating your "own little world" in a linux box.

1. first boot off a live cd
2. mkdir the necessary folders
3. be sure to mount boot only inside the root directory (this maybe your problem)
4. chroot in the root directory

---

### Post by chek2fire on 2010-11-21
i have done this but nothing happens. The strange thing is that in my installation are missing some folders like /bash /lib32 /lib64. I will try to copy that folder from the live cd

---

### Post by chek2fire on 2010-11-21
The problem must be more serious. I have see that all the /bin folder was empty. I have copy files from live cd to the /bin folder and i have finally execute update-initramfs but now i cant login in to my system. It say something about mount. In recovery mode i have this errors

/dev/sda1: clean
EXT4-fs (sda1):Unrecognized mount option "realtime" or missing value
An error occurrred while mounting / 
Press S to skip mounting or M for manual recovery
mountall: mount / [413] terminated with status 32
mountall: Filesystem could not be mounted: /

---

### Post by AlexanderDGreat on 2010-11-21
> installation are missing some folders like /bash /lib32 /lib64 - I also don't have these folders, if that's not a typo error, and /bash, means it's located in the file system not inside a folder.

> chroot: cannot run command ' /bin/bash' : No such file or directory - means you weren't able to mount the / directory properly.

This happens when the folders aren't properly mounted. Do you have a separate boot partition? How many partitions do you have?

> I have see that all the /bin folder was empty. - yes, because it's not mounted yet OR you're not inside the jail yet.

> /dev/sda1: clean
EXT4-fs (sda1):Unrecognized mount option "realtime" or missing value
An error occurrred while mounting /
Press S to skip mounting or M for manual recovery
mountall: mount / [413] terminated with status 32
mountall: Filesystem could not be mounted: / - it's because you've updated initramfs without ALL THE NECESSARY FOLDERS. You can't simply copy and paste folders inside the chroot. It's like installing from a cd with corrupt or missing files.

---

### Post by chek2fire on 2010-11-21
Ok thanks for the help and i finally i am again inside my system. The first thing that i have to do is to copy the bin folder from live cd to my partition. Then i have done with success the initramfs update and then i have to edit fstab and change the realtime to the correct relatime. Thanks again :)

---

### Post by carvao on 2010-12-05
> **AlexanderDGreat said:**
> Worked for me, I have a separate /boot partition here's what I've done:

1. sudo mkdir /media/newroot/
2. sudo mount / /media/newroot/
3. cd /media/newroot/
4. sudo mount /dev/sda1 boot
5. sudo chroot /media/newroot/

Then proceed with the rest of the fix.

Thanks for all who's helping and building our wonderful community and distro.

this solution also worked for me. i have two partitions, each one with a different ubuntu version: 10.10, previous, and a new 10.04. 
both was working fine until the upgrade in the 10.04 version, and then i got the message "udevadm trigger is not permitted while udev is unconfigured." when tried to choose 10.04 to boot.

what i did differently that worked for me was instead of "sudo mount / /media/newroot/" in the 2nd line, i specified my two partitions with ubuntu. "sudo mount /dev/sdb5 /media/newroot/" and "sudo mount /dev/sbd7 /media/newroot/", each one at a time, repeating the whole sequence of commands. i don't know which one was the solution but i worked.

thanks

---

### Post by yamasaki2025 on 2010-12-14
> **rossoneri711 said:**
> hello,

I am getting the same error, and i tried following the procedure you mentioned.

1. Boot liveCD
2. "sudo fdisk -l"
3. "sudo mkdir /media/newroot"
4. "sudo mount /dev/sda1 /media/newroot"
5. "sudo chroot /media/newroot"
6. "ls /boot" to find your latest kenel. 
7. "sudo update-initramfs -u -k 2.6.32-24-generic"
8. "dpkg --configure -a" as JTZ mentioned in the last post

I also tried 

sudo apt-get update
sudo apt-get dist-upgrade

but i get 0 packets to be installed.

I really dont know what else to do..please help


Thank solved for me!!:P

---

### Post by zu87 on 2010-12-15
> **AlexanderDGreat said:**
> Worked for me, I have a separate /boot partition here's what I've done:

1. sudo mkdir /media/newroot/
2. sudo mount / /media/newroot/
3. cd /media/newroot/
4. sudo mount /dev/sda1 boot
5. sudo chroot /media/newroot/

Then proceed with the rest of the fix.

Thanks for all who's helping and building our wonderful community and distro.

Unfortunately none of the fixes offered here have solved my problem, though I feel AlexanderDGreat's fix above is the closest.

I have seperate /boot, /swap, /home and root partitions on my hard drive. 

The above solution fails at step 2. I get the following error:
mount: / is not a block device

can anybody think of a solution for this?
I'm very new to Linux in general, still going through some growing pains :)

---

### Post by zu87 on 2010-12-15
Ok, so I solved my problem with step 2 (appologies, the answer was here all along) but now when I run:

sudo update-initramfs <kernel>

I get an error from gzip "no space left on device"
Is this because I'm booting from USB instead of CD?

Thank you all for your help in advance

Edit: Ok so I figured this one out too. My /boot partition is very small (50MB). There were two solutions:

1. repartition the hard drive to increase the size of the /boot partition (I've seen 500MB recommended) or ro include /boot in the root directory.

2. Delete all files from previous kernels to free up space.

---

### Post by yoramdavid on 2010-12-17
> Re: "udevadm trigger is not permitted while udev is unconfigured."
Ok, so I solved my problem with step 2 (appologies, the answer was here all along) but now when I run:

sudo update-initramfs <kernel>

I get an error from gzip "no space left on device"
Is this because I'm booting from USB instead of CD?

Thank you all for your help in advance

Edit: Ok so I figured this one out too. My /boot partition is very small (50MB). There were two solutions:

1. repartition the hard drive to increase the size of the /boot partition (I've seen 500MB recommended) or ro include /boot in the root directory.

2. Delete all files from previous kernels to free up space.
Last edited by zu87; 1 Day Ago at 10:47 AM.. Reason: solved 

I am having the same problem. At about half way through installing, after downloading all the files needed, it tells me not enough space. But there is space, I have 128Mb free on the /boot partition and 1.5 Gb on the /Ubuntu partition.

The above solution fails at step 2. I get the following error:
mount: / is not a block device

I cannot do the initramfs update because it says it is a read-only directory.

With the chroot /media/newroot I get the error "cannot run command '/bind/bash': no such file or directory"

I tried from both a USB drive and from a CD.

Any help is welcome, thanks.

Update:
I realized a "File System" drive (folder (inode/directory) was created during this process which gets out of space.
Location: computer:///, Volume: unknown.
Is there something I am doing wrong?

---

### Post by thesubroot on 2010-12-18
i'm using ubuntu 10.10, and i got that error after updating the system.
I try to make all the steps u said, but i got those errors:
```
sudo: unable to resolve host ubuntu
update-initramfs: Generating /boot/initrd.img-initrd.img-2.6.35-23-genric
grep: /boot/config-initrd.img-2.6.35-23-genric: No such file or directory
WARNING: missing /lib/modules/initrd.img-2.6.35-23-genric
Device driver support needs thus be built-in linux image!
FATAL: modules must be specified using absolute paths.
"initrd.img-2.6.35-23-genric" is a relative path
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
WARNING: Couldn't open directory /tmp/mkinitramfs_h1c23s/lib/modules/2.6.35-22-generic: No such file or directory
FATAL: Could not open /tmp/mkinitramfs_h1c23s/lib/modules/2.6.35-22-generic/modules.dep.temp for writing: No such file or directory
```
plz help

---

### Post by Mecasickle on 2010-12-20
Just installed Ubuntu 10.10 anda had this error after my 5th boot. I installed it from USB. Anyway , any other solution?

---

### Post by cleverbubbles123 on 2010-12-20
> **thesubroot said:**
> i'm using ubuntu 10.10, and i got that error after updating the system.
I try to make all the steps u said, but i got those errors:
```
sudo: unable to resolve host ubuntu
update-initramfs: Generating /boot/initrd.img-initrd.img-2.6.35-23-genric
grep: /boot/config-initrd.img-2.6.35-23-genric: No such file or directory
WARNING: missing /lib/modules/initrd.img-2.6.35-23-genric
Device driver support needs thus be built-in linux image!
FATAL: modules must be specified using absolute paths.
"initrd.img-2.6.35-23-genric" is a relative path
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/initrd.img-2.6.35-23-genric/modules.dep: No such file or directory
WARNING: Couldn't open directory /tmp/mkinitramfs_h1c23s/lib/modules/2.6.35-22-generic: No such file or directory
FATAL: Could not open /tmp/mkinitramfs_h1c23s/lib/modules/2.6.35-22-generic/modules.dep.temp for writing: No such file or directory
```
plz help
Yeah I got an error like that too. I think (not an expert) that it is a problem when you run the chroot command, and it thinks you are in a location other than /media/newroot?

---

### Post by Mecasickle on 2010-12-20
Stupid, update manager. Having the problem on my new Alienware m11x. Hmm, I've pretty much tried everything on this thread (booting from USB stick).  But nothing.

I get the Chroot error or I can't update my kernel because I lack of "/bin/bash" file.

---

### Post by cleverbubbles123 on 2010-12-21
> **Mecasickle said:**
> Stupid, update manager. Having the problem on my new Alienware m11x. Hmm, I've pretty much tried everything on this thread (booting from USB stick).  But nothing.

I get the Chroot error or I can't update my kernel because I lack of "/bin/bash" file.
yh, thats the file i "don't" have ( even though it IS in the directory /bin)

---

### Post by cleverbubbles123 on 2010-12-21
root@ubuntu:/# sudo update-initramfs -u -k all
sudo: unable to resolve host ubuntu
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.35-23-generic





what is wrong?

---

### Post by AlexanderDGreat on 2010-12-21
> gzip: stdout: No space left on devicewhat is wrong?

---

### Post by Mecasickle on 2010-12-21
In my case, I get this error:

ubuntu@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg
ubuntu@ubuntu:~$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
cp: cannot stat `/vmlinuz': No such file or directory

What should I do about the /vmlinuz??
Thanks!

---

### Post by AlexanderDGreat on 2010-12-22
> cp: cannot stat `/vmlinuz': No such file or directory - it means it's not mounted. You need to mount it first, did you follow the exact steps here? Is your /boot a separate partition?

---

### Post by Mecasickle on 2010-12-24
I've follows these isntructions:
1) Boot Live CD (USB stick in my case for Ubuntu 10.10 in my case)
2) sudo fdisk -l
3) sudo mkdir /media/newroot
4) sudo mount /dev/sdb1 /media/newroot
5)sudo chroot /media/newroot
6) ls /boot
7) sudo update-initramfs -u -k 2.6.35-22-generic
8) Reboot & smile.

Basically on step 5 it bugs because it tells me that this when I perform the chroot operation:

ubuntu@ubuntu:~$ sudo chroot /media/newroot
chroot: failed to run command `/bin/bash': No such file or directory

When I perform the sudo fdisk -l
I get  this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb33fd09d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       38914   297169240    7  HPFS/NTFS

Disk /dev/sdb: 4009 MB, 4009754624 bytes
93 heads, 8 sectors/track, 10526 cylinders
Units = cylinders of 744 * 512 = 380928 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10527     3915772    c  W95 FAT32 (LBA)

-----

I guess that what I have to mount is my sdba1 partition, ive tried every other option, with my sda1, sda2, sd3 partition too, but no luck. So I really don't understand if I'm "moutning my boot partition correctly"

How do I know if my /boot is a separate partition ?

Thanks man! Sorry for the late replay, I've been busy with exams.

Any other direction I should be pointing out to?

---

### Post by Mecasickle on 2010-12-25
Figured out that the best thing to do, is to reinstall ubuntu (wubi version).

Cheers

---

### Post by AlexanderDGreat on 2010-12-29
I'm so sorry haven't been able to reply. But really, if you have time you should study more on how to CHROOT.

Simply put, CHROOT, is just mounting your whole system to a folder and going inside that folder and have your little private space in there to install, run commands, apart from what is running in your current LOGIN desktop.

Here, I pasted a simple CHROOT'ing example:

```


METHOD 3 - CHROOT

This method of installation uses the chroot command to gain access to the broken
system's files. Once the chroot command is issued, the LiveCD treats the broken
system's / as its own. Commands run in a chroot environment will affect the broken
systems filesystems and not those of the LiveCD.

1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later). Please note that the
Live CD must be the same as the system you are fixing - either 32-bit or
64-bit (if not then the chroot will fail).

2. Open a terminal - Applications, Accessories, Terminal.

3. Determine your normal system partition - (the switch is a lowercase "L")

      sudo fdisk -l
          * If you aren't sure, run

            df -Th. Look for the correct disk size and ext3 or ext4 format. 
4. Mount your normal system partition:
          * Substitute the correct partition: sda1, sdb5, etc. 

      sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt
5.

      Only if you have a separate boot partition:
          * sdYY is the /boot partition designation (for example sdb3)
          *

            sudo mount /dev/sdYY /mnt/boot 
6. Mount the critical virtual filesystems:

      sudo mount --bind /dev  /mnt/dev
      sudo mount --bind /dev/pts  /mnt/dev/pts
      sudo mount --bind /proc /mnt/proc
      sudo mount --bind /sys  /mnt/sys
7. Chroot into your normal system device:

      sudo chroot /mnt
8. If there is no /boot/grub/grub.cfg or it's not correct, create one using

      update-grub
9. Reinstall GRUB 2:
          *

            Substitute the correct device - sda, sdb, etc. Do not specify a
partition number. 

      grub-install /dev/sdX
10.

      Verify the install (use the correct device, for example sda. Do not specify a
partition): sudo grub-install --recheck /dev/sdX
11.

      Exit chroot: CTRL-D on keyboard
12. Unmount virtual filesystems:

      sudo umount /mnt/dev/pts
      sudo umount /mnt/dev
      sudo umount /mnt/proc
      sudo umount /mnt/sys
          * If you mounted a separate /boot partition:

            sudo umount /mnt/boot 
13. Unmount the LiveCD's /usr directory:

      sudo umount /mnt/usr
14. Unmount last device:

      sudo umount /mnt
15. Reboot.

      sudo reboot 

Post-Restoration Commands

Once the user can boot to a working system, try to determine why the
system failed to boot. The following commands may prove useful in locating and/or fixing the problem.

    *

      To refresh the available devices and settings in /boot/grub/grub.cfg
          o

            sudo update-grub 
      To look for the bootloader location.
          o

            grub-probe -t device /boot/grub 

      To install GRUB 2 to the sdX partition's MBR (sda, sdb, etc.)
          o

            sudo grub-install /dev/sdX 
      To recheck the installation. (sda, sdb, etc.)
          o

            sudo grub-install --recheck /dev/sdX


```

It's taken from here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") - when a user wants to FIX GRUB, just pay attention to METHOD #3 - And ignore all the rest of technojabber.

I've looked on this myself when I was studying and messing with my GRUB. It helped me a lot to understand what CHROOT is all about when I was on the udevadm problem.

Hope you find it useful.

---

### Post by potiphera on 2011-01-05
After a kernel update and reboot on 64-bit Ubuntu Studio 10.04, I'm getting this error, in combination with an error that says "cryptsetup: lvm device name [long hexadecimal device name] does not begin with /dev/mapper/" (I have full disk encryption enabled).  I've gotten the latter error before, and was able to fix it by pressing Shift and entering GRUB.  Now I can't because of the udevadm error.  I tried Audi200Q's advice, and all the commands seemed to work except the update-initramfs commands gave me an error saying "cryptsetup: WARNING: invalid line in /etc/crypttab -", and my system still won't boot.  I posted more about it [here]("http://ubuntuforums.org/showthread.php?t=1631203").  Is there anything else I can try?  Thanks!

---

