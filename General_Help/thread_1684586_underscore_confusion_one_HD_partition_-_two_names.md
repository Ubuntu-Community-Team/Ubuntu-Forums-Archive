---
title: "underscore confusion: one HD partition - two names?"
date: 2011-02-09
forum: General Help
---

### Post by mr.peeters@gmail.com on 2011-02-09
hi, 

it seems i'm having a problem with the name of one of my hard disk partitions.
this partition is formatted in NTFS since I'm still using win for some applications (another partition is ext4 for ubuntu system).
in ubuntu everything works fine - apart from the fact that there seems to be some confusion about the name of this partition.

I labeled the partition 'VILES' - so it's address should be /media/VILES - however, when I go have a look at file system/media there is two folders, one is called 'VILES' and the other 'VILES_' (including the underscore at the end.
'VILES' is empty and contents are 'unreadable' - 'VILES_' is the partition I'm talking about, with all my folders and docs in there.

the problem is that sometimes programs can't find their files anymore because they're confusing 'VILES' and 'VILES_' - when I use places on my panel, and use recent documents, sometimes the computer doesn't find these recent files because 'acces to /media/VILES is denied' - others are no problem (I guess these are connected to 'VILES_'

In GParted I can see that the mount point is /media/VILES_ and the label VILES

Any idea how I can get rid of this confusion with the underscore?

Thanks for any help.

running ubuntu 10.10 - GNOME 2.32.0 on a lenovo thinkpad X201

---

### Post by matt_symes on 2011-02-09
Hi

> hi, 

it seems i'm having a problem with the name of one of my hard disk partitions.
this partition is formatted in NTFS since I'm still using win for some applications (another partition is ext4 for ubuntu system).
in ubuntu everything works fine - apart from the fact that there seems to be some confusion about the name of this partition.

I labeled the partition 'VILES' - so it's address should be /media/VILES - however, when I go have a look at file system/media there is two folders, one is called 'VILES' and the other 'VILES_' (including the underscore at the end.
'VILES' is empty and contents are 'unreadable' - 'VILES_' is the partition I'm talking about, with all my folders and docs in there.

the problem is that sometimes programs can't find their files anymore because they're confusing 'VILES' and 'VILES_' - when I use places on my panel, and use recent documents, sometimes the computer doesn't find these recent files because 'acces to /media/VILES is denied' - others are no problem (I guess these are connected to 'VILES_'

In GParted I can see that the mount point is /media/VILES_ and the label VILES

Any idea how I can get rid of this confusion with the underscore?

Thanks for any help.

running ubuntu 10.10 - GNOME 2.32.0 on a lenovo thinkpad X201

Is your forums username your real e-mail address ? I would get it changed otherwise you could well get spammed. Not by people on the forum though.

Anyways to your question. Did you create the directory /media/VILES yourself ?

Try this. Unmount your drive. Check to see if the mount point still exists in /media. if it does delete the mount point

```
sudo rm /media/VILES
sudo rm /media/VILES_
```

Ubuntu will try to create the mount point with the same name as the label in /media. However if this mount point already exists it has to use another, maybe appending an underscore.

Kind regards

---

### Post by mr.peeters@gmail.com on 2011-02-11
Thanks for helping out matt_symes!
However it didn't work completely yet.
I unmounted the partition as you said - media/VILES_ dissapeared alright but media/VILES (the empty and 'unreadable' folder) still exists (see screenshot). [IMG]file:///home/mrpeeters/Desktop/Screenshot.png[/IMG]
When I try to delete it in terminal I get: "cannot remove `/media/VILES': Is a directory"
Any idea how to proceed?

Ah and thanks for the e-mail tip - I was indeed getting some spam lately. 
So I'll change my username.
Cheers for that!

---

