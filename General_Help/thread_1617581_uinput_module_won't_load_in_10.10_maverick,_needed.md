---
title: "uinput module won't load in 10.10 maverick, needed for thinkfinger"
date: 2010-11-09
forum: General Help
---

### Post by thebigkevdogg on 2010-11-09
Hi All,

I just upgraded my lenovo T61p to ubuntu 10.10 maverick. I use the thinkfinger package to use my fingerprint reader for sudo/login/screen unlocking. This has worked perfectly in previous ubuntu releases, but I can only get it to work for login, not sudo or locked screen.

I think the problem has to do with uinput not loading. I have it in /etc/modules, but it still doesn't show up (I also manually load it with modprobe and it won't work):

```
kevin@milner:~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

uinput
lp
rtc
kevin@milner:~$ lsmod | grep uinput
kevin@milner:~$ sudo modprobe uinput
kevin@milner:~$ lsmod | grep uinput
kevin@milner:~$
```

Any ideas? This is a 64 bit install.

Thanks,
Kevin

---

### Post by thebigkevdogg on 2010-11-10
(bump) any ideas? should this question be somewhere else?

---

### Post by ulidtko on 2010-12-10
If you have file /dev/uinput, then the driver is loaded and working.

```
crw-r----- 1 root root 10, 223 2010-12-04 09:32 /dev/uinput

```

---

### Post by beejee on 2010-12-17
Hi,

I have the same problem, need to load uinput for the G15Daemon.

When i do 
   $ sudo modprobe -v uinput
   $
there is no response. 
lsmod shows no uinput module loaded

   $ ls -l /dev/uinput
   crw-r----- 1 root root 10, 223 2010-12-17 13:22 /dev/uinput
and 
   $ sudo cat uinput
   cat: uinput: No such device

Any idea where to look for more info?
Thanks.

---

### Post by dddw on 2010-12-22
I can confirm this issue on 32 bits as well
Wiican doesnt run uinput automatically (as it should)
wminput however does force it to become active generally (but even now and then fails at it too)
also see:
[https://bugs.launchpad.net/wiican/+bug/667582](https://bugs.launchpad.net/wiican/+bug/667582)

---

### Post by penkoad on 2010-12-31
Hi,

Same here with my T61 (lenovo) use to work fine with previous version of Ubuntu but Maverick appears to have brought a regression

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/609645](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/609645)

There a sudo patch in the way but so far it has not reach the repositories.

---

### Post by SuperElitist on 2011-01-09
I am suffering the same problem - unable to start uinput via **/etc/modules** or **sudo modprobe uinput**. modprobe gives no error message, which implies it is maybe starting, but since **lsmod** does not show it running, it is possibly stopping right away?

It seems that this is a problem for a number of applications, i.e. thinkfinger, wiicast, g15daemon...

Is there a bug posted for the root cause? I have only seen bugs posted for the various applications it seems to affect.

Also, is there a way we can get more information about uinput starting, maybe a verbose mode or something?

---

### Post by malluen on 2011-02-22
I've been having the same problem with uinput not loading on startup with xbmclive dharma. 

It's hackish but I added a shell script to init to load it via modprobe. It works =)

---

### Post by Desyth on 2011-02-24
Running into this issue on Maverick x64 as well.  What did you do to get it to load, malluen?

---

### Post by modul8 on 2011-05-21
Did anyone ever figure this out?
I am having the same problem with Natty x64.
I have used Karmic and Lucid (both 32bit) with no issues on the same hardware but with Natty uinput just doesn't seem to load. I get no errors.

I have /dev/uinput but my PS3 bluetooth remote will not work. I can pair but without uinput I get no control.

---

### Post by ZenFire on 2011-07-03
Still no news on this? I am having the same issue on my Maverick 64 bit machine, doesn't show up in lsmod and sudo modprobe uinput does nothing...

Would really like to get my PS3 remote working but without uinput that is not happening.

---

### Post by Halsafar on 2011-11-26
Same problem here.  UBuntu 11.10

---

### Post by missingno on 2011-12-27
Same issue in 11.10 on my Lenovo Y570. Can't get Wiican to work without it, and a search brought me to an updated build that's supposed to fix this issue but didn't. Anyone know what's going on?

---

### Post by kentoe on 2012-03-24
Same problem here with my ubuntu 10.10, I need it for xbxdrv in using my 360 controller with ubuntu. Nothing for uinput and joydev in /dev/input or /dev/

Can't load uinput or joydev from /etc/modules on start up.

lsmod shows neither of them available

"sudo modprobe uinput" doesn't load anything and results in an error

Nobody has found a solution? There's nothing I can find online about these problems

---

### Post by bobbaluba on 2012-05-13
same problem here on 12.04, I'm trying to connect a wiimote. I read somewhere that uinput is now compiled into the kernel, and that's why it doesn't show up on lsmod. You have to be root to access uinput, though, and that's kind of problematic.

---

### Post by oldos2er on 2012-05-13
Old thread closed. Please start a new thread for your question.

---

