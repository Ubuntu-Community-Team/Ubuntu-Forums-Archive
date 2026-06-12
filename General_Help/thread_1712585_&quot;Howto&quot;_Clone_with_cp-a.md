---
title: "&quot;Howto&quot; Clone with cp-a"
date: 2011-03-22
forum: General Help
---

### Post by Lianli on 2011-03-22
This is just a simple clone that I do every so often to keep as a back up
incase something bad hapens. It has saved me a few times in th past.
Every so often when I feel my system is the most stable, or if I made
a lot of changes, i redo the clone. I even wrote a lil script to
automate it.

I'll just explaine how i do it for my system, and if you try this
it should be easy to alter for your system.

I have three hard drives in my system. they are recognized as
sda sdb and sdc. My main install is on disk sda with this
partition scheme...

sda1 = /boot 
sda2 = swap
sda3 = / 

Basically, I create a partition scheme that matches my main system
partition scheme to another disk. To make things easier  i use the 
same amount of partitions as sda has, although they don't have to
match. It would just be alil more complicated if they didn't. The sizes
don't have to match as long as there is enough room to hold
everything. you could easily do this to a usb drive as well.

I use disk sdb as my backup install. I partition sdb similar to
sda disk so i have partitions

sdb1 = /boot
sdb2 = swap
sdb3 = /

I make sure sdb1 is bootable. I really don't need to make
a swap partition, but i do anyway, just in case my main disk fails.
I use fdisk, but you can use whaterver to accomplish the partitioning.

After that's done, I use a live cd and boot into it. I like using 
Puppy Linux live cd, but it doesn't matter as long as you can
boot up out of you main install. 

Ok, im in puppy linux and I need to mount sda1 sdb1 sda3 and sdb3.
Puppy linux by default mounts these dives to /mnt but you could
mount them anywhere you like. Once I have my partitions mounted
The rest is simple...

I want to copy everything from sda1 to sdb1....

code...
cp -a -v /mnt/sda1/* /mnt/sdb1

The above command copies everything preserving permissions and all
links etc. the -v switch isn't needed, It just lets me see the copying
being done. When it's finished, I do same for sdb3...

code...
cp -a -v /mnt/sda3/* /mnt/sdb3

After it finishes, I have to edit a couple files to reflect sdb verses sda.
/etc/fstab
/etc/mtab

so i open /mnt/sdb3/etc/fstab and alter the entries to reflect sdb instead of
the sda partitions. If you use uuid you can run blkid in a terminal to
list the uuid's for you.

Then in my /mnt/sdb3/etc/mtab the one entry that needs changed from
sda to sdb

After that you need to add a boot listing to grub to boot your sdb clone.
I don't like grub2 and down graded to grub legacy. For me it's as simple
as copying and pasting the entries in my menu.list and just alter
the copied entries to reflect sdb instead of sda. You can do the same
for grub2 but you need to add your entries for booting sdb into /etc/grub.d
i think it is and add a file with the entries in it and then update grub for
it to add them to your /boot/grub/grub.cfg file. Ugh that's just a huge over kill
to me and is frustrating, but some people love grub2.

That's it. after you boot into your cloned install, you may need to alter 
some specific user files to reflect sdb verses sda like conky entries etc..
For me it's just my conky.confg

After doing this a few times i wrote a script to automate it, first copying
my fstab and mtab and my conky.conf from sdb3 to safe place, then deleting
everything in sdb1 and adb3, then coping everything same as above, then 
copying back the fstab and mtab and my conky.conf files so i dont
have to edit them agin. Anyway you get the idea, i hope. I not very good
with english and sometimes explain this badly. I know this might be
old fashioned way of cloning, but totally works great for me. I love
having a back up install just incase. I use to do this to a external usb
drive every so often and then set it aside for emergency in case I
totally goober up my main install, which I am professional at really
goobering up sometimes :P

Edit.. oops.. I totally forgot.
You need to install grub to mbr of you cloned disk if that where you clonning to, but depending on your set up. For me it's the mbr and I also add entries for grub in my cloned install to boot both sda and or sdb so im all set to boot my backup disk directly without need of sda disk. Hope that make sense.

---

