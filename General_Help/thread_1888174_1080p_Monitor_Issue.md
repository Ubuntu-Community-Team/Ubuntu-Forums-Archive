---
title: "1080p Monitor Issue"
date: 2011-11-28
forum: General Help
---

### Post by JF382 on 2011-11-28
[SOLVED] I have Ubuntu 11.10 and a 1080p Monitor and when I use the HDMI out with my laptop it only goes up to 1024. x728

---

### Post by BC59 on 2011-11-28
What kind of video driver you use?

Did you install the proprietary drivers?

---

### Post by LowSky on 2011-11-28
are you sure you computer can even show 1920x1080? just because a monitor can doesn't mean it will work at that resolution

---

### Post by JF382 on 2011-11-29
> **LowSky said:**
> are you sure you computer can even show 1920x1080? just because a monitor can doesn't mean it will work at that resolution

Well it worked on Windows 7 in 1080p, so it supports it.

---

### Post by JF382 on 2011-11-29
> **BC59 said:**
> What kind of video driver you use?

Did you install the proprietary drivers?

Intel HD Graphics 3000. And what is a proprietary driver, and how would I go upon installing this? Thanks.

---

### Post by BC59 on 2011-11-29
On the upper left part of the left bar "the launcher" push and to the search box right "jockey".

Open the application and see if there is an option to use new video drivers.

---

### Post by JF382 on 2011-11-29
> **BC59 said:**
> On the upper left part of the left bar "the launcher" push and to the search box right "jockey".

Open the application and see if there is an option to use new video drivers.

It says No Proprietary drivers are in use on this system, but no other drivers pop up in that window to install. What do I do? Thanks.

---

### Post by BC59 on 2011-11-29
To show what resolutions are currently supported for your display run:

```
xrandr
```

Now on how you could change resolution see here:

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

---

### Post by JF382 on 2011-11-29
SOLVED. Thank you.

---

