---
title: "How do I create shortcuts to the desktop from a folder on a NAS drive?"
date: 2011-01-01
forum: General Help
---

### Post by helipilotx on 2011-01-01
Hello guys. Here is my dilemma! 

Like always Linux likes to make the easy tasks in life a little bit more difficult. :confused:

I have a NAS and Ubuntu 10.x  I like to make a shortcut from a folder on the NAS drive to the desktop.

If i right click on the file and click 'Make Link' it tells me that the target does not support symbolic links. :mad:

So what can I do to make it happen?

is there maybe a way so mount the NAS like a fixed system disk? Because from the system disc I am able to make links. 


Thanks ...  ):P

---

### Post by dcstar on 2011-01-02
> **helipilotx said:**
> Hello guys. Here is my dilemma! 

Like always Linux likes to make the easy tasks in life a little bit more difficult. :confused:

I have a NAS and Ubuntu 10.x  I like to make a shortcut from a folder on the NAS drive to the desktop.

If i right click on the file and click 'Make Link' it tells me that the **target does not support symbolic links**. :mad:

So what can I do to make it happen?

is there maybe a way so mount the NAS like a fixed system disk? Because from the system disc I am able to make links. 


Thanks ...  ):P

This might help:

[http://forum.linuxmint.com/viewtopic.php?f=90&t=33604&start=0](http://forum.linuxmint.com/viewtopic.php?f=90&t=33604&start=0)

Also installing the **smbfs** package may help.

---

### Post by gandaran on 2011-01-02
> **helipilotx said:**
> Hello guys. Here is my dilemma! 

Like always Linux likes to make the easy tasks in life a little bit more difficult. :confused:

I have a NAS and Ubuntu 10.x  I like to make a shortcut from a folder on the NAS drive to the desktop.

If i right click on the file and click 'Make Link' it tells me that the target does not support symbolic links. :mad:

So what can I do to make it happen?

is there maybe a way so mount the NAS like a fixed system disk? Because from the system disc I am able to make links. 


Thanks ...  ):P
have you tried bookmarking the drive in nautilus (or bookmark any folder on the drive) name the drive whatever you like the then it will be in the panel places menu, I think this is the best solution but if you prefer a desktop shortcut launcher it should work just by filling in the start command with  something like 'smb://192.168.0.1/usb1-c/' (this ip is mine check what is yours)
I don't recommend system mounting the drive unless you have to use some backup tool, it's unnecessary just to access the drive.

---

### Post by Vigh on 2011-01-02
agree bookmark using nautilus, click connect to server, type ip address of NAS, when it comes up bookmark the folder you want to have a link to in nautilus, what I did

---

### Post by helipilotx on 2011-01-02
How can I 'System Mount' a NAS?  (please how exactly not just use i.e. xyz...)

---

### Post by Vigh on 2011-01-02
click places in the top menu and just click connect to server, make permanent link, its stored in bookmarks then

---

### Post by davec64 on 2011-01-02
Have a look in:

```
/home/<username>/.gvfs
```

For some reason a NAS box is mounted here. You should be able to create a symlink to this folder if you want.  :)

---

### Post by gandaran on 2011-01-03
> **helipilotx said:**
> How can I 'System Mount' a NAS?  (please how exactly not just use i.e. xyz...)
cifs would be the best way to mount any network drive but would be a temporary mount, if you want the drive to mount at startup you have to add the drive mount option to /ect/fstab.
this is a cifs guide (install cifs from package manager) to mount the drive temporary or permanent fstab, it's for opensuse but works the same for ubuntu.
[http://opensuse.swerdna.org/susesambacifs.html](http://opensuse.swerdna.org/susesambacifs.html)

---

