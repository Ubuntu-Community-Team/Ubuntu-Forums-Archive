---
title: "Firefox 8 Memory"
date: 2011-12-21
forum: General Help
---

### Post by SipSomeSalt on 2011-12-21
Yo -- my firefox keeps crashing. I've only got 512MB of RAM and firefox alone using one flash video maxes me out at like 95 MB of RAM. Can I lower this, or should I just downgrade my firefox?

---

### Post by SipSomeSalt on 2011-12-21
[IMG]http://img269.imageshack.us/img269/81/screenshotsystemmonitors.png[/IMG]

---

### Post by lovinglinux on 2011-12-21
On YouTube, a 360p video is using about 30Mb on my 32bit system, while a 1080p is using 70 Mb. Unless you are on a 64bit using fullscreen mode, I think 100Mb is a little bit excessive for the plugin container.

Please check how much ram the plugin container uses while viewing [http://www.youtube.com/watch?v=HomAZcKm3Jo](http://www.youtube.com/watch?v=HomAZcKm3Jo) in different resolutions.

---

### Post by SipSomeSalt on 2011-12-21
[IMG]http://img696.imageshack.us/img696/6966/screenshotsystemmonitorn.png[/IMG]

360

[IMG]http://img85.imageshack.us/img85/2558/screenshotsystemmonitort.png[/IMG]

1080

The flash video I was watching on the first thing was a 40 minute episode of True Life so that kinda makes sense. I just wanna limit the amount of RAM Firefox uses -- it's KILLING me.

---

### Post by lovinglinux on 2011-12-21
You should consider a lighter distro like Lubuntu or Xubuntu.

---

### Post by SipSomeSalt on 2011-12-21
Are you pooping me? That's how I combat this? I lose everything I've got because firefox 8 is huge? Good Answer......

Next!

---

### Post by lovinglinux on 2011-12-22
> **SipSomeSalt said:**
> Are you pooping me? That's how I combat this? I lose everything I've got because firefox 8 is huge? Good Answer......

Next!

Well, there is nothing wrong with your Firefox. 

You can install xubuntu and lubuntu without replacing your current installation.

To install lubuntu from terminal:

```
sudo apt-get install lubuntu-desktop
```


To install xubuntu from terminal:

```
sudo apt-get install xubuntu-desktop
```

If you do install and doesn't like it, then you can revert to Ubuntu only following [these instructions](http://www.psychocats.net/ubuntu/puregnome).

---

### Post by holycow131415 on 2011-12-22
Or try lighter browsers like chromium, seamonkey, etc.
Or upgrade your ram for like 40 bucks.

---

### Post by Ms. Daisy on 2011-12-22
> **holycow131415 said:**
> or upgrade your ram for like 40 bucks.
+1

---

### Post by SipSomeSalt on 2011-12-23
Yo -- I wanna downgrade to 3.65 but I downloaded a tar.bz2 file. I extracted the file, but how do I move it to usr/local? I don't have the file permissions, and su won't allow me to use my password.

---

### Post by guyver_dio on 2011-12-23
I don't think downgrading firefox will make that much of a difference. Either get more memory or install lubuntu desktop, it's made for low spec machines.

---

### Post by dcstar on 2011-12-23
My Firefox 9.01 is currently using 238.2 MiB!!!!

It is getting a bit bloated in the ever increasing speed war with the other browsers......

---

### Post by Vaphell on 2011-12-23
Recent benchmarks show it is actually the leanest of the pack in most cases if you measure memory use. Besides you seriously underestimate the complexity of a modern browser (that doesn't come free) and the bloat of modern webpages full of flash objects and craptons of javascript.
Look at **about:memory** to see where the memory goes. My adblocked facebook with empty wall sits at ~30MB alone. Youtube main page - another 10MB. Back button working in an instant - previos pages cached in memory N megs a pop. All that does add up.

Maybe try running adblock and noscript to get rid of all the unnecessary crap that bogs the browser down (flash ads, 3rd party tracking/datamining/ad-loading scripts). You could also investigate settings responsible for caching in **about:config** page.

When you have 512MiB and 300 goes to the desktop alone you don't have enough headroom to realistically expect smooth browsing without heavy tweaking.

---

### Post by lovinglinux on 2011-12-23
> **dcstar said:**
> My Firefox 9.01 is currently using 238.2 MiB!!!!

It is getting a bit bloated in the ever increasing speed war with the other browsers......

I have just tested several versions of Firefox and the latest version of Chrome and Opera to see how much memory the use with a clean profile on startup. See the comparison:

Chrome 16 - 59Mb
Opera 11.6 - 38Mb

Firefox 3.0.19 - 30Mb
Firefox 3.5.19 - 29Mb
Firefox 3.6.25 - 29Mb
Firefox 4 - 39Mb
Firefox 5 - 37Mb
Firefox 6 - 38Mb
Firefox 7 - 36Mb
Firefox 8 - 37Mb
Firefox 9 - 37Mb
Firefox 10 - 38Mb
Firefox 11 - 36Mb
Firefox 12 - 36Mb

All browsers were started with only Google page open and they were giving a few seconds for the memory value stop fluctuating. If the about:home page were used instead of Google, the values would be lower. However, due to the inconsistency in the about:home page across different versions of the same browser and different browsers, Google page was chosen instead. 

My Firefox starts at 220Mb, but that is due to the fact that I have about 60 extensions installed and I save my cache on memory instead of the disk.

Chrome with 22 extensions goes to 512Mb of RAM used. To calculate this value, I have considered all chrome separate process in the System Monitor. I am not sure if this is accurate, since Chrome *about:memory* shows 260Mb.

> **Vaphell said:**
> Recent benchmarks show it is actually the leanest of the pack in most cases if you measure memory use. Besides you seriously underestimate the complexity of a modern browser (that doesn't come free) and the bloat of modern webpages full of flash objects and craptons of javascript.
Look at **about:memory** to see where the memory goes. My adblocked facebook with empty wall sits at ~30MB alone. Youtube main page - another 10MB. Back button working in an instant - previos pages cached in memory N megs a pop. All that does add up.

Maybe try running adblock and noscript to get rid of all the unnecessary crap that bogs the browser down (flash ads, 3rd party tracking/datamining/ad-loading scripts). You could also investigate settings responsible for caching in **about:config** page.

When you have 512MiB and 300 goes to the desktop alone you don't have enough headroom to realistically expect smooth browsing without heavy tweaking.

+1

Edit a Wordpress blog for a while to see how your memory goes up.

---

### Post by whatthefunk on 2011-12-23
Try Opera.  Its the fastest on my machine which is also low on memory.

Lubuntu would really, really speed up your computer as a whole...

---

### Post by lovinglinux on 2011-12-23
This discussion inspired me to create a browser memory analysis thread:

[http://ubuntuforums.org/showthread.php?t=1899304](http://ubuntuforums.org/showthread.php?t=1899304)

---

### Post by vasa1 on 2011-12-23
> **lovinglinux said:**
> ... I save my cache on memory instead of the disk.
...

Please could you provide more details on how you do this? :)

---

### Post by lovinglinux on 2011-12-23
> **vasa1 said:**
> Please could you provide more details on how you do this? :)

[http://www.webgapps.org/tutorials/firefox/optimization/ramdisk-cache](http://www.webgapps.org/tutorials/firefox/optimization/ramdisk-cache)

---

