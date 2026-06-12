---
title: "Nautilus Segfaults"
date: 2009-12-12
forum: General Help
---

### Post by paranoid_humanoid on 2009-12-12
Nautilus won't start all of a sudden. All I get is a cryptic Segmentation fault.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/495715](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/495715)
I don't know what to do now!

---

### Post by RedSingularity on 2009-12-12
Try reinstalling nautilus?

---

### Post by paranoid_humanoid on 2009-12-12
No, that did not work. It has to do with my user's config files. It works will as root.

---

### Post by RedSingularity on 2009-12-12
Go into your home folder and press ctl + H to show the hidden folders.  Delete the .nautilus folder.  Then try starting it up again.

---

### Post by paranoid_humanoid on 2009-12-12
I tried that. The folder gets recreated and left empty. It must be another directory or some other corrupted file.

---

### Post by RedSingularity on 2009-12-13
Ok delete that one again and these as well.

/home/you/.gconf/apps/nautilus
and...
/home/you/.gnome2/accels/nautilus

If this doesnt work you can install another file manager until you fix nautilus.  

Hint:  If you do the following command you will find all the nautilus items on your computer........you can then delete them all and reinstall the software to see if it made a difference. 

sudo find / -name nautilus

---

### Post by paranoid_humanoid on 2009-12-13
This is really frustrating, I did everything you said. Deleted everything that came out of `find` and reinstalled every package that had the name "nautilus" from synaptic and still it did not work!

I'm using Thunar now as my default file manager but I'm not at all happy with it :(
And I have no desktop icons any more. Nautilus was in charge of that :(

---

### Post by RedSingularity on 2009-12-13
You said on launchpad that it works under other users?  Like root?

---

### Post by paranoid_humanoid on 2009-12-13
Yeah, it does.

---

### Post by RedSingularity on 2009-12-13
Hmmm so your are correct then..........its just a problem in your personal directory.  Try this command then,

find /home/your-name -name nautilus*

That may bring up other files that you didnt see before.

---

### Post by paranoid_humanoid on 2009-12-13
It did not find any more files or directories. Just the ones I deleted in the last attempt :(

---

### Post by RedSingularity on 2009-12-13
On thing i would try is removing it like this................

 sudo apt-get autoremove --purge nautilus

then search for all the files again and delete those as well.  That way you know you have deleted any know config file.

---

### Post by ubername on 2009-12-13
> **RedSingularity said:**
> On thing i would try is removing it like this................

 sudo apt-get autoremove --purge nautilus

then search for all the files again and delete those as well.  That way you know you have deleted any know config file.

Whoops. Tried this. It has removed GNOME (part of dkms* which the above command removed?), and I can't reinstall as it 'Depends: swfdec-mozilla but it is not going to be installed'

(I am on Lucid, so I don't know if this would affect stable releases!) 

Fortiunately I have XFCE which is working well.

(By the way, purging nautilus, removing all instances of find ~/nautilus* then reinstalling nautilus didn't resolve the issue -  still get 
(nautilus:3806): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed)

Update: fixed 'missing gnome' problem;  I had to reinstall 'gnome-desktop-environment', not 'gnome'

---

### Post by paranoid_humanoid on 2009-12-13
You have that problem as well?

Actually I don't think the "Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()" failed message is about this error, because launching nautilus as root produces this message as well but nautilus starts up correctly.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
Delete the .themes folder?

---

### Post by paranoid_humanoid on 2009-12-13
> **Sin@Sin-Sacrifice said:**
> Delete the .themes folder?

Nope. Did not work!

---

### Post by john newbuntu on 2009-12-13
A few things I would try in a seg fault situation are:
1. memory diagnostics - good to make sure we do not have hardware issues
2. reinstall gdm/ubuntu desktop (perhaps a dependent lib is missing or the version is different)
3. Run nautilus with strace (might point out if a file read/write went bad)

---

### Post by paranoid_humanoid on 2009-12-14
Fixed it =P~
Running strace on nautilus I found out it's checking for files in ~/.local/share so I backed it up and let Nautilus start with a fresh empty one and it started fine. The first thing it did is it created the directory gvfs-metadata, so it must've been a corrupted file over there because I deleted it from the back up and restored it and now it's working again :D

Thanks a lot to everyone who helped me with this, I really appreciate it :biggrin:

---

### Post by ubername on 2009-12-14
I renamed ~/.local/share/gvfs-metadata  to ~/.local/share/gvfs-metadata.old, logout then login, Desktop is back - thanks to all.

---

### Post by Hawy.php on 2009-12-23
> **ubername said:**
> I renamed ~/.local/share/gvfs-metadata  to ~/.local/share/gvfs-metadata.old, logout then login, Desktop is back - thanks to all.

Thanks so much 
i faced same problem and i tried alot of things 
renaming my .gnome and deleting my .nautilus folders 
and not works 

just renaming metadata that works perfect for me 

:popcorn:

---

