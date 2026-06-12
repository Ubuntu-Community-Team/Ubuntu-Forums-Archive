---
title: "After upgrade my system will no longer boot, Please Help !"
date: 2009-11-06
forum: General Help
---

### Post by zonemikel on 2009-11-06
I had did "sudo apt-get upgrade" a few days ago and i just recently got to restart my computer. After I did I get 

grub error 22 

So i go and try and reinstall grub, it gives me this 

/dev/sdb does not have any corresponding BIOS drive

i tried entering grub and using root (hd1,0) then setup(hd1) or setup (hd1,0) they both give me 

error 17 unable to mount 

I install a totally different hard disk and restore from a backup I had from a few days ago using the install cd and dd. When i try and mount the partition i get 

mount: unknown filsystem type "LVM2_member" 

however using the server ed cd i can mount it and see my files .... but i still get grub error 22 when i boot and i still get the same errors when i try and install grub on the disk .... 

any idea what i should do ? Its a server with weeks of work on it i really cant afford to loose it.

for example i just booted with the server ed and went into "rescue a broken system" I got a prompt by executing a shell in /dev/GalacticAC/root ... but if i try and choose /dev/sda2 as a root file system it will tell me "mount failed while mounting the device you entered for your root file system /dev/sda2 on /target"

GalacticAC was the name of the server btw. 

so executing a shell in /dev/GalacticAC/root as the root file system i can see all my files but if i try 

grub-install /dev/sda1

i get 

/dev/GalacticAC/ does not have any corresponding BIOS drive 

That is the same problem i've been getting from the get go ... i cant do anything if i cant install grub so it will boot the damn hard disk 

I can see that the files are there and intact why cant i install grub ?

trying grub-install --recheck /dev/sda gives me the same "bios drive" error

if i try to go into grub and do this  i get 
grub> root (hd0)
grub> setup(hd0)
ERROR 17: cannot mount selected partition

its already mounted, why cant grub do it ? 

I edited /boot/grub/device.map and it looks like this (i think)
hd0 /dev/sda

I have to type all this because the system i'm working on does not have inet

---

### Post by zonemikel on 2009-11-06
after 30 minutes views 1 ??? please i've been messing with this all f'ing day

going into grub and typing 

find /boot/grub/stage1 gives 
file not found 

however i can navigate and see that file in /boot/grub/ wth ?

---

