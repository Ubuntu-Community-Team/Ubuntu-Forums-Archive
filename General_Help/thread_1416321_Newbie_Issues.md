---
title: "Newbie Issues"
date: 2010-02-25
forum: General Help
---

### Post by rickreation on 2010-02-25
hello all, 
I have been wanting to use Ubuntu for some time and have started running it. I have the following problems:

1) Ubuntu is unable to gain access to my wireless card, so I can't configure it to connect to my router

2) No sound

3) My speedtests in Windows 7 are typically 15-25 mbps. In Ubuntu 9.10 I'm barely getting .7mbps.

I am hoping these are all basic issues, but I know very little and have had trouble finding the answers from my own searching.

Thanks in advance for the help!

Rick

---

### Post by Ozymandias_117 on 2010-02-25
1. You can usually install drivers for wireless cards through System -> Administration -> Hardware Drivers

2. Not sure, sorry

3. My guess would be it's just because most speedtest sites I've seen use something like Java or Flash, which do still run better in windows. Real world results should be the same on either operating system.

---

### Post by MooPi on 2010-02-25
Let's start with finding out what your hardware is.
open a terminal and type ```
sudo lshw>hardware
``` ```
lsmod>drivers
```These will deposit a text file in your home directory listing hardware & drivers. Copy and paste the contents of the files here.

---

### Post by sinurge on 2010-02-25
> **rickreation said:**
> hello all, 
I have been wanting to use Ubuntu for some time and have started running it. I have the following problems:

1) Ubuntu is unable to gain access to my wireless card, so I can't configure it to connect to my router

2) No sound

3) My speedtests in Windows 7 are typically 15-25 mbps. In Ubuntu 9.10 I'm barely getting .7mbps.

I am hoping these are all basic issues, but I know very little and have had trouble finding the answers from my own searching.

Thanks in advance for the help!

Rick
on 2 - you might want to read [http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)

---

### Post by Ozymandias_117 on 2010-02-25
One thing for 3... I assume you've already installed the ubuntu-restricted-extras package (I don't THINK speedtest will work without it, but it might) If it's NOT installed, that would be a huge reason for speedtest to be slow ;) (Command to get it if you don't have it is "sudo apt-get install ubuntu-restricted-extras" - If it says something about no package found, run "sudo apt-get update" then repeat the first command)

---

