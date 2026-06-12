---
title: "How do I increase my maximum amount of allowed shared memory?"
date: 2011-05-17
forum: General Help
---

### Post by Maheriano on 2011-05-17
My problem is I installed Zone Minder for camera security and I'm testing it on my laptop with the built in webcam and everything seems to work perfectly except when I try to view the live feed from the camera, it's just a black box. No video.

I checked [this]("http://kirichkov.com/tag/zoneminder/") website and it's exactly the problem I'm having with a fix for it but his fix doesn't work. He says to type:
```
user@ubuntu:~$ sudo echo "256000000" > /proc/sys/kernel/shmmax
user@ubuntu:~$ sudo service apache2 restart
user@ubuntu:~$ sudo service zoneminder restart
```
But when I do the first line, I get this:
```
deemar@Clementine:~$ sudo echo "256000000" > /proc/sys/kernel/shmmax
bash: /proc/sys/kernel/shmmax: Permission denied

```

---

### Post by wojox on 2011-05-17
In order to add the change permanently you’ll need to edit /etc/sysctl.conf and add a line kernel.shmmax = 256000000 to it.

---

### Post by Maheriano on 2011-05-17
I actually got it working, I had to change the video output from gray, which I thought would be a safe debug setting and change it to YUYV which is the correct colour encoding for the webcam according to some command that probes the video device.

---

