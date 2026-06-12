---
title: "Adobe Flash Plugin has no audio"
date: 2009-12-15
forum: General Help
---

### Post by Burky on 2009-12-15
My Adobe Flash Plugin for Mozilla Firefox used to work properly, now it only plays the video w/o any sound. Any help? I'm using Karmic Koala.

---

### Post by scouser73 on 2009-12-15
[COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

---

### Post by Burky on 2009-12-15
> **scouser73 said:**
> [COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

That's currently the way I installed it originally. Not working...

---

### Post by adamsojc on 2010-01-03
I don't know if this will help you or not but lots of folks seem to overlook this simple thing.

When Karmic 9.10 installs the PCM audio volume is all the way down.

Check that it is adjusted all the way up by right clicking on the speaker icon in the system tray and show the mixer.  If necessary configure the mixer to show the PCM channel and turn the volume up.

It took me a while to figure this out.  I hope it helps.

---

### Post by bozo_the_grey on 2010-01-04
Hi,

I noticed this problem today on my machine (kubuntu karmic koala amd64 ). Not sure what happened as audio was working two days ago. I'm trying to work out what I did install. Maybe some nvidia drivers. Do you know if there is a way to see the packages I have installed in the last days ?

Thanks

Bozo

---

### Post by Burky on 2010-01-09
By installing libflashsupport and rebooting my system, it fixed the problem.
```
sudo apt-get install libflashsupport

```

---

