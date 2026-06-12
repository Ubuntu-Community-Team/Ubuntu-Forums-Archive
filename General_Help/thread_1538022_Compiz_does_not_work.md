---
title: "Compiz does not work"
date: 2010-07-24
forum: General Help
---

### Post by fishkid257936 on 2010-07-24
after I upgraded to Ubuntu 10.04, I have not been able to use compiz. when it runs, it does not do anything. I tried "<NAME>@LINUX-PC:~$ compiz &
[1] 5881
<NAME>@LINUX-PC:~$ compiz (core) - Warn: No GLXFBConfig for depth  32
Launching fallback window manager"
Also "glxinfo | grep -i render" "direct rendering: Yes
OpenGL renderer string: GeForce2 MX/AGP/SSE/3DNOW!"
Can someone help me?

My Graphics Card is a GeForce2 MX/MX 400.

---

### Post by Zorgoth on 2010-07-24
What drivers are you using?  I would recommend the nVidia binaries if it isn't too old of a card.

---

### Post by fishkid257936 on 2010-07-24
Nvidia 96.43.17

---

### Post by geoffjay on 2010-07-24
That's a pretty old driver, you might want to get the 256.x driver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and install it.

---

### Post by Zeike on 2010-07-24
> **fishkid257936 said:**
> Nvidia 96.43.17

This is a very old version.  Are you using that particular version for a certain reason? You might have better luck with 173 (256 sometimes has problems with older cards like yours)

---

### Post by fishkid257936 on 2010-07-24
will i need to remove the old driver? or will it do it?

---

### Post by geoffjay on 2010-07-24
No need to remove old driver. You will have to back out into a terminal using ctrl+alt+f1 and do:

sudo /etc/init.d/gdm stop
sudo apt-get install linux-headers-`uname -r`
cd /path/to/downloaded/nvidia/driver
sudo sh nvidia-driver

obviously the path and the name of the driver file are dependent on where you downloaded it to and the file that you downloaded.

---

### Post by Zeike on 2010-07-24
> **geoffjay said:**
> No need to remove old driver. You will have to back out into a terminal using ctrl+alt+f1 and do:

sudo /etc/init.d/gdm stop
sudo apt-get install linux-headers-`uname -r`
cd /path/to/downloaded/nvidia/driver
sudo sh nvidia-driver

obviously the path and the name of the driver file are dependent on where you downloaded it to and the file that you downloaded.

Or you know, you could just install the nvidia-173 package.

---

### Post by realzippy on 2010-07-24
AFAIK this (96.xx) is the only driver that works for a geforce2 chip.
Probably this was the only offered driver from *restricted drivers*?

---

### Post by geoffjay on 2010-07-24
Yep, looks like you're right. Did you try [http://ubuntuforums.org/showthread.php?t=1488662](http://ubuntuforums.org/showthread.php?t=1488662) ?

---

### Post by realzippy on 2010-07-24
Because:

*Warn: No GLXFBConfig for depth 32*

run in terminal:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

then restart X...

---

### Post by fishkid257936 on 2010-07-24
uggg not again! ctrl+alt+f1 does not work. just shows a black screen.

---

### Post by geoffjay on 2010-07-24
A black screen with no terminal?

---

### Post by fishkid257936 on 2010-07-24
yep.

---

### Post by fishkid257936 on 2010-07-24
OHHH MYYY GOOOSH. So many probs. I think i am going to switch to openSUSE.

---

### Post by geoffjay on 2010-07-24
Hey if openSUSE works better for you I say go for it.

But before you do that have you tried moving your existing xorg.conf out of the way and restarting? I'm assuming of course that you're on 10.04.

If that breaks things when you come back up do a `sudo nvidia-xconfig` to recreate your xorg.conf.

You could also try removing anything nvidia and reinstall using the driver that you can download from nvidia's site.

To find what nvidia packages you have installed do

dpkg -l nvidia*

and then remove all of them using apt-get remove xxx

---

### Post by fishkid257936 on 2010-07-24
Thanks SOOOO much! that worked! Compiz works! (I am SOOO not going to switch! for some strange reason ctrl+alt+f1 does not work) What i did was remove the driver (that was not the suggested driver), then installed the (suggested) driver.

---

### Post by geoffjay on 2010-07-24
You're welcome. You might want to do some searching or start a new thread for the ctrl-alt-f1 issue, I did a quick google search and found a bunch of threads related to that issue.

---

