---
title: "Help with copying entire system"
date: 2009-08-12
forum: General Help
---

### Post by tgeer43 on 2009-08-12
Alright folks - please humor me here. I'm trying to recover from a disaster. If I later need to explain how things got to this point or why I'm attempting to do things in this particular way then I will but it's a real clusterf*** that I'd rather not revisit just now.

It's really quite simple. I've copied all of the files from an existing Jaunty 64-bit installation to a folder on a second hard drive. I did this by booting Puppy Linux from a USB flash drive and then using ROX file manager to copy the files. Just for good measure I made a second backup by using the tar command.

Now what I want to do is delete the partition in question, merge it with some other unallocated space, do a fresh install from a live CD, and then copy the files back over. The hoped for outcome is to have the system back exactly the way it was before doing this. I know it sounds like a crazy way to do things but I've got my reasons.

What I really want to know is if it will actually work. More specifically, did copying with ROX get all of the files? Will using ROX to copy everything back over the top of the new install restore everything back to its original condition? I can just as easily use 'cp' from the CLI if need be. Would I be better off untarring the archive that I made over the top of the new install? Is there anything I need to be aware of or look out for?

Thanks in advance for your help - you guys have never let me down yet.

tgeer

---

### Post by snek on 2009-08-12
this shouldn't be too much of ba problem. the most important dirs you need are /etc and /home. if you have those it should be relatively easy. just rfepartition like you said and then copy your home directory over the new one. you will probably need to use sudo for this or start a filemanager with gksu. after this be sure to chmod -R yourusername.yourusername /home/yourusername 

you can have a look in /etc if there are any things you will still need, like /etc/X11/xorg.conf

don't mind the punctuation, i'm writing this from my mobile in the train

---

### Post by mdurham on 2009-08-12
> What I really want to know is if it will actually work. More specifically, did copying with ROX get all of the files? Will using ROX to copy everything back over the top of the new install restore everything back to its original condition?
I think that rsync would have been a better choice than rox, however, can you right click on the saved files directory and get it's size and then do the same to where the files came from. They should be the same size.

---

### Post by dcstar on 2009-08-12
> **tgeer43 said:**
> 
........
Now what I want to do is delete the partition in question, merge it with some other unallocated space, do a fresh install from a live CD, and then copy the files back over. The hoped for outcome is to have the system back exactly the way it was before doing this. I know it sounds like a crazy way to do things but I've got my reasons.

What I really want to know is if it will actually work
........


Probably not, copying back files from a broken system will most likely break the new system unless you know **exactly** what broke the original system and can avoid doing it again.

Far easier to just preserve all user data in a separate /home partition and save the existing installed package lists to be used to reinstall them on the new system.

---

### Post by tgeer43 on 2009-08-20
Well, massive bad blocks on the drive made my crazy idea impractical.

dcstar, what exactly do you mean by "save the existing installed package lists"?

Thanks in advance,

tgeer

---

### Post by nikhilk on 2009-08-20
> **tgeer43 said:**
> dcstar, what exactly do you mean by "save the existing installed package lists"?

I think he means that make a record of all the packages that you have currently installed so that you know what to install on the new system to make it similar to your earlier system.

You can get that list via
```
sudo dpkg -l
```

---

### Post by mdurham on 2009-08-20
Here is what I do:

# Create a text list of an existing installation of all apt-get installed packages
# in order to re-install on a newly installed distro

# make the list
[old distro] sudo dpkg --get-selections >packages

# Now put them back on the new distro
[new distro] sudo dpkg --set-selections <packages

[new distro] sudo apt-get dselect-upgrade

# that's it!

Cheers, Mike

---

### Post by tgeer43 on 2009-08-22
Thank you - that's extremely handy.

tgeer

---

