---
title: "iPod mounting, etc."
date: 2006-05-25
forum: General Help
---

### Post by terragf on 2006-05-25
So, I've just started using Kubuntu a few days ago, and I've gotten a few programs up and running, but this gtkpod is stumping me.

Here's what I have:

I plug in the iPod, and it sort-of gets detected (in Konqueror, media:/, is displays the ipod) but I am cobut statesmpletely unable to mount it or view inside it, because an error states that: "mount: unknown filesystem type 'audo' "  (I thought it might be a typo at first, because I could not find any information at all on 'audo' filesystems, but apparently it isn't one)

So I can't seem to mount the device...also, there is nothing relating to ipod, or sda in my /dev folder.

gtkpod opens correctly, but states that "/mnt/ipod/iPod_Control/iTunes/iTunesDB" does not exist, and the import aborts.


I also followed the ubuntu wiki information as far as I was able to, but still no solution
also, I tried the ipodslave mentioned in these forums, but using the command
"sudo apt-get install ipodslave"  gives an error saying the ipodslave package doesn't exist - even after I installed the package

any help would be appreciated, please
thanks

---

### Post by mjunior on 2006-05-25
I have the same scenario...I installed the gtkpod and had the same reffered message you meant...

---

### Post by mjunior on 2006-05-25
I reached the IPod now...

try this:
follow this guide:
[http://www.ubuntuforums.org/showthread.php?t=134656&highlight=ipod](http://www.ubuntuforums.org/showthread.php?t=134656&highlight=ipod)

then open gtkpod
go to preferences
and type the /mnt/ipod on the mounting point field

connect your ipod
click on your ipod name on gtkpod left tab
File/add directory or file and have fun

Ps. the unmouting process and eject device is still a wonder...because the device is still displays a do not disconnect message

---

### Post by terragf on 2006-05-26
I've already done those things, thanks though...also, my iPod name isn't shown on the left, it just says iPod...

---

### Post by Patrick-Ruff on 2006-05-26
well, I'm sure theres some alternative programs you can use for such acts. perhaps emulating some windows programs for the iPod. but idk, I never really tried much of that

gl

---

### Post by mjunior on 2006-05-30
I downloaded the KDE packages and now I'm using amrok...it's working smootly then gtk though I coudn't delete the files (actualy the delete is performed normaly..but when I check for the volume space...it didn't change..so I gess the amrok is not removing the db entries and just the files it's selves)...

Give it a try and see if you can reach your IPod that way..

---

### Post by Video Toaster on 2006-05-30
Try installing the ipodslave package from the repositories.  Also, you must mount your iPod in KDE (maybe ipodslave will help with that) before using GTKPod (or at least I had to in Kubuntu...)  Once the iPod is mounted (mounts as /media/sda2 on my computer), change the mount path in GTKPod to wherever KDE mounted your iPod.

Worked well enough for me.  :)

---

