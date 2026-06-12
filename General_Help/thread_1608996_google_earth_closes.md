---
title: "google earth closes"
date: 2010-10-29
forum: General Help
---

### Post by sohlinux on 2010-10-29
I just installed google earth but it closes after 2 seconds.

ubuntu 10.10

executing from terminal...

$ googleearth

(process:2160): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.26.0/gobject/gtype.c:2710: You forgot to call g_type_init()

(process:2160): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:2160): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Google Earth has caught signal 11.


Anyone know how to fix this?

---

### Post by JustinR on 2010-10-29
> **sohlinux said:**
> I just installed google earth but it closes after 2 seconds.

ubuntu 10.10

executing from terminal...

$ googleearth

(process:2160): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.26.0/gobject/gtype.c:2710: You forgot to call g_type_init()

(process:2160): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:2160): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Google Earth has caught signal 11.


Anyone know how to fix this?

How did you install GoogleEarth?

---

### Post by sohlinux on 2010-10-30
> **JustinR said:**
> How did you install GoogleEarth?

from synaptic package manager

---

### Post by JustinR on 2010-10-30
> **sohlinux said:**
> from synaptic package manager

Okay. Can you open a terminal and type this:
```

sudo apt-get purge libglib2.0-0 libglib2.0-data
sudo apt-get install libglib2.0-0 libglib2.0-data

```

---

### Post by sohlinux on 2010-10-30
> **JustinR said:**
> Okay. Can you open a terminal and type this:
```

sudo apt-get purge libglib2.0-0 libglib2.0-data
sudo apt-get install libglib2.0-0 libglib2.0-data

```

thanks but it didnt work :(

---

### Post by sohlinux on 2010-10-30
managed to fix it :P

in /home/user/.config/Google/GoogleEarthPlus.conf - changed enableTips=true to enableTips=false

---

### Post by sohlinux on 2010-10-30
google earth is fine but :( street view doesn't work, all stree view images are fuzzy and blurry :(

---

### Post by protpisys on 2010-10-30
This worked for me, just did it this morning and it works fine:

[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

just go step by step

---

### Post by JustinR on 2010-10-30
> **sohlinux said:**
> google earth is fine but :( street view doesn't work, all stree view images are fuzzy and blurry :(

That should mean the image is still loading - loading time depends on how fast your internet connection is.

---

### Post by sohlinux on 2010-10-30
> **JustinR said:**
> That should mean the image is still loading - loading time depends on how fast your internet connection is.

street view is very fast loading in windows so its not an internet speed issue

in ubuntu the first image loads quickly then after all the others are just fuzzy and pixelated, at first I thought they would not load at all but I waited for about 2 -3 minutes then the next image finally loaded. far too slow :(

---

### Post by raydar on 2010-11-07
Google Earth 5.2.1.1588 in Ubuntu 10.10 crashed when the tips window opened, after the splash and after the app loaded, giving me a "signal 11" error.  

I went to edit the config file specified in message #6 of this thread, but found no "enableTips" line in the file.  So, I added

enableTips=false

right above the "lastTip" line (which is to say right below the "VID" line) and now Google Earth seems to work just fine.

---

### Post by sohlinux on 2010-11-07
> **raydar said:**
> Google Earth 5.2.1.1588 in Ubuntu 10.10 crashed when the tips window opened, after the splash and after the app loaded, giving me a "signal 11" error.  

I went to edit the config file specified in message #6 of this thread, but found no "enableTips" line in the file.  So, I added

enableTips=false

right above the "lastTip" line (which is to say right below the "VID" line) and now Google Earth seems to work just fine.

glad to hear it. how well are your street view images loading? mine is extremely slow 1-2 minutes for each image, the first image loads right away.

---

### Post by kuvanito on 2010-11-07
sohlinux,what video card do you have?
i had this very same problem with google earth and I switched from an ATI to a Nvidia card and lots of problems were solved with my Ubuntu.

---

### Post by sohlinux on 2010-11-07
> **kuvanito said:**
> sohlinux,what video card do you have?
i had this very same problem with google earth and I switched from an ATI to a Nvidia card and lots of problems were solved with my Ubuntu.

I am using a laptop so I cant swap the video card but would another driver fix this?

this is what I have in my sony vaio laptop

 *-display
                description: VGA compatible controller
                product: M92 [Mobility Radeon HD 4500 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:49 memory:c0000000-cfffffff ioport:d000(size=256) memory:d0020000-d002ffff memory:d0000000-d001ffff

---

### Post by raydar on 2010-11-08
> **sohlinux said:**
> . . . how well are your street view images loading? mine is extremely slow 1-2 minutes for each image, the first image loads right away.

If you'd have asked me last night, I'd have said very slow; I waited about a minute, like you say.  But I tried it this morning, and it loaded as fast as I could reasonably ask for.  For contrast, there's no appreciable delay when I navigate even the high-res Google Sky imagery at [https://sites.google.com/site/geclusters/](https://sites.google.com/site/geclusters/) and I wonder whether you experience any delay with that.

For what it's worth, I'm running a running a 3GHz Celeron desktop machine with 2GB of RAM, Nvidia 7300GS graphics card with 512MB memory, and have a relatively fast broadband connection.

---

### Post by sohlinux on 2010-11-08
> **raydar said:**
> If you'd have asked me last night, I'd have said very slow; I waited about a minute, like you say.  But I tried it this morning, and it loaded as fast as I could reasonably ask for.  For contrast, there's no appreciable delay when I navigate even the high-res Google Sky imagery at [https://sites.google.com/site/geclusters/](https://sites.google.com/site/geclusters/) and I wonder whether you experience any delay with that.

For what it's worth, I'm running a running a 3GHz Celeron desktop machine with 2GB of RAM, Nvidia 7300GS graphics card with 512MB memory, and have a relatively fast broadband connection.

google sky imagery loads quite fast and strangely enough my street view is loading much faster today, about 20 seconds per image but still quite slow compared to google earth running in windows where the images load in a second or two

---

### Post by ogobeone on 2010-11-14
> **sohlinux said:**
> managed to fix it :P

in /home/user/.config/Google/GoogleEarthPlus.conf - changed enableTips=true to enableTips=false

I just felt the need to second your solution.  This worked for me too, although there was no ´enableTips=true´ entry in my GoogleEarthPlus.conf file.  I simply added ´enableTips=false´ to the document, then typed googleearth at the command prompt.  Prior to that I had the same problem you were having.:KS

---

