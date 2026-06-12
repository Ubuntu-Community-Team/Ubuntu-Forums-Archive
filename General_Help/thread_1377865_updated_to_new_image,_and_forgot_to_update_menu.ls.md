---
title: "updated to new image, and forgot to update menu.lst can't boot!"
date: 2010-01-10
forum: General Help
---

### Post by mr clark25 on 2010-01-10
i know i have been having a lot of problems, but i keep having more :(

this time, i ran update manager, and noticed that i was getting a new image, but i quickly forgot this. then, while installling the updates, it asked me if i wanted to keep my old menu.lst. i told it to keep my old one, since it worked fine. it then told me that i needed to restart, so i did. it got to where it would normally start loading grub, but my computer wouldn't go any farther. (would not load grub) i would think that it would still load my old image.

i am writing this while running a liveUSB.

i ran the boot info script, and attached its output.

i know this should be posted under installation&upgrades, but general help seems to be much more active.

because of this, my father doesn't want me updating any more...

---

### Post by mr clark25 on 2010-01-10
i see 23 views, and surely someone knows the answer to this?

i guess that maybe that person i am waiting for isn't logged in right now...

---

### Post by vinnywright on 2010-01-10
did you used to get you'r grub screen whar you see the kernels and sutch or did it just strate boot ?

if you keep hiting esc wile booting do you get the grub screen?

if yes try to boot to a terminal log in and run sudo update-grub and reboot.

if no post you'r menu.lst and the content's of /boot

VINNY

---

### Post by drs305 on 2010-01-10
Is your BIOS booting to the grub drive first (sda)?

Can you get to the menu by pressing ESC during boot?

I see from the RESULTS.txt you have both a menu.lst and a grub.cfg file. Before the failure, were you seeing both the Grub legacy and Grub 2 options on the menu (i.e. had you done an online upgrade to Karmic but still retained Grub legacy)? 

If you can get to the Grub menu, you could try highlighting the first entry, pressing "e" to get into the edit mode. Remove the "uuid" line entirely by holding down the delete key and on the "kernel" line change the "root=UUID=...." to "root=/dev/sda1" and try booting with those temporary changes.  The UUIDs appear to be correct but I'd try it this way regardless.

---

### Post by mr clark25 on 2010-01-10
thanks for the replies! sorry i couldn't get back earlier.

1. i cannot get to the screen where i select a kernel

2. havent tried the esc key, will do so now.

3. i chrooted into my system and ran update-grub from my liveusb. it fornd my kernals and put them in menu.lst, and it completed with success.

4. yes, my bios is booting to my first drive (sda5) (or trying to)

5. there is no option to press the esc key, but i will try to now, because i have heard that it can be hidden.

6. i created a grub.cfg and pasted my menu.lst into it. i thought that maybe that would fix it, but it didnt. 

7. i think i have grub legacy. i dont know for sure, though. it must be grub legacy, because i previosly had no grub.cfb file.

---

### Post by mr clark25 on 2010-01-10
when i press the esc key, my system starts beeping at me. i dont know what that means, so i stopped pressing the key.

---

### Post by drs305 on 2010-01-10
If you are using Grub (legacy) if it is set up to boot automatically hitting ESC causes the menu to appear. You would press it every second or so after you here your system beep at startup (POST).  In Grub 2, you hold down the shift key to view the menu if it isn't showing up.

One thing you want to do is go back to the LiveCD, mount /dev/sda5 and remove or rename that /boot/grub/grub.cfg file. If you are using Grub it may confuse things, and if you are using G2 (you shouldn't be according to RESULTS.txt) it wouldn't work anyway.

---

### Post by mr clark25 on 2010-01-10
ill try it again, but i dont think a menu will appear.

i took your advice and renamed the grub.cfg file.

now, where do i go from here? maybe it would be better if i just updated to grub2.

i could chroot into my system, and run the command to update to grub2. does anyone recommend this? should i re-install grub legacy first?

---

### Post by mr clark25 on 2010-01-10
this is how i chrooted into my system nad ran update-grub: (minus the $)

> **Leppie said:**
> 
```

$sudo bash
$mkdir -p /mnt/temp/boot
$mount /dev/sda5 /mnt/temp/
$mount -o bind /proc /mnt/temp/proc
$mount -o bind /dev /mnt/temp/dev
$mount -o bind /dev/pts /mnt/temp/dev/pts
$mount -o bind /sys /mnt/temp/sys
$chroot /mnt/temp
$grub-install --recheck /dev/sda
$update-grub
$exit
```

i ran all of these. i think "grub-install --recheck /dev/sda" re-installs grub legacy and checks to make sure everything is installed correctly. correct me if i am wrong.

---

### Post by mr clark25 on 2010-01-10
i have a spare 100gb partition on my hard drive. maybe it would be better just to take 10gb of it and install another instalation of ubuntu on it, just for the grub2.

or is there a better solution?

---

### Post by mr clark25 on 2010-01-11
does anyone think that that would be a good idea?

---

### Post by drs305 on 2010-01-11
> **mr clark25 said:**
> does anyone think that that would be a good idea?

It's an easy way to get things sorted. When you get near the end of the install setup just check the 'Advanced' button to make sure you have Grub 2 doing what you want.

If your system now boots to a normal Ubuntu desktop (I can't tell from the last few posts), the other option is just to try to install Grub 2 (grub-pc) and hope for the best. ;-)

---

### Post by mr clark25 on 2010-01-11
there are going to be a lot of posts like this...

all i did was run the update manager, and then my computer wouldnt turn back on...
does anyone know the command that updates from grub legacy to grub2? or to remove grub and then install grub2 from scratch?


someone REALLY need to make a sticky how-to on fixing this.

---

### Post by sdowney717 on 2010-01-11
for grub2, try
sudo apt-get install grub-pc

---

### Post by Leppie on 2010-01-11
> **mr clark25 said:**
> does anyone know the command that updates from grub legacy to grub2? or to remove grub and then install grub2 from scratch?
remove grub legacy:
```
sudo apt-get purge grub
```
install grub2:
```
sudo apt-get install grub-pc grub-common
```

---

### Post by mr clark25 on 2010-01-11
but, will those work when i chroot into my system?

---

### Post by sdowney717 on 2010-01-11
it should if your root.
I got this from another post on how to become root of the os from a live CD

From the Live Desktop run:

Code:

sudo mount /dev/sdXY /mnt

(of course XY must represent your drive and partition #'s!)

Then:

Code:

sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

You should notice that the command prompt changes from ubuntu@ubuntu$ to # which means you're now root in that OS. I like to be sure I am where I want to be with "cat /etc/issue" and "df -H".

Then revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

And when you're done:

Code:

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt

---

### Post by mr clark25 on 2010-01-11
my computer finally works again!!! (uninstalled grub legacy, and installed grub2)

thanks so much for the help!


i think i had a mix of grub legacy and grub2, so i am amazed it even worked at all now that i look at it. i was able to hold shift to get to the menu, but i know i had grub legacy. there were many other things, too. im so glad it works again!

---

