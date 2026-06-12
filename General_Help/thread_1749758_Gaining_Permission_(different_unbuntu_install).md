---
title: "Gaining Permission (different unbuntu install)"
date: 2011-05-04
forum: General Help
---

### Post by danielgalanos on 2011-05-04
I'll try to briefly outline the issue:

I upgraded from Ubuntu 10 to 10.04 and did so without first backing up my important files (Never doing that again). It no longer boots up past the Ubuntu screen. Whatever, I'll try to grab my files and do a fresh install.

I burned an Ubuntu cd and ran the os off said disk. I then found the location of my old home and root directories somewhere like media/bunchofnumbersandletters/home. I was able to copy some of my files with no issue, but with others I lacked the proper permission to do so. I attempted to use su since I want to be dan@lupus rather than ubuntu@ubuntu but it said that user does not exist, which makes perfect sense but my question is this: how do I 'login' for lack of better expression such that I can cp or mv or whatever my files onto my usb.

I'm rather inexperienced so if you would, please make no assumptions as to what I know how to do because I likely do not. =(

Thanks in advanced! I've seen some of the awesome stuff you've helped other people out with in the past and can only hope.

---

### Post by seawolf167 on 2011-05-04
Try

```
sudo cp /source /destination
```or to grab all subfolders/files as well

```
sudo cp -r /source /destination
```Make sure if your /destination is an external hard drive you mount it (either via the disk manager or using *mount*)

---

### Post by danielgalanos on 2011-05-04
I've tried that already and it didn't work. I think the issue is I'm the wrong user. Right now I'm ubuntu@ubuntu whereas my old install I was dan@lupus.

---

### Post by pme 72 on 2011-05-04
Some other ideas:

Accessing protected Ubuntu files from Live CD:
[http://ubuntuforums.org/showthread.php?t=1745719](http://ubuntuforums.org/showthread.php?t=1745719)

---

### Post by seawolf167 on 2011-05-04
If you are running in a Live session your user will be *ubuntu*

Unless you add another user in the live session you won't be able to change to a different user since the OS wouldn't know who the new user is. 

I'd check that the filesystem is properly mounted first, as you should not run into issues with *sudo* coping files from a LiveCD

```
mount
```

If you want a GUI option you can use

```
gksudo nautilus
```

---

