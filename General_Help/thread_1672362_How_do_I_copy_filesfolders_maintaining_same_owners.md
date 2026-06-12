---
title: "How do I copy files/folders maintaining same ownership, etc. using Nautilus?"
date: 2011-01-20
forum: General Help
---

### Post by carlos123 on 2011-01-20
Hi there, 

I am trying to move data between two laptops using a USB Flash drive.  From my old laptop to my new one. 

The problem I am having is that some files/folders are owned by root in my home directory while most are owned by my user. 

If I use something like Nautilus, Gnome-Commander, MC, to copy and run these programs as my user, when a root owned file is encountered, an error occurs (obviously) in that my user cannot copy a root owned file. 

If I run these programs as root and then copy, all files and folder copies are changed to Root as owner. 

I am rather stuck wondering how in the world I can copy my Home directory with some files/folders owned by my user and some by root over to my new Home directory without any change to ownership, permissions, etc..

Oh..I would like to make such copies without using the command line if possible. 

Any advice would be appreciated. 

Thanks. 

Carlos

---

### Post by Ex_Machina on 2011-01-20
After copying do
chown <yourusername>:<yourusername> filename
over the files.

use -r for recursive or just * for like everything in that directory.

Good luck.

---

### Post by carlos123 on 2011-01-20
Thanks but I can't do that.  I want to maintain the SAME owner and everything about these files without setting all to one particular owner or another. 

In other words if my original Home directory has some owned by Root and some owned by user Carlos I want the new Home directory to again have those same files owned by whoever they are owned by. 

If I chown then all files will be set to a particular owner (or I will have to spend all day doing a chown one at a time on particular files). 

Does anyone know of a way to copy all files/folders through a GUI client under Linux that allows one to keep all permissions, owners, etc.?  

Carlos

---

### Post by mikewhatever on 2011-01-20
It's odd, you shouldn't have files owned by root in your home folder. What are they?

---

### Post by Ex_Machina on 2011-01-20
Maybe tarring it and unpacking it at the location will do

---

### Post by carlos123 on 2011-01-20
Thanks for the input you all but I don't have time to explain why I have files owned by root, www-data, or whoever inside my Home directory.  I am just looking for a way to copy them while maintaining same permissions, ownership, etc. using a GUI client. 


Thanks. 

Carlos

---

### Post by mikewhatever on 2011-01-20
It's ok, carlos, you don't have to explain. I think Ex_Machina's suggestion is the way to go, especially since you are going to use flash drives, probably with ntfs/fat32 file systems which don't preserve linux permissions. Tar your home directory as root, then copy the archive, then untar to the new computer.
```

sudo -i
cd /
tar cvpzf carlos-home.tgz /home/carlos/

```

To untar:

```

sudo -i
tar xvpfz carlos-home.tgz -C /home/
```

Not quite sure about a gui client.

---

### Post by carlos123 on 2011-01-20
Interesting..using tar I mean. Never used it like that before. 

Unfortunately my tar file would be several GB in size but I guess I could do it in chunks. 

I figured out how to do it through a GUI though. 

gnome-commander used as root will copy all files and folders and preserve everthing though initially...they appear as user root.  But as the copy progresses their original permissions are set and things are good. 

I got thrown off by the way it initially made everything root I think. 

Thanks again. 

Carlos

PS.  I GUI was much, much easier than command line for what I needed as I had to be very selective and carefully copy over only certain directories and files as my old laptop is very unstable and freezes up a lot.

---

### Post by Conzo on 2011-01-20
> **carlos123 said:**
> Hi there, 

I am trying to move data between two laptops using a USB Flash drive.  From my old laptop to my new one. 

The problem I am having is that some files/folders are owned by root in my home directory while most are owned by my user. 

If I use something like Nautilus, Gnome-Commander, MC, to copy and run these programs as my user, when a root owned file is encountered, an error occurs (obviously) in that my user cannot copy a root owned file. 

If I run these programs as root and then copy, all files and folder copies are changed to Root as owner. 

I am rather stuck wondering how in the world I can copy my Home directory with some files/folders owned by my user and some by root over to my new Home directory without any change to ownership, permissions, etc..

Oh..I would like to make such copies without using the command line if possible. 

Any advice would be appreciated. 

Thanks. 

Carlos


First off   add some Nautilus stuff  
**sudo apt-get install libapr1 libaprutil1 libsvn1 nautilus-actions  nautilus-gksu nautilus-image-converter nautilus-open-terminal  nautilus-script-audio-convert nautilus-script-collection-svn  nautilus-script-manager nautilus-scripts-manager nautilus-wallpaper  subversion**


After this you will be able to right click the folder and OPEN AS ADMIN (root ) 
this will take care of the non ower stuff ! 

Conzo

---

### Post by carlos123 on 2011-01-20
That's weird the way gnome-commander does it. 

It will copy a whole set of directories and make them all owned by Root.  Until it is through with the whole copy operation.  And then, right before my eyes, it will change them all to the ownership that they were in the original. Almost as an afterthought. 

Carlos

---

### Post by carlos123 on 2011-01-20
Thanks Conzo but I figured out how to do it through gnome-commander or at least get around it's quirks. 

I hardly ever use Nautilus anyway. 

Carlos

---

### Post by carlos123 on 2011-01-21
Well...gnome-commander copied the owner correctly but it messed up the permissions.  The permissions are not what they were but rather they are the system default one's that come standard with Ubuntu. I have changed a bunch of those as I have a local copy of Apache installed and use it to simulate a working web server for web development work. 

Back to the drawing board..sigh...

I guess I have little choice but to resort to the command line at this point. 

Linux can be such a pain sometimes when all I want to do is get a working copy of the files and directories I had on my other laptop!  

Oh well...

Carlos

---

### Post by omegaFil on 2011-07-08
I'm not fully sure but try...

[FONT=Courier New]cp -R --preserve <things to copy>[/FONT]

Hope it works nice

---

