---
title: "Google Earth"
date: 2010-09-18
forum: General Help
---

### Post by FahadMKS on 2010-09-18
I have installed the Google earth by following the steps in the link [http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/) and it has got installed, but the issue is that, I am not able to access it as it gets closed automatically when opening.

Can anyone help me in this issue?

Note: there is no error message as it just closes.
I have also installed the graphics driver uptodate

---

### Post by HermanAB on 2010-09-18
Hmm, I think the Google Earth software developers were hired from Microsoft...

Google Earth is best avoided.  It is a POS.

---

### Post by FahadMKS on 2010-09-18
Its OK, but can you help me in finding a software as similar to the Google Earth.

---

### Post by jondodson on 2010-09-18
Hi.  It's best installed using the software centre, which will install it into the correct place and grant it the correct permissions to run.  I think you need to install the medibuntu repository first so that GE appears in the software centre.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by FahadMKS on 2010-09-18
I will try this and let you guys know

---

### Post by Soul-Sing on 2010-09-18
> **jondodson said:**
> Hi.  It's best installed using the software centre, which will install it into the correct place and grant it the correct permissions to run.  I think you need to install the medibuntu repository first so that GE appears in the software centre.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

yep i had the same here, via medibuntu it runs fine....

---

### Post by FahadMKS on 2010-09-20
Thank you guys, the issue has now been solved.

---

### Post by SubCool on 2010-09-20
> **jondodson said:**
> Hi.  It's best installed using the software centre, which will install it into the correct place and grant it the correct permissions to run.  I think you need to install the medibuntu repository first so that GE appears in the software centre.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Thank you!

---

### Post by FahadMKS on 2010-10-29
I tried to install the Google Earth to the new Ubuntu 10.10 and I am not able to do it.

The software was loaded in the 10.04 version, but not in the new ver.

I installed the version from the Synpatic, but the Launching Icon is not there in the Menu.

What should I do to get this issue resolved.

I have loaded the Pic of what I get when I try to install the Google Earth using the sh command.

---

### Post by protpisys on 2010-10-30
this works, just follow step by step:

[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

---

### Post by FahadMKS on 2010-10-31
That step was awesome dude.........
it workd, and now i have the package installed, but the issue is that, when I try to open google earth, it closes unexpectedly

---

### Post by wightghost on 2010-10-31
I've been following this thread since I had trouble installing and loading Google Earth too.  I followed the advice of this thread:

> [http://ubuntuforums.org/showthread.php?t=1429155](http://ubuntuforums.org/showthread.php?t=1429155)

and deleted the .googleearth folder in the home folder then started google earth again and it worked fine.

Hope this helps.:)

---

### Post by FahadMKS on 2010-11-13
I have tried that step and the issue still seems to be there.

I tried to reinstall the Google Earth and after a fresh reinstallation also the issue seems to be there.

Is there anything else that can be done?????

---

### Post by oldos2er on 2010-11-13
Are you using the latest drivers for your video card? Google Earth requires video drivers with 3d hardware acceleration.

---

### Post by FahadMKS on 2010-11-13
Yes, I have installed the Latest Drivers for Nvidia via Additional Drivers option.

---

### Post by oldos2er on 2010-11-13
Can you run **googleearth** in a terminal, and post all the output here? It may or may not help diagnose the problem.

---

### Post by FahadMKS on 2010-11-13
Yes,
 I opened the Terminal and then typed googleearth and hence the software started and then closed automatically as before.

```

```fahadmks@fahadmks-desktop:~$ googleearth

(process:2070): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.26.0/gobject/gtype.c:2710: You forgot to call g_type_init()

(process:2070): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:2070): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/fahadmks/.googleearth/crashlogs/crashlog-4cdf4ba7.txt

Please include this file if you submit a bug report to Google.
fahadmks@fahadmks-desktop:~$ 
```

```


This is what I get in the Terminal.

---

### Post by oldos2er on 2010-11-14
Maybe there's something here that can help you: [http://www.google.ws/support/forum/p/earth/thread?hl=en&tid=522e9e6586ef2cc2](http://www.google.ws/support/forum/p/earth/thread?hl=en&tid=522e9e6586ef2cc2)

---

