---
title: "Video unavailable"
date: 2012-09-29
forum: General Help
---

### Post by pwabrahams on 2012-09-29
On most news sites, when I attempt to play a video I get the message "This video is currently unavailable".  This happens with Firefox, Chrome, and Konqueror, so I doubt if it's a browser issue.  At the same time there are lots of videos that I am able to play, like the ones from YouTube.  Here's just one of the ones that gives me trouble: [http://www.politico.com/multimedia/video/2012/09/webb-hammers-romney-on-military.html]("http://www.politico.com/multimedia/video/2012/09/webb-hammers-romney-on-military.html").

It's not a matter of trying at the wrong time; I get this message consistently.

---

### Post by cogier on 2012-09-29
I tried your link and the video worked fine for me. Have you installed the Ubuntu-restricted-extras?

This is available from the Software Centre or you can enter the following in Terminal

**sudo apt-get install ubuntu-restricted-extras**

To add more good stuff check out [Medibuntu]("http://medibuntu.org/repository.php") Paste the code into Terminal.

---

### Post by robtygart on 2012-09-29
> **cogier said:**
> I tried your link and the video worked fine for me. Have you installed the Ubuntu-restricted-extras?

This is available from the Software Centre or you can enter the following in Terminal

**sudo apt-get install ubuntu-restricted-extras**

To add more good stuff check out [Medibuntu]("http://medibuntu.org/repository.php") Paste the code into Terminal.

It works for me too. 

Change that to Kubuntu restricted extras..

```
sudo apt-get install kubuntu-restricted-extras
```

---

### Post by pwabrahams on 2012-09-29
I thought I had already installed both restricted-extras packages, so I double-checked:
```
pwa@pwa-K60IJ:~/Documents$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for pwa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
pwa@pwa-K60IJ:~/Documents$ sudo apt-get install kubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

```
So whatever the problem is, it's not for lack of the right repositories.  But maybe there's a package in those repositories that isn't installed but should be.

The error code that shows up is VE_FMS_CONNECT_FAILED.  From what I can find out by researching that code, the problem is related to Flash -- and Flash under Kubuntu seems to be problematic.  I've tried several versions of Flash -- 64-bit, 32-bit, and Beta.  They all behave the same way.

---

### Post by pwabrahams on 2012-09-30
Apparently the VE_FMS_CONNECT_FAILED error appears in several browsers and several OS's, but not consistently.  Back in February Adobe acknolwledged that there was a problem in Flash and attempted to fix it, but the status of the fix or where it's propagated to are unclear.

Meanwhile I'd very much like to know what the difference is between systems that manifest the problem and systems that don't.

---

