---
title: "Shutdown from a keystroke?"
date: 2006-03-25
forum: General Help
---

### Post by beforewisdom on 2006-03-25
I would like to bind either "shutdown -h now" or "halt" to a keybinding.

I got the hang of binding custom keys with gconf, this one seems to elude me.  I'm guess that it has something to do with root privileges.

Is there anyway I can do this gnome?  My last system ( using that other desktop ) had this and it was a tremendous convenience.

Thanks in advance for information.

Steve

---

### Post by Xian on 2006-03-26
Add this to the end of your sudoers file:

```
ALL ALL = NOPASSWD: /usr/sbin/shutdown
```

Then use this command as the keybinding:

```
sudo shutdown -h now
```

---

### Post by beforewisdom on 2006-03-26
[QUOTE=Xian]Add this to the end of your sudoers file:

```
ALL ALL = NOPASSWD: /usr/sbin/shutdown
```

Then use this command as the keybinding:

```
sudo shutdown -h now
```[/QUOTE]

Got it!  Thanks much!

For the benefit of people who may come to this post in the future through the search I would like to add that the path is "/sbin/shutdown", at least on my system.

Also, only edit /etc/sudoers with visudo( takes you into nano, not vi in Ubuntu):

sudo bash
visudo

This program will not let you save sudoers if  you edit it incorrectly.  If you do edit it incorrectly sudo will be disabled and since you can only access this file as root you will be in a bad spot

If you get into that bad spot (ahem)  you can access your sudoers file by using the livecd and mounting to your hard drive thus ( assuming your hard disk is hda1):

mkdir /mnt/myharddrive

mnt /dev/hda1  /mnt/myharddrive

---

