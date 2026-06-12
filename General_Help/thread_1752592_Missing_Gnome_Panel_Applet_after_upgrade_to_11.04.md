---
title: "Missing Gnome Panel Applet after upgrade to 11.04"
date: 2011-05-08
forum: General Help
---

### Post by Spr0k3t on 2011-05-08
So the upgrade has been done but there's something I'm missing from my day to day usage on my primary system.

[img]http://ubuntuforums.org/attachment.php?attachmentid=191524&stc=1&d=1304829417[/img]

I can't find this applet anywhere (Remote Desktop Viewer).  Need some help/suggestions.  The "Connect to Server" is not going to work for my needs.  I've set up a launcher temporarily but would like to see the panel applet option back.

---

### Post by carl4926 on 2011-05-08
Are you logging in using Ubuntu Classic

---

### Post by Spr0k3t on 2011-05-08
Yes.  This is in the gnome environment without Unity.

---

### Post by carl4926 on 2011-05-08
Worth checking a new user login to see if it's just some crud from the old /home/user*
or something deeper

---

### Post by Spr0k3t on 2011-05-08
Good suggestion, however the applet is still missing from the list to be able to add it.  Tried a clean install to verify this issue.  I'm wondering if I build the latest vinagre (3.0.1) if it would include the applet or if it's something the devs have removed.

Onward to the VMs!

---

### Post by Spr0k3t on 2011-05-08
Well, looks like the problem is psuedo solved.  The package vinagre has been compiled with the --without-panelapplet leaving the single feature I'm looking for out of the loop.  The problem on the otherhand is dealing with multiarch cmake support for building packages from source.  There's a work around but it's rather hackish and could possibly break.  I was able to get it working in the VM, but will wait until the cmake upstream is put back in order.

I miss the panel applet... made things so much faster.

[Related Bug](https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/751940)

---

