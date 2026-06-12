---
title: "Hide specific mounted drives from Desktop"
date: 2011-03-06
forum: General Help
---

### Post by braikar on 2011-03-06
Hi,
I just installed Lucid Ubuntu/Gnome (10.04) and I'm having troubles figuring out how to hide some specific drives from the Desktop.
I know of the option to hide all mounted drives, but that's not what I want, I still want USB keys, CDs etc. to show up on the Desktop.

I've checked many threads but they are really old, for example in:
[http://ubuntuforums.org/showthread.php?t=792651](http://ubuntuforums.org/showthread.php?t=792651)

it says to mount the drives anywhere but /media and they won't show on the desktop, but it's not true here, since i mounted mines in ~/Music, ~/Documents, ~/Videos etc. and they still show up on the desktop.

There are also explanations to use HAL to ignore the devices, I haven't tried those, since I know that now HAL is now obsolete.

Can anyone point me to a thread with the answer? or is there an answer? I couldn't find one except in posts from 2008 or earlier which are not relevant anymore.

That's my /etc/fstab file:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc                    proc  nodev,noexec,nosuid  0  0  
/dev/sdb1  /                        ext4  errors=remount-ro    0  1  
/dev/sda1  /home/braikar/Personals  ext3  defaults             0  0 
/dev/sda2  /home/braikar/Music      ext3  defaults             0  0  
/dev/sda3  /home/braikar/Videos     ext3  defaults             0  0  
/dev/sda4  /home/braikar/Software   ext3  defaults             0  0  
/dev/sdb5  /home/braikar/Documents  ext4  defaults             0  0  

```

And I get all these drives on the Desktop (Personals, Music, Videos, Software, Documents)... Is there a tweak to get the desktop to hide specific icons by checking their name or something like that?

---

### Post by mcduck on 2011-03-06
The point about mounting the drives anywhere else than in /media is just as relevant now as it was before.

Just keep in mind that you have to delete the old mount points from inside /media as well.

If the drives still appear on desktop after that your fstab configuration must be wrong and the drives are getting automounted instead of being mounted using fstab. Also you might want to use UUID's instead of device names in fstab, that allows the system to detect actual partitions instead of having to rely on the device names which can change on some situations, at least on some systems.

---

### Post by Morbius1 on 2011-03-06
A mount point in your /home/x folder or in /media will produce a mount icon on the desktop. You can remove all mount icons by going to gconf-editor:

/apps/nautilus/desktop/volumes_visible

and remove the check.

The only problem is that when you plug in a USB stick or access a remote share on the network it won't show an icon either.

---

### Post by Cavsfan on 2011-03-06
I was wondering this same thing myself. I know I have gotten my USB drive icon off of my desktop in a previous version of Ubuntu.
I think it was a right click on desktop option but, I cannot remember. I have slept since then...

My fstab file only shows my ext4 and swap drives, yet my USB drive icon shows on my desktop.
The only way I have been successful in getting it not to display is to unmount it, but I don't really want to do that.

Is the gconf-editor option the only way?
Thanks :D

---

### Post by braikar on 2011-03-07
> **Morbius1 said:**
> A mount point in your /home/x folder or in /media will produce a mount icon on the desktop.

That's what I needed to know :) so no way to hide these drives if I mount them in home :(
So there is no way to hide specific drives, it should be an option..

Thanks for the help :)

---

### Post by wiggly81 on 2011-03-07
its actually easyer then you think...

press Alt+F2 and type 
```
gconf-editor
```
hit run

browse to "apps > nautilus > desktop" uncheck "volumes_visible"

the icons will not show on desktop anymore

---

### Post by mcduck on 2011-03-07
> **wiggly81 said:**
> its actually easyer then you think...

press Alt+F2 and type 
```
gconf-editor
```
hit run

browse to "apps > nautilus > desktop" uncheck "volumes_visible"

the icons will not show on desktop anymore

No, it's not that easy. If you read the first post, the OP wants to keep all removable drives on the desktop, and only remove a specific drive.

That gconf option would remove *all* drives from desktop.

---

### Post by mcduck on 2011-03-07
> **braikar said:**
> That's what I needed to know :) so no way to hide these drives if I mount them in home :(
So there is no way to hide specific drives, it should be an option..

Thanks for the help :)

I wan't aware of the drives mounted inside /home appearing on the desktop this way, but if they really do it's still not a problem...

Just mount your drives elsewhere, like inside /mnt, and then *link* them into your home. (actually that's exactly what I'm doing with my internal drives to have them accessible in my home directory while keeping them from appearing on the desktop)

---

### Post by Morbius1 on 2011-03-07
Another method you might want to explore is to use "bind" in an upstart job:
From your earlier post as an example:
> /dev/sda2  /home/braikar/Music      ext3  defaults             0  0  
/dev/sda3  /home/braikar/Videos     ext3  defaults             0  0  
Change those mount points to /mnt - that will get them off the desktop:
> /dev/sda2  /mnt/Music      ext3  defaults             0  0  
 /dev/sda3  /mnt/Videos     ext3  defaults             0  0  
 (1) Create an upstart job named "bind-mount.conf"
```
gksu gedit /etc/init/bind-mount.conf
```(2) The content of that file would look something like this:
> # Remount partitions with bind
#
description "Bind Partitions to Home Directory"

start on stopped mountall

script
  mount --bind  /mnt/Music /home/braikar/Music
  mount --bind  /mnt/Videos /home/braikar/Videos
end script
The advantage - well, the advantage for someone like me - is that all of the linkages from and to partitions or directories are in one place that I can keep track of when I find that I don't remember what I've linked to what :wink:

I should also note that back in the good old days you were able to use bind in fstab where it would be easier to set up and more coherent. But mountall and upstart discombobulated how and when fstab runs so that is no longer a safe method. The upstart job above waits for mountall to finish before it executes the script.

Just something to consider.

---

### Post by braikar on 2011-03-07
Oh stupid me!! 8-[

Thanks for the answers mcduck and Morbius! I was so focussed on mounting the drives I had completely omitted that I could use 'ln' or 'bind' and mount the drive somewhere else and just create a shortcut!

Cheers :D

---

### Post by Digital_Man on 2011-03-18
Many thanks! I came to the Forum seeking a solution for this specific issue, and Morbius1 has provided it. It works perfectly - thank you!

---

