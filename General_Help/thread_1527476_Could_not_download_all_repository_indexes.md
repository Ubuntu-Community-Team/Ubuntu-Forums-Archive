---
title: "Could not download all repository indexes?"
date: 2010-07-09
forum: General Help
---

### Post by squidpotion on 2010-07-09
So earlier today Ubuntu automatically updated and later on I got this icon in my panel saying the update information was outdated. So I tried updating again and it said "Failed to fetch [http://ppa.launchpad.net/acheck/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/acheck/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz) 404 Not Found." 

Anyone have any idea what to do about this? I recently installed gstreamer-plugins-ugly-multiverse to get rhythmbox ripping into mp3, could that have anything to do with it? I'm pretty new to Ubuntu/Linux. Thanks in advance!

---

### Post by birkopf on 2010-07-09
> **squidpotion said:**
> So earlier today Ubuntu automatically updated and later on I got this icon in my panel saying the update information was outdated. So I tried updating again and it said "Failed to fetch [http://ppa.launchpad.net/acheck/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/acheck/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz) 404 Not Found." 

Anyone have any idea what to do about this? I recently installed gstreamer-plugins-ugly-multiverse to get rhythmbox ripping into mp3, could that have anything to do with it? I'm pretty new to Ubuntu/Linux. Thanks in advance!

Installing "ugly" wouldn't do anything to it. If you didn't changed recently anything in /etc/apt/sources.list and didn't changed anything in System -> Administration -> Software Sources
all should be fine. Sometimes repo's are not available (usually few minutes when server gets slow) 

Wait day or two and in Terminal enter:

sudo apt-get update

If everything will be fine - temporary problem on server side. If not - send error code.

---

### Post by squidpotion on 2010-07-11
Alright, well it still won't update. I'm assuming the error code is all the stuff in the Terminal after I try to run update? If not, let me know.

---

### Post by squidpotion on 2010-07-14
Bump.

I did a system update earlier today (finally), but it's STILL giving me the same thing. Same icon in the panel, same pop-up. Here's a screenshot of what happens when I try to update, if that helps. 

[[IMG]http://a.imageshack.us/img96/4455/screenshotkw.png[/IMG]]("http://img96.imageshack.us/i/screenshotkw.png/")

---

### Post by philinux on 2010-07-14
> **squidpotion said:**
> Failed to fetch [http://ppa.launchpad.net/acheck/ppa/...64/Packages.gz](http://ppa.launchpad.net/acheck/ppa/...64/Packages.gz)  404 Not Found.

It looks like that ppa gone bye bye. I suggest you remove it from your sources list.
[https://launchpad.net/ubuntu/+ppas?name_filter=acheck&show_inactive=on](https://launchpad.net/ubuntu/+ppas?name_filter=acheck&show_inactive=on)

---

