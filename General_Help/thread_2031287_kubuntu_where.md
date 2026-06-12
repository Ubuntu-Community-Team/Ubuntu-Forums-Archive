---
title: "kubuntu: where?"
date: 2012-07-21
forum: General Help
---

### Post by icegood on 2012-07-21
wubi fails to install kubuntu:
```

07-21 23:38 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/kubuntu/daily-live/current/precise-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found


```

---

### Post by WorMzy on 2012-07-21
I guess you have an out of date version of the Wubi installer, or Wubi itself is out of date. [The current daily images are of 12.10 (Quantal Quetzal)]("http://http://cdimage.ubuntu.com/kubuntu/daily-live/current/")

---

### Post by bcbc on 2012-07-21
It's a bug: [https://bugs.launchpad.net/wubi/+bug/1004173](https://bugs.launchpad.net/wubi/+bug/1004173)

You have to download the ISO yourself to install - workaround here: [http://askubuntu.com/q/163666/14916](http://askubuntu.com/q/163666/14916)

Wubi always tries the dev release after the prod release fails (so it runs during development). That last line that you copied is the dev release of 12.04 failing but the actual error is that it couldn't find the prod release because they coded in the wrong path for kubuntu. It's a few lines up from the one you copied.

---

### Post by robtygart on 2012-07-21
> **icegood said:**
> wubi fails to install kubuntu:
```

07-21 23:38 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/kubuntu/daily-live/current/precise-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found


```


Installing Kubuntu from an ISO is very easy, I don't know about Windows 7, but when I had Vista all I had to do is download the ISO and then click it, and it opened up my Burning software, then I cliked "burn", then restart.

---

