---
title: "help with file system error"
date: 2010-03-04
forum: General Help
---

### Post by gabrielcik on 2010-03-04
Hello,

Suddenly today during the start up the pc stopped to respond while doing a file system check...

I switch it off, restarted and everything seemed to be fine, i got the desktop without troubles.

Then i tried to boot from the live Key and run a fsck but it didn't work, i got some error like:

superblock could not be read....
and at the end it says to run e2fsck 

I did it and i got the same error...

So i restarted ubuntu and i decided to try:

sudo touch /forcefsck
sudo shutdown -f now

and i got a blue screen where i selected the first option (something alike restart in normal way)

at the next restart i finally got the checking and it was fine!

So I don't really understand what is the problem and why i can't run fsck or e2fsck from live key

any help, pls? thank you!

---

### Post by gabrielcik on 2010-03-04
I tried again from usb key...

If i run e2fsck or fsck  to /dev/sda i get this error:

The super block could not be read or does not describe a correct ext2.....
you may try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

If i run e2fsck or fsck /dev/sda1 
i don't get any error:  /dev/sda1: clean... and number of files and blocks

I use ext4 journaled on a ssd drive (aligned by leaving 1 mb before the partition).

---

