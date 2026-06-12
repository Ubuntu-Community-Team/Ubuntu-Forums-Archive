---
title: "xboxdrv or xboxdrv-daemon autostart"
date: 2010-08-19
forum: General Help
---

### Post by frostypepper on 2010-08-19
I have downloaded and compiled the xboxdriver from Grumbels git hub. Running 9.10 minimal with xbmc 9.11.

I can run the driver manually and actually run multiple instances of the driver for multiple controllers. I cannot however get more than one instance of the driver to start up at boot.

I have the freshly compiled driver and daemon that came with source files in /usr/local/bin.

I can run the driver via 'sudo /usr/local/bin/xboxdrv --wid0', I can even get a second wireless controller working with 'sudo /usr/local/bin/xboxdrv --wid1'

When I add the driver to /etc/rc.local it runs fine on startup. The problem is I want more than one instance running. When I add the exact same line right under it except change the  wid0 to wid1 it will not automaticly run the second driver.

I also can get zero activity from the daemon. I have tried adding it to the rc.local, or /etc/init.d/local (I think someone mentioned it somewhere) with no luck.

I am not quite sure what I am doing wrong. My ultimate goal is to have 2 minimum to 4 maximum controllers work from startup. I want to add emulators to a xbmc htpc and just dont want to have to worry about manually starting drivers. I have forgone using xpad due to its somewhat limited support for wireless xbox360 controllers.

Thanks for the help!

---

### Post by frostypepper on 2010-08-20
Anyone?

---

### Post by frostypepper on 2010-08-20
So I thought perhaps its booting up too fast to call the second driver startup. I added /usr/local/bin/xboxdrv --wid 0 && /usr/local/bin/xboxdrv --wid 1 with no luck.

I also added 
/usr/local/bin/xboxdrv --wid 0
sleep 60
/usr/local/bin/xboxdrv --wid 1

again with no luck.

---

### Post by frostypepper on 2010-08-21
bump

---

### Post by Grumbel on 2010-08-22
Try:

```

/usr/local/bin/xboxdrv --wid 0 &
sleep 60
/usr/local/bin/xboxdrv --wid 1 &

```

The & is important, as it puts xboxdrv in the background and you probably don't need to sleep 60, one or two seconds should be enough.

---

### Post by frostypepper on 2010-08-23
Grumbel that did the trick. I was able to get 4 instances running. I completely forgot to add the '&'.

I most deffinately need the drives running, but do you think it better to use the daemon or just run them right at boot?

I cant seem to get the daemon to load. I am using the following in my /etc/rc.local to try and start the daemon.

```
/usr/local/bin/xboxdrv-daemon.py -v -x /usr/local/bin/xboxdrv -- --deadzone 12000 --dpad-as-button --trigger-as-zaxis -D &
```

Thanks for the help Grumbel, I really appreciate it.

---

