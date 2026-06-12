---
title: "filesystem black hole"
date: 2010-11-10
forum: General Help
---

### Post by dcompiled on 2010-11-10
I have been getting low file space warning on my system which is odd because I'm not using that much space.  When I use the disk usage viewer to explore where all the space has gone it believes my home folder is using 8GB.  When I look at the contents of the folder the largest item is the documents folder which takes up 12%.  I am only able to account for about 1GB of the 8GB.  How can this be?  I also tried 

du ~ --max-depth=1 -h

Which gave the same information.

---

### Post by Jeruvy on 2010-11-10
Try using the following options:

```

du -h -c -s /
```

this way you should check all the folders in your files system. (This should not scan any removable devices)

Its quiet except for some errors that may pop up, no worries.  Then it gives you a total.  If you want a more exact number, remove the '-h' option.

---

### Post by WorMzy on 2010-11-10
Use baobab to get a more in-depth reading of where space is being used.

Also, are you using a Wubi installation, or a partition installation?

---

### Post by dcompiled on 2010-11-10
I am using a partition install.  I think the .gfvs folder in my home folder is eating up all the space but im not sure what this folder does exactly.  Something about gnome vfs.

---

### Post by WorMzy on 2010-11-10
gvfs = GNOME Virtual File System

Are you mounting any external filesystems (e.g. a FTP server, Samba server) as your user? The space these virtual filesystems take up shouldn't count towards your actual diskspace usage, since the files are on a remote system.

Of course, if you're not mounting anything, then the .gvfs folder should be empty.

---

### Post by dcompiled on 2010-11-10
I am mounting a windows share.  Because this is perplexing me see the linked image for a better visual.

[IMG]http://www.columbia.edu/%7Eamg2229/misc/ubuntu-fs.png[/IMG]

---

### Post by dcompiled on 2010-11-10
[http://www.cs.columbia.edu/~amg2229/misc/ubuntu-fs.png]("http://www.cs.columbia.edu/%7Eamg2229/misc/ubuntu-fs.png")[IMG]http://www.cs.columbia.edu/%7Eamg2229/misc/ubuntu-fs.png[/IMG]

---

### Post by bcbc on 2010-11-10
Run the disk usage analyzer as root:
gksu baobab

That might tell a different story. Also go to preferences and check the 'select devices' to include in filesystem scan. If there's anything mounted it should show up there.

---

### Post by dcompiled on 2010-11-10
> **bcbc said:**
> Run the disk usage analyzer as root:
gksu baobab

That might tell a different story. Also go to preferences and check the 'select devices' to include in filesystem scan. If there's anything mounted it should show up there.

Interesting idea - I see exactly the same thing.  Maybe the disk is corrupted or something.  I guess I can try to run fsck.  Any other ideas?

---

### Post by bcbc on 2010-11-11
> **dcompiled said:**
> Interesting idea - I see exactly the same thing.  Maybe the disk is corrupted or something.  I guess I can try to run fsck.  Any other ideas?

I'm leaning towards the black hole theory as well ;)

---

### Post by dcstar on 2010-11-11
> **dcompiled said:**
> Interesting idea - I see exactly the same thing.  Maybe the disk is corrupted or something.  I guess I can try to run fsck.  Any other ideas?

Really?, I see significantly different readings when baobab is run under root or user privileges.

---

### Post by bcbc on 2010-11-11
> **dcstar said:**
> Really?, I see significantly different readings when baobab is run under root or user privileges.

Not so much on your home directory.

---

### Post by theSuperman on 2010-11-11
I have never heard of baobab, but I have used gdmap a lot. Maybe see what that finds.

---

### Post by dcompiled on 2010-11-12
SOLVED:

Should have used the -a option to DU within my home folder.  There was a hidden file created 6.5GB large called .xsession-errors.old.   Does anyone have an idea what this file is and why it my grow to such an enormous size?

```
du -ach --max-depth=1 ~
```

---

### Post by dcompiled on 2010-11-12
To the curious reader this appears to be the problem:

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/592492]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/592492")

Bugs in flash...

---

