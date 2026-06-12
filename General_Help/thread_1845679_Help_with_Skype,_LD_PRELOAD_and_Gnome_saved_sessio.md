---
title: "Help with Skype, LD_PRELOAD and Gnome saved session"
date: 2011-09-17
forum: General Help
---

### Post by towheedm on 2011-09-17
I know this worked previously but I cannot say exactly at which point it stopped working.

Hibernate does not work om my machine so as a workaround I have set Gnome to remember running apps when logging off.  This works just fine for me with the exception of skype.

To get my webcam (Sony EyeToy) to work with Skype I must use this command:

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype.
```

Now after logging out and back in, Skype starts, but the webcam does not work.  It appears that the v4l2convert library is not pre-loaded before starting Skype.

As I said, this worked in the past, but after so many updates I cannot pinpoint at which point it stopped working.

Any help is greatly appreciated.

Thanks.

---

