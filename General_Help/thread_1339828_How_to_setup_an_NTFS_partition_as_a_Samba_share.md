---
title: "How to setup an NTFS partition as a Samba share?"
date: 2009-11-28
forum: General Help
---

### Post by DishBreak on 2009-11-28
Hi all,

I recently did a fresh install of Koala (my in-place upgrade was causing too much of a problem). I ended up losing the Samba share I created back in 8.10, and in my brilliance, I did not back up my smb.conf. 

I've been looking for a good guide somewhere, and this Wiki guide is kinda hard to parse:
[https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration)

I wrote my original smb.conf line by line following a forum post. (which I'm sure has faded into oblivion as I can't find it.) 

Now to get to my point: I want to be able to mount my NTFS partition (/media/*), which I do not have ownership over. I've tried adding
```
usershare owner only = false
```
to my smb.conf, but it doesn't seem to work. What am I missing, and where should I be looking for more info?

---

### Post by Baelus on 2009-11-28
There's some info here regarding NTFS and permissions:

[http://ubuntuforums.org/showthread.php?t=1333807]("http://ubuntuforums.org/showthread.php?t=1333807")

---

