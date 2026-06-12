---
title: "Sound system settings not preserved after reboot"
date: 2012-04-01
forum: General Help
---

### Post by susja on 2012-04-01
Hello,
I'm using Ubuntu 11.10. My PC does not have microphone and I have external Logitech camera with built-in mic. I use it all the time when use Skype. To change the input I modify it in System Settings -> Sound -> and then in Hardware and Input tab select my mic. It works fine until I restart system. Every time after restart I have to repeat this procedure.
Could someone please help me to make the change permanent?
Thanks in advance.

---

### Post by matt_symes on 2012-04-02
Hi

Can you post the output of

```
ls -l ~/.pulse/*
```

That's a small L after ls. Can you also post the output of

```
cat /etc/asound.conf ~/.asoundrc
```

It's very possible you will not have the last two files though.

Kind regards

---

### Post by susja on 2012-04-02
thanks for reply.
Here's the output:
eliya@Linda:~$ ls -l ~/.pulse/*
-rw-r--r-- 1 eliya eliya   696 2012-02-24 12:22 /home/eliya/.pulse/810179e92fe70791092f30e80000000c-card-database.tdb
-rw-r--r-- 1 eliya eliya    43 2012-04-01 12:35 /home/eliya/.pulse/810179e92fe70791092f30e80000000c-default-sink
-rw-r--r-- 1 eliya eliya    61 2012-04-01 12:35 /home/eliya/.pulse/810179e92fe70791092f30e80000000c-default-source
-rw-r--r-- 1 eliya eliya 12288 2012-04-01 12:45 /home/eliya/.pulse/810179e92fe70791092f30e80000000c-device-volumes.tdb
lrwxrwxrwx 1 eliya eliya    23 2012-03-31 21:42 /home/eliya/.pulse/810179e92fe70791092f30e80000000c-runtime -> /tmp/pulse-ox0EndaxrydT
-rw-r--r-- 1 eliya eliya 12288 2012-04-01 12:35 /home/eliya/.pulse/810179e92fe70791092f30e80000000c-stream-volumes.tdb
eliya@Linda:~$ 
**
eliya@Linda:~$ cat /etc/asound.conf ~/.asoundrc
cat: /etc/asound.conf: No such file or directory
cat: /home/eliya/.asoundrc: No such file or directory
eliya@Linda:~$

---

### Post by matt_symes on 2012-04-05
Hi

Sorry for the late reply.

Try the fixes in this thread.

[http://ubuntuforums.org/showthread.php?t=1784771](http://ubuntuforums.org/showthread.php?t=1784771)

Also, have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

Can you also post the output of

```
cat /home/eliya/.pulse/810179e92fe70791092f30e80000000c-default-source
```

Do this twice. 

1. After a reboot and before setting the new audio input device to the webcam
2. After setting the audio input device to the webcam.

Kind regards

---

### Post by susja on 2012-04-05
> **matt_symes said:**
> Hi

Sorry for the late reply.

Try the fixes in this thread.

[http://ubuntuforums.org/showthread.php?t=1784771](http://ubuntuforums.org/showthread.php?t=1784771)

Also, have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

Can you also post the output of

```
cat /home/eliya/.pulse/810179e92fe70791092f30e80000000c-default-source
```Do this twice. 

1. After a reboot and before setting the new audio input device to the webcam
2. After setting the audio input device to the webcam.

Kind regards
hi matt_symes
thanks for your reply,
I was reading first thread you pointed and before doing any modifications I realized that one of the files mentioned there does not exist on my system i.e. "No help? Comment out line 372 in /etc/init.d/alsa-utils"
Not sure how it'll affect my changes but I'll try it anyway later and let you know.
Meanwhile here's the output you requested:
eliya@Linda:~$ cat /home/eliya/.pulse/810179e92fe70791092f30e80000000c-default-source
alsa_input.pci-0000_00_1b.0.analog-stereo
eliya@Linda:~$
Thanks again and appreciate your help

---

### Post by Adrian98 on 2012-04-05
> **matt_symes said:**
> Hi

Sorry for the late reply.

Try the fixes in this thread.

[http://ubuntuforums.org/showthread.php?t=1784771](http://ubuntuforums.org/showthread.php?t=1784771)

Also, have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

Can you also post the output of

```
cat /home/eliya/.pulse/810179e92fe70791092f30e80000000c-default-source
```

Do this twice. 

1. After a reboot and before setting the new audio input device to the webcam
2. After setting the audio input device to the webcam.

Kind regards


That helped me well. In my system the sound system was not working at all but now its working well!! Thanks

---

### Post by matt_symes on 2012-04-05
Hi

From the terminal, please post the output of

```
lspci -s 00:1B.0
```

and 

```
lsusb
```

and 

```
aplay -l
```

That is a small L after aplay.

Can you also post the output of

```
cat /home/eliya/.pulse/810179e92fe70791092f30e80000000c-default-source
```

after you have changed the audio input to the webcam.

Kind regards

---

