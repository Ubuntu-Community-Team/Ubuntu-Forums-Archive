---
title: "Poor Performance in Compiz"
date: 2011-08-05
forum: General Help
---

### Post by Joseph Schwenker on 2011-08-05
I just installed Ubuntu 11.04 onto a new hard drive today, and I've been noticing poor performance with nVidia drivers in Compiz. On my previous 10.10 install, I could resize windows with the "Normal" resize in Compiz easily, but it's extremely laggy in 11.04. Moving windows is also choppy, as is the zoom plugin.
Is this an issue with my drivers? I have an nVidia GeForce 8800GT 512MB and am using the "current" drivers from Additional Drivers.

---

### Post by realzippy on 2011-08-05
Maybe you should check
if sync to Vblanc is enabled in compiz and/or nvidia-settings
and disable it.

---

### Post by Joseph Schwenker on 2011-08-05
Thanks for your response, realzippy. Sync to vblank is unchecked in Compiz, but it's not in nVidia X Server Settings. I unchecked it there just now, but I assume I'll have to reboot before I see any potential performance improvement.

---

### Post by realzippy on 2011-08-05
running
```
nvidia-settings -l
```

should be enough

---

### Post by Joseph Schwenker on 2011-08-05
Nope, didn't work. Just restarted my computer and still had bad performance. I tried running that command, too, but Windows are still choppy when they move around.
I just found that there are two different sync to vblank options in nVidia X server settings, I had unchecked the one in X Server XVideo Settings, but not in OpenGL settings. I just unchecked the other one, switched from Compiz to Metacity then back to Compiz again. I also ran nvidia-settings -l, but I still have choppy windows.
Is this a driver issue?

---

### Post by Joseph Schwenker on 2011-08-05
Just restarted my computer, but I'm still getting choppy performance. Attached is a screenshot of my nvidia-settings window, for reference.

---

### Post by wildmanne39 on 2011-08-05
Hi, are you using unity or classic?

---

### Post by Joseph Schwenker on 2011-08-05
I'm using Ubuntu Classic.

---

### Post by wildmanne39 on 2011-08-05
Hi, that is what I thought here is a fix that usually works for classic.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by Joseph Schwenker on 2011-08-06
> **wildmanne39 said:**
> Hi, that is what I thought here is a fix that usually works for classic.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

HOLY JESUS! That fixed my problem! You win 10 internets, a cookie, and many kudos.

---

### Post by wildmanne39 on 2011-08-06
Hi, your welcome! I am glad it worked,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by Joseph Schwenker on 2011-08-06
> **wildmanne39 said:**
> Hi, your welcome! I am glad it worked,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

Yep, already did that before you even posted your message. ;)

---

### Post by Jetro on 2012-11-07
The answer is to downgrade? :(
I get choppy zooming, not any other effects are bad (as I can see), but the zooming is horrible! Latest Ubuntu version (12.10).

---

### Post by wildmanne39 on 2012-11-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

