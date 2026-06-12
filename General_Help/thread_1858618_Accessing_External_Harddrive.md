---
title: "Accessing External Harddrive"
date: 2011-10-12
forum: General Help
---

### Post by mbhammerbro on 2011-10-12
[SIZE=3][FONT=Calibri]Hey guys,[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I am[/FONT][/SIZE][SIZE=2][FONT=Verdana] currently running Ubuntu 11.04 and I am having a little trouble editing a config file. What I am trying to do is edit the gnump3d config file so that I can set my root folder to be my external harddrive. I can cd into the harddrive using [/FONT]```
cd /media/GoFlex\ Media\ Disk/
``` but when i set the config file line to [HTML]root = /media/GoFlex\ Media\ Disk/[/HTML] it says it is an invalid file path. I know there is another way to refer to my external harddrive, but I'm not sure of how to do it.[/SIZE]

---

### Post by collisionystm on 2011-10-12
> **mbhammerbro said:**
> [SIZE=3][FONT=Calibri]Hey guys,[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I am[/FONT][/SIZE][SIZE=2][FONT=Verdana] currently running Ubuntu 11.04 and I am having a little trouble editing a config file. What I am trying to do is edit the gnump3d config file so that I can set my root folder to be my external harddrive. I can cd into the harddrive using [/FONT]```
cd /media/GoFlex\ Media\ Disk/
``` but when i set the config file line to [HTML]root = /media/GoFlex\ Media\ Disk/[/HTML] it says it is an invalid file path. I know there is another way to refer to my external harddrive, but I'm not sure of how to do it.[/SIZE]


Try to change it in your /etc/passwd and reboot.

sudo nano /etc/passwd

This is the first line
```
root:x:0:0:root:/root:/bin/bash
```Change to this
```
root:x:0:0:root:/media/GoFlex\ Media\ Disk/:/bin/bash
```reboot

---

### Post by papibe on 2011-10-12
```
root = "/media/GoFlex Media Disk/"
```
I got the idea from [here]("http://www.mail-archive.com/gnump3d-users@gnu.org/msg00693.html").

Tell us how it goes,
Regards.

---

### Post by papibe on 2011-10-12
@collisionystm, I think he's referring to the GNUMP3d [configuration]("http://www.gnu.org/s/gnump3d/config.html#Config") file, which is either the file /etc/gnump3d/gnump3d.conf" or "~/.gnump3drc".

Regards.

---

### Post by mbhammerbro on 2011-10-12
> **papibe said:**
> ```
root = "/media/GoFlex Media Disk/"
```
I got the idea from [here]("http://www.mail-archive.com/gnump3d-users@gnu.org/msg00693.html").
 
Tell us how it goes,
Regards.
 
 
No good, didn't work.

---

### Post by cryptotheslow on 2011-10-12
Can you be clear as to whether you are trying to make the external drive the root filesystem of your system as a whole, or the "root" (or top level) directory for the Gnump3D application please?

People may interpret your original request incorrectly and give you advice that will royally hose your system.

---

### Post by mbhammerbro on 2011-10-12
> **cryptotheslow said:**
> Can you be clear as to whether you are trying to make the external drive the root filesystem of your system as a whole, or the "root" (or top level) directory for the Gnump3D application please?
 
People may interpret your original request incorrectly and give you advice that will royally hose your system.
 
Oh, ok.  I am trying to make my external the top directory of of gnump3d.

---

### Post by cryptotheslow on 2011-10-12
I'm not familiar with gnump3d but papibe's advice sounds sane.

Can you post up the contents of the conf file here between code tags?

Also the output of these two commands issued in a Terminal window:

```
ls -l /media
```
```
ls -l /mnt
```

That is a lowercase letter L as an option.

---

### Post by mbhammerbro on 2011-10-12
> **cryptotheslow said:**
> I'm not familiar with gnump3d but papibe's advice sounds sane.
 
Can you post up the contents of the conf file here between code tags?
 
Also the output of these two commands issued in a Terminal window:
 
```
ls -l /media
```
```
ls -l /mnt
```
 
That is a lowercase letter L as an option.
 
Honestly this is the best i can do for now because I am using RDP through my android phone because I'm at work.
 
Contents of config file: 
```

.
.
root = /media/FreeAgent\ GoFlex\ Drive/
.
.

```
 
```

justin@Media-PC:~$ sudo ls -l /media
total 8
drwx------ 1 justin justin 8192 2011-09-11 15:24 FreeAgent GoFlex Drive

```
 
```

justin@Media-PC:~$ sudo ls -l /mnt
total 0

```
 
By the way, I can access my drive through a cd command, I just can't set that as the directory in the config file.

---

### Post by cryptotheslow on 2011-10-12
It's really going to be down to how gnump3d parses its conf file.

As papibe's suggestion did not work you could try:

```
root = "/media/FreeAgent\ GoFlex\ Drive/"
```

or

```
root = "/media/FreeAgent\ GoFlex\ Drive"
```

You may want to consider re-labelling the partition on the external drive to something without spaces in it, then you wouldn't have to worry about escaping the spaces. Just one idea to reduce the variables involved :)

Before doing so, be mindful of whether the current mount point is referenced anywhere else (other apps, /etc/fstab and so on). You'll likely need to unmount the partition before relabelling it - or at least re-mount it after changing it to get the mount point to update.

---

### Post by collisionystm on 2011-10-12
Do you know the easiest way to figure out how to do your / 's in a spaced file name??

Open Terminal...

cd /media

cd Free*TAB*

Where I put TAB, hit the tab key. It will auto complete for you and VOILA! Give you the proper file name with the / 's in place. Just copy and paste that.

---

### Post by mbhammerbro on 2011-10-12
> **cryptotheslow said:**
> It's really going to be down to how gnump3d parses its conf file.
 
As papibe's suggestion did not work you could try:
 
```
root = "/media/FreeAgent\ GoFlex\ Drive/"
```
 
or
 
```
root = "/media/FreeAgent\ GoFlex\ Drive"
```
 
You may want to consider re-labelling the partition on the external drive to something without spaces in it, then you wouldn't have to worry about escaping the spaces. Just one idea to reduce the variables involved :)
 
Before doing so, be mindful of whether the current mount point is referenced anywhere else (other apps, /etc/fstab and so on). You'll likely need to unmount the partition before relabelling it - or at least re-mount it after changing it to get the mount point to update.
 
 
Neither of those worked.  What's the best way for me to un-mount, rename, and then re-mount?

---

### Post by cryptotheslow on 2011-10-12
You are restarting gnump3d after making each of these changes to test them out right? It is unlikely to pick up a conf file change without a restart.

"Best" way to unmount / relabel / re-mount is debatable until the cows come home, there are many ways to achieve it, none "better" than any other. It's just a matter of preference.

Personally (on 10.04) I would use GParted. Use the drop-down up top to select the external drive, right click on the partition and select "Unmount", right-click again and select "Label" - change as required, commit the change using the button on the toolbar, then right-click again and select "Mount".

But bear in mind my earlier comment about thinking about where the current label maybe referenced (sorry for labouring that point if it is obvoius to you!).

---

### Post by mbhammerbro on 2011-10-12
> **cryptotheslow said:**
> You are restarting gnump3d after making each of these changes to test them out right? It is unlikely to pick up a conf file change without a restart.
 
"Best" way to unmount / relabel / re-mount is debatable until the cows come home, there are many ways to achieve it, none "better" than any other. It's just a matter of preference.
 
Personally (on 10.04) I would use GParted. Use the drop-down up top to select the external drive, right click on the partition and select "Unmount", right-click again and select "Label" - change as required, commit the change using the button on the toolbar, then right-click again and select "Mount".
 
But bear in mind my earlier comment about thinking about where the current label maybe referenced (sorry for labouring that point if it is obvoius to you!).
 
Thanks I'll try this when I get home.  I would be restarting but I don't even currently have it running because I keep getting an error on that line of the config.

---

### Post by cryptotheslow on 2011-10-12
Ahh fair point if it refuses to start up at all :D

And yes - probably best to wait until you are physically with the machine before venturing into relabelling partitions.... or any other partition related shenanigans for that matter. Such activities over a remote link of any kind, without being >1200% sure you know what to do, is only ever going to go one way......... badly.

I'm sure you'll survive your shift without your music :D

---

### Post by mbhammerbro on 2011-10-13
> **cryptotheslow said:**
> Ahh fair point if it refuses to start up at all :D

And yes - probably best to wait until you are physically with the machine before venturing into relabelling partitions.... or any other partition related shenanigans for that matter. Such activities over a remote link of any kind, without being >1200% sure you know what to do, is only ever going to go one way......... badly.

I'm sure you'll survive your shift without your music :D

Awesome it works.  I had to use ```
sudo umount /dev/sdb1
``` to unmount though.  But thanks a lot for all of the help.

---

