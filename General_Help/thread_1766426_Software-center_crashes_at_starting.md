---
title: "Software-center crashes at starting"
date: 2011-05-24
forum: General Help
---

### Post by NattyMeerkat on 2011-05-24
I installed Audacity, the Software-Center downloaded and installed it, but it crashed.
Now it crashes every time I try to start it.:
```
user@ubuntu:~$ software-center
/usr/share/software-center/softwarecenter/app.py:1192: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-05-24 17:17:08,419 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-05-24 17:17:08,418 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
2011-05-24 17:17:08,791 - softwarecenter.app - INFO - software-center-agent finished with status 0
segmentation fault

```I tried to start synaptic, but it show only:
```
user@ubuntu:~$ synaptic
segmentation fault
```I restarted the computer and everything.

calling apt-get install -f:
```
user@ubuntu:~$ sudo apt-get install -f
Paketlisten werden gelesen... Fertig //=reading package lists... Done
user@ubuntu:~$ rd aufgebaut... 50% //~= ng build... 50% (I think from "dependance tree is being build" or something like that
```Thanks for your support.

---

### Post by NattyMeerkat on 2011-05-28
Hello?

---

### Post by linuxinstalledfromhdd on 2011-05-28
What changes did you make to your system prior to this happening?  Anything specific? Did you add a PPA repository?  Did you enable something from within Synaptic? Did you change your source.list file recently?  Did you upgrade to 11.04 or is this a fresh installation?

---

### Post by Remi76 on 2011-06-02
Same here,

I'm new to Linux and used Ubuntu (10.10.10) for a starting point, I immediate upgraded to 11.04 and began installing software. After installing Thunderbird I got this:

```

user@ubuntu:~$ software-center
/usr/share/software-center/softwarecenter/app.py:1192: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-05-30 16:47:53,177 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-05-30 16:47:53,176 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
Segmentatiefout
user@ubuntu0:~$ 

```I scrapped the install an began with a clean version of 10.10.10 and it worked just fine until I tried to install a moonlight (silverlight) package
while doing that I got the segfault again


My immediate thought was to de-install, but how? 


PS: I already asked this in the Dutch forum 
[http://forum.ubuntu-nl.org/software-en-configuratie/probleem-installeren-van-software/msg735601/#msg735601](http://forum.ubuntu-nl.org/software-en-configuratie/probleem-installeren-van-software/msg735601/#msg735601)

---

### Post by Remi76 on 2011-06-02
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219)

---

### Post by sealong on 2011-06-10
sudo rm /var/cache/apt/*.bin

---

### Post by cybercookie72 on 2011-06-12
@sealong I used a modified version of what you showed us to make sure it works...I added -r recursive and -f force :) just to make sure .... thanks for the post

sudo rm -rf /var/cache/apt/*.bin

---

### Post by Remi76 on 2011-06-12
Sorry I forgot to post I found the solution.

```

sudo apt-get update && sudo apt-get upgrade

```

---

