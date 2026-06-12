---
title: "Strange behaviour by ubuntu 9.10"
date: 2010-03-28
forum: General Help
---

### Post by abhishek bansal on 2010-03-28
hi all,
recently i was trying to mount my partition automatically at start
up ...so i gone through some tutorials on the net nd made some changes
in /etc/fstab file (i made a back up before making any changes). when
i was changing permissions of folder in which i tried to mount my all
partitions i got my system screwed up.then it was showing following error at start up
and GUI was not turning up.
"could not update ICEauthority file "
also my sudo was not working so first i restored original fstab file
through recovery console then i googled out about above errors. I
found some solution now my system is working but showing strange
behaviour like:

> ubuntu is not detecting any of my hdd partition
> disk utility is not working (showing no error)
>fdisk -l shows nothing
> no new software is getting installed via ubuntu software center (shows no error when clicking on install but nothing turns up)
>i cannot restart or shutdown my system from GNOME it only logs off my session (although through terminal its working)
>no media player showing sound controls enabled
>gnome not showing ethernet or sound volume icon in upper panel (although net is working)
>users and groups from system->administration menu is not working (error:cannot load configuration)

i think most of the administrative tasks are not working.........i googled out but found nothing satisfactory.....if nybody hav ny clue plz help...i dont want to reinstall it, coz i m not very experienced with linux n it took about a whole month to customize my ubuntu 9.10 on my college internet...
thanx in advance.

---

### Post by Ozymandias_117 on 2010-03-28
> **abhishek bansal said:**
> **1**when i was changing permissions of folder in which i tried to mount my all partitions i got my system screwed up.**2**then it was showing following error at start up
and GUI was not turning up.
"could not update ICEauthority file "

> ubuntu is not detecting any of my hdd partition
> disk utility is not working (showing no error)
>fdisk -l shows nothing
> no new software is getting installed via ubuntu software center (shows no error when clicking on install but nothing turns up)
>i cannot restart or shutdown my system from GNOME it only logs off my session (although through terminal its working)
>no media player showing sound controls enabled
>gnome not showing ethernet or sound volume icon in upper panel (although net is working)
>users and groups from system->administration menu is not working (error:cannot load configuration)

i think most of the administrative tasks are not working.........i googled out but found nothing satisfactory.....if nybody hav ny clue plz help...i dont want to reinstall it, coz i m not very experienced with linux n it took about a whole month to customize my ubuntu 9.10 on my college internet...
thanx in advance.

1. What folders were you messing with the permissions to?

2. ```
sudo rm ~/.ICEauthority
``` should fix that, but, you say sudo doesn't work... so you could try a live disk, or wait until other things are fixed, all that does (As far as I know) is hold records of X session starts, so it shouldn't be causing any problems.

3. All the rest of your problems sounds like there are issues with /sbin and /usr/sbin hopefully it's just a permission issue and can be resolved...

---

### Post by steve_steve on 2010-03-28
I'm a noob too.  When a similar thing happened here, I rebooted, selected 'recovery mode' & went thru 'try to make free space' and 'repair broken packages' and it got fixed.

---

### Post by abhishek bansal on 2010-03-28
> **Ozymandias_117 said:**
> 1. What folders were you messing with the permissions to?
i made a folder named "drives" in /media and i was trying take its permissions by 
chown -R abhishek:abhishek /media/drives
> **Ozymandias_117 said:**
> 
2. ```
sudo rm ~/.ICEauthority
``` should fix that, but, you say sudo doesn't work... 

now my sudo is working.....(after changing the permissions of /etc/sudoers)
but this code not worked i m in same condition as before...
> **Ozymandias_117 said:**
> 
so you could try a live disk, or wait until other things are fixed, all that does (As far as I know) is hold records of X session starts, so it shouldn't be causing any problems.


3. All the rest of your problems sounds like there are issues with /sbin and /usr/sbin hopefully it's just a permission issue and can be resolved...


how to resolve them...??

---

### Post by abhishek bansal on 2010-03-28
> **steve_steve said:**
> I'm a noob too.  When a similar thing happened here, I rebooted, selected 'recovery mode' & went thru 'try to make free space' and 'repair broken packages' and it got fixed.

how can i repair broken packages ??

---

### Post by steve_steve on 2010-03-28
It's an option that comes up when you start in recovery mode.

---

### Post by abhishek bansal on 2010-03-28
> **steve_steve said:**
> It's an option that comes up when you start in recovery mode.

I m sorry but i connect internet through a proxy so i cannot download those packeges in recovery mode without ny proxy settings...

---

