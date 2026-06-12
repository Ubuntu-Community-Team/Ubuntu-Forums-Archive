---
title: "wipe an external hard drive"
date: 2009-09-20
forum: General Help
---

### Post by CarlC4 on 2009-09-20
i need to wipe an external hard drive with ubuntu installed on it, it can connect through esata and usb. I want it completely wiped so it's like brand new.

---

### Post by Yvan300 on 2009-09-20
Go to system->administrator->synaptics and search and install gnome partition editor and you can use that to format your external hd to the format of your choice.

---

### Post by wojox on 2009-09-20
Download and burn dban:

[http://www.dban.org/](http://www.dban.org/)

---

### Post by erilidon on 2009-09-20
I would have to agree with using dban as it will wipe the drive completely the gnome partition editor will just do a low level format.

---

### Post by jonallport on 2009-09-20
Use dd, assuming the hdd is sdX (i.e. partitions sdX1, sdX2, etc.):

dd if=/dev/zero of=/dev/sdX 

Overwrites each block with zeros, also known as 'low-level format'.

For a more secure 'wipe' try:

dd if=/dev/urandom of=/dev/sdX

Will do the same with pseudo-random data instead of zeros. DON'T use /dev/random unless you have several days to wait.  Why not try the random overwrite a few times if you're really paranoid?

---

### Post by coffeecat on 2009-09-20
If you have a need to completely wipe the data such that it can't be recovered, rather than do a simple format, you don't have to download dban (useful though that is). You can use the 'shred' command from the terminal. You can use shred to wipe partitions or whole drives - not just files. See 'man shred' for more details. Just one hint: the default number of passes is 25, which is absurd overkill. Use the -n flag to specify a sane number of passes.

---

### Post by CarlC4 on 2009-09-20
thanks for the ides every one, i was messing with it and now i can't connect to the hard drive

---

### Post by CarlC4 on 2009-09-20
oh, and i can't boot off it, so can i do these things while it's connected by usb or esata?

i'm using a laptop that has vista dual booted with ubuntu 9.04, if that helps at all.

---

### Post by erilidon on 2009-09-20
I would still use dban to wipe the hard drive and I wouldn't recommend using anything less than a DOD 3 pass wipe. Then I would install gnome partition editor as [Yvan300]("http://ubuntuforums.org/member.php?u=780232") suggested you can reformat the drive with that program to ext, fat, ntfs, whatever. and then should be able to see it again.

---

### Post by CarlC4 on 2009-09-21
it sounds like the best idea, but i have no disks and i don't want to go out and buy some. is there something that will wipe it while my comp is on, AND MORE IMPORTANTLY how can i get the computer to recognize it

---

### Post by erilidon on 2009-09-21
If you dont want to make a disk of dban then I would do as [jonallport]("http://ubuntuforums.org/member.php?u=274630") said 

"For a more secure 'wipe' try:

dd if=/dev/urandom of=/dev/sdX"

(though I am not sure if this works as I have never done it) then used partition editor to format the drive back to fat, ntfs, ext or whatever, so you can see it again

---

### Post by CarlC4 on 2009-09-21
how do i do that.
do i just plug the hard drive through usb and run it in terminal?

---

### Post by Whiffle on 2009-09-21
I'm curious, are you trying to wipe it so the data can't be read ever ever again, or wipe it just so you can use it?  

If its the latter, then you can just install gparted (shows up under System > Administration > Partition Manager), plug in your drive, select it in the drop down at the top right corner, delete the partitions, make a new one, and format it.

If its the former, then ignore this post :)

---

### Post by CarlC4 on 2009-09-21
it is the later thank you i'll try it now

---

### Post by CarlC4 on 2009-09-21
uh it's not working, it's not letting me delete

---

### Post by erilidon on 2009-09-21
> **CarlC4 said:**
> uh it's not working, it's not letting me delete

what exactly does it says when its not letting you?

---

### Post by CarlC4 on 2009-09-22
ok here is the current problem, ubuntu is not recognizing the hard drive

---

### Post by erilidon on 2009-09-22
okay, could you be a little more descriptive?

The only quick thing I can think of off the top of my head is maybe the harddrive is not formatted so therefore it wouldn't just pop up as a mounted drive on the desktop.

Do you have the Partition Editor installed? Does it see it in there?

---

### Post by CarlC4 on 2009-09-22
yeah nothing sees it, not the partition editor or anything

---

### Post by t0p on 2009-09-22
At the top of this thread you said you could connect to the drive by sata and usb.  So what have you done to the drive in the meantime?

---

### Post by CarlC4 on 2009-09-22
well i was able to connect, now it doesn't i tried just deleting the data, bad move huh?

---

### Post by erilidon on 2009-09-23
you can try this:
[http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux](http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux)

---

### Post by Whiffle on 2009-09-23
> **CarlC4 said:**
> well i was able to connect, now it doesn't i tried just deleting the data, bad move huh?


Unplug it from the usb, and plug it back in.  Now open up a terminal (Applications > Accessories > Terminal), and run

```

dmesg

```

Post up the last 15-20 lines or so, there should be something in there about it.  (ctrl + shift + c to copy out of the terminal).

---

### Post by x C0MMAND0 x on 2009-09-23
Would you be able to boot to DBAN in a virtual machine and then have it detect the external hard drive from there?  That way, you don't have to use a CD to burn it...

---

### Post by Yvan300 on 2009-09-23
Most programs like partition manager require you to restart your pc because the disk that you are gonna format( most of the times is your internal hard drive) is in use. But when it comes to the external hard drive then when it is unmounted it is no longer in use. So if the same principles apply then you could just mount the iso of the program that you want to use and format your drive, or you could also boot from a virtual machine if you have enough ram.

---

