---
title: "remastersys iso too large"
date: 2010-04-14
forum: General Help
---

### Post by Rocket J Squirrel on 2010-04-14
I'm getting ready to change my wubi/Windows 7 dual boot laptop to a full  Ubuntu machine. To prepare, I want to back up Ubuntu because I have  made a number of changes and patches to get 9.10 to properly talk to the  wireless card, handle Windows shares reliably, etc. 

I'm using  remastersys with with the full backup option to hopefully make a full  backup to a USB flash drive because I have some  personal stuff in Home that I hope to keep.

I unmounted shares  and shut down other windows in the duration, but at the end of a long,  long backup process, remastersys is telling me that the backup file  exceeds the max ISO size. remastersys reports the Filesystem size at 64  Mbytes. 

I could exclude the Home folder and subdirectories, but  according to the disk usage analyzer, they aren't using any real space  at all. Please see attached screenshot (is there a way to put a  thumbnail of the shot in this post?).

I've emptied the trash. 

So  -- what am I not doing right here?

Also, does anyone know how to  terminate a remastersys backup that is in process without leaving a  bunch of large files in the remastersys folder and subdirectories? I  found the only way to clean up the shrapnel is to completely uninstall  remastersys and then re-install it. 

Thanks for any help.

---

### Post by Rocket J Squirrel on 2010-04-14
Oh -- I see the forum put a thumbnail on the post.

---

### Post by mike555 on 2010-04-14
Only time I had the "too big" problem was when I had a bunch of pictures and movies in my home folder.......... if that is your problem just put the images, movies, iso's etc. on a thumbdrive and delete the ones in your home ... empty trash , empty root trash , and try again .........

---

### Post by colorlessprism on 2010-04-14
im curious as to your "/host" folder did you use wubi?. typically the windows partition where you installed Wubi is available as /host within Ubuntu. i would try adding "/host" to your exception list in remastersys and see if that doesn't fix you issue.

as far as the shrapnel goes i dont know what to do to fix other than not interrupting remastersys. when remastersys finishes and your done with the iso open a terminal and type "sudo remastersys clean"

---

### Post by Rocket J Squirrel on 2010-04-14
Thanks, folk!

_Mike555_: Good advice! This is a fairly young install of Ubuntu so I don't have any large media files or stuff like that. As the Disk Usage thingy shows, the stuff in my Home folder is 0.6% of the overall.

_colorlessprism_: Hmm, yes, it was wubi (first line in my OP, learned my lesson in another thread). I will add /host to the exclusion list and have another go at it. 

I asked about cleaning up remastersys shrapnel on their forum and fragedelic, the author, provided this information, for anyone who is seeking help on this and stumbles across this thread:
[INDENT]Quit the gui normally and close the terminal window the remastersys  process has opened.  Then do the following from another terminal window:
[/INDENT]```
sudo  killall -KILL mksquashfs
sudo killall -KILL remastersys
sudo  remastersys clean
```[INDENT]That should clean things up for you.
[/INDENT]

---

### Post by Rocket J Squirrel on 2010-04-14
Hey, colorlessprism: excluding /host seems to have done the trick. I guess it makes sense that the author of remastersys would not have addressed the wubi situation, as it's a sorta-kinda trainer wheels ubuntu. 

So  . . . now I got five files: 

custom.iso
custom.iso.md5
dummysys
ISOTMP
remastersys.log

I want to put them on a flash stick and boot off it. Just copy them to the stick and figure out how to make it bootable? Use UNetbootin? 

(The long term goal here is to strip Windows off the machine and go big-boy Unbuntu).

---

### Post by colorlessprism on 2010-04-14
you should be able to use "USB startup Disc Creator" (i think its installed by default, but if not you should be able to get it in the repo's) and convert your ISO (typically the only file created you'll need unless you start distributing your creation) to a usb drive. you should also have the ability to make a persistence file (files downloaded and changes made will stick) up to 4GB in size. one thing to consider though is booting from flash drive is SLOW compared to traditional means. the larger the persistence file the slower your install will boot. i have found that 512MB to 1GB good enough to make changes to the flash drive. thanks for the remastersys cleaning options, i have noted them in my CodeBook

---

### Post by bemental on 2010-10-18
> **Rocket J Squirrel said:**
> Hey, colorlessprism: excluding /host seems to have done the trick. I guess it makes sense that the author of remastersys would not have addressed the wubi situation, as it's a sorta-kinda trainer wheels ubuntu. 

So  . . . now I got five files: 

custom.iso
custom.iso.md5
dummysys
ISOTMP
remastersys.log

I want to put them on a flash stick and boot off it. Just copy them to the stick and figure out how to make it bootable? Use UNetbootin? 

(The long term goal here is to strip Windows off the machine and go big-boy Unbuntu).

I'm going to give this a try as well and let everyone know how it turns out.  While I don't necessarily need to have my setup backed up, the computer I have install WUBI onto is going to be "re-imaged" this week.

---

### Post by bemental on 2010-10-18
I don't think I've ever been able to boot from USB from a remastersys backup iso.

I'll have to try burning it to a CD instead, although it IS curious...

---

### Post by PRC09 on 2010-10-18
I  created a remastersys backup iso yesterday and used the Startuo Disk Creator in 10.10 and it worked fine....I just used the iso file tho and not the others in the folder....

---

