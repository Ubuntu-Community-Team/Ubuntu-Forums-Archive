---
title: "Moving up to 11.04"
date: 2011-05-20
forum: General Help
---

### Post by ddjolley on 2011-05-20
I have been running Ubuntu 10.04 on my laptop for sometime.  I am now replacing Fedora 9 on my desktop with Ubuntu 11.04.  When I first boot my new desktop installation (11.04), the first thing I see is a warning:

Video mode not supported.

That concerns me although the boot seems to continue normally.  After logging in I will often see the screen flash blank and return.  When it returns the cursor is missing.  If I do a series of reboots I can eventually get the cursor to return.

I'm wondering what I need to do to start resolving these difficulties.

Thanks for any input.

        ... doug

---

### Post by Hedgehog1 on 2011-05-20
This is caused by the resolution for the new grub menu being too high.

Please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by ddjolley on 2011-05-21
Thanks.  That takes care of the video-not-supported issue.  I'm still having cursor problems.  I thought that the two issues might be related.  Apparently they are not.  Accordingly, I'll re-post on the cursor issue.  Thanks for the help.

       ... doug

---

