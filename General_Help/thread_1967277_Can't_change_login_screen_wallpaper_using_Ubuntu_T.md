---
title: "Can't change login screen wallpaper using Ubuntu Tweak Tool"
date: 2012-04-28
forum: General Help
---

### Post by Zukaro on 2012-04-28
I'm trying to change my login screen wallpaper to another wallpaper; I've downloaded Ubuntu Tweak Tool and chosen the wallpaper I want to use, but it wont display.  All that's displayed is a blank screen instead (however, the original wallpaper will still display if I change it back to that).

I'm using Ubuntu 12.04 (64 bit).

---

### Post by Zukaro on 2012-04-28
Could anyone help?  I'm not sure how to get it working and everything on Google basically says it just works.

---

### Post by GameX2 on 2012-04-28
Have you seen this topic?

[http://ubuntuforums.org/showthread.php?t=1967801](http://ubuntuforums.org/showthread.php?t=1967801)

Good luck!

---

### Post by Zukaro on 2012-04-28
No I haven't, but thanks.  :P
I'll try some of the suggestions there.

---

### Post by Zukaro on 2012-04-29
[https://bugs.launchpad.net/ubuntu-tweak/+bug/888186](https://bugs.launchpad.net/ubuntu-tweak/+bug/888186)

I've managed to get it working based on the posts in there.

The issue is due to a bug.  To get around this issue you need to copy your wallpaper to /usr/share/backgrounds and then set the permissions to read only (there's 3 permissions sections, set the last two to read only and leave the first on as read/write).

That should fix it.

---

### Post by PCLinuxGuy on 2012-08-05
> **Zukaro said:**
> [https://bugs.launchpad.net/ubuntu-tweak/+bug/888186](https://bugs.launchpad.net/ubuntu-tweak/+bug/888186)

I've managed to get it working based on the posts in there.

The issue is due to a bug.  To get around this issue you need to copy your wallpaper to /usr/share/backgrounds and then set the permissions to read only (there's 3 permissions sections, set the last two to read only and leave the first on as read/write).

That should fix it.

has there ever been a fix for this bug in tweak? I've the same issue in 10.04 LTS 64 bit.  I had a feeling the workaroound you posted was something that may work and glad to know it's a possible workaround.  what about the whole setting the appearance window to come up at login to change it that way?

---

### Post by Steven D on 2012-08-06
Make sure your folder containing the pictures isn't set so only your user can read the files. Had same issue, set to anyone can read-only and it worked.

---

