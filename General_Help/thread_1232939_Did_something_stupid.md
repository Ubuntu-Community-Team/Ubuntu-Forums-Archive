---
title: "Did something stupid"
date: 2009-08-06
forum: General Help
---

### Post by zmzach on 2009-08-06
Well the long and the short of it is I think I accidently deleted my kernel. Deleted this folder: /lib/modules/2.6.24-24-generic

However I ran sudo apt-get update and apt-get upgrade from 2.6.23-23 in grub and at least now I can get most everything running successfuly. before I would log into gnome and all I would see what a blank tan screen with my mouse.

Now though I've got a couple problems:
-No sound
-No wireless network
-Lost my "STUFF" folder on the desktop which contained my music, pictures, etc. Funny thing is, a couple of pictures that were on my desktop are still there.

Do I just need to work through these problems or is there an easy-er fix to this?

---

### Post by SyL on 2009-08-11
> **zmzach said:**
> 
-Lost my "STUFF" folder on the desktop which contained my music, pictures, etc. Funny thing is, a couple of pictures that were on my desktop are still there.


 do you mean /home/<userid>/stuff?

```

sudo updatedb
locate stuff

```


Looking for a particular file?


```

locate filename
locate "*.avi"

```[http://www.linfo.org/locate.html](http://www.linfo.org/locate.html)



> **zmzach said:**
> is there an easy-er fix to this?

re-install

---

