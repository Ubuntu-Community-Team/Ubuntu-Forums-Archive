---
title: "ubuntu 10.10 on hp compaq tc1100 nvidia driver"
date: 2010-11-06
forum: General Help
---

### Post by vipern0odle on 2010-11-06
I have successfully installed ubuntu 10.10 on an old hp compaq tc1100. 

Ubuntu 10.4's hardware driver function found the right driver and installed it. 

Using the "current" driver on 10.10 causes boot failure (fatal error no screens found).

Ubuntu identifies my graphics card as 01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)

Which nvidia driver should I install? 96? 96 worked in 10.4.

Any help would be much appreciated.

---

### Post by MyR on 2010-11-06
[http://ubuntuforums.org/showthread.php?t=563736](http://ubuntuforums.org/showthread.php?t=563736)

---

### Post by vipern0odle on 2010-11-07
Thank you for your reply. I am aware of these posts. However, they refer to Ubuntu 8.10 and nothing after that. The "additional drivers" programme states that no drivers are in use. WHen I ask it to check for drivers, it repeats the message. I have tried to install the current driver but that leads to the errors cited in my first post. I'm afraid to install the nvidia 96 driver (even tohugh it worked in 10.4)  since I don't want to reinstall everything. I have backed everything up and I have even used AptOnCD to make backups of all my updates so I suppose it's worth a try. Any last words of wisdom? Thanks so much for your help.

---

### Post by MyR on 2010-11-07
The posts continue on past the first page.  On the top and bottom right of the page you can move between pages.  The thread that I linked to is very long, so it would save time to start at the end and read the newest posts first.

You can manually install the latest 96 pre-release if you need 3-D acceleration, otherwise you don't need it.

---

### Post by redbook4574 on 2010-11-07
> **vipern0odle said:**
> I have successfully installed ubuntu 10.10 on an old hp compaq tc1100. 

Ubuntu 10.4's hardware driver function found the right driver and installed it. 

Using the "current" driver on 10.10 causes boot failure (fatal error no screens found).

Ubuntu identifies my graphics card as 01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)

Which nvidia driver should I install? 96? 96 worked in 10.4.

Any help would be much appreciated.

Stick with lucid Nvidia96 drivers are not playing in maverick

---

### Post by MyR on 2010-11-07
> **redbook4574 said:**
> Stick with lucid Nvidia96 drivers are not playing in maverick

Incorrect, the latest 96.43.19 pre-release is working.

---

### Post by redbook4574 on 2010-12-20
> **MyR said:**
> Incorrect, the latest 96.43.19 pre-release is working.

OK now working with 96.43.19, one problem, how do I get the pointer to rotate. It stubbornly remains 90 degrees out of sync.

---

### Post by jetak on 2010-12-28
I also got the nvidia 96.43.19 drivers working. To get the Stylus(Pointer) to rotate correctly I followed the directions given here: [http://www.unifyingtheory.net/ubuntu10.04tc1100.html]("http://www.unifyingtheory.net/ubuntu10.04tc1100.html") with a few changes.
> gedit rotate```
#!/bin/sh
if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "Serial Wacom Tablet stylus" Rotate NONE
else
        xrandr -o left
        xsetwacom set "Serial Wacom Tablet stylus" Rotate CCW
fi
```chmod +x rotate
sudo mv rotate /usr/bin/rotate
Note the name "Serial Wacom Tablet _stylus_" (The original directions omitted the stylus part). 

Check out [http://ubuntuforums.org/showthread.php?t=1423278]("http://ubuntuforums.org/showthread.php?t=1423278")

To see the full name of the device (Serial Wacom Tablet) use:
```
jet@jetpad:~$ xsetwacom --list --verbose
... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device 'Power Button' (6).
... Found device 'Video Bus' (7).
... Found device 'Power Button' (8).
... Found device 'AT Translated Set 2 keyboard' (9).
... Found device 'Serial Wacom Tablet eraser' (10).
Serial Wacom Tablet eraser ERASER    
... Found device 'Serial Wacom Tablet stylus' (11).
Serial Wacom Tablet stylus STYLUS    
... Found device 'Jing-Mold USB K/B+Mouse' (12).
... Found device 'Jing-Mold USB K/B+Mouse' (13).

```

Where the device name is "Serial Wacom Tablet stylus" with the associated number (11), though this number may change at boot so it is not good to reference to in the rotate.sh script.

Now there may be a better way of doing this, but so far this seems to work. Hope it helps.

Now to get Unity to behave properly, but that is for another time and another thread. But if anyone has any tips, please point me in the correct direction.

---

