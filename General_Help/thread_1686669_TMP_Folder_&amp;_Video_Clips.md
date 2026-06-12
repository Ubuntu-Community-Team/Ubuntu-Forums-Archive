---
title: "TMP Folder &amp; Video Clips"
date: 2011-02-12
forum: General Help
---

### Post by BruisedQuasar07 on 2011-02-12
Do not know if this is connected but I downloaded and installed updates recently (Ubuntu 10.10) and had a few things went wrong. 

First, I could no longer shrink windows to bottom panel (a weird one I never ran across before!). When I clicked on the minus symbol Firefox and other windows would just shut down. I figured out that one. I found something had been turned off in panel menu. Now I discovered another strange one.

This one really lessens Ubuntu's usefulness. 

I go into tmp folder and move instructional & finance news streams & clips before they disappear so I can keep them. I do this with YouTube instructional clips quite a lot and other handy clips I find, A handy feature about Linux that does not exist in MS Windows. I could save any video or audio stream this way. Never had a problem doing this with any Linux distro.

Suddenly, I find no clip icons in the tmp folder, not even the empty looking ones that you see immediately when a stream begins, or junk advertising clips that auto d/l when I am on certain financial sites.

Anybody have any ideas about what happened or how I can get streams and such to download into tmp again? This was a simple, fast way for me to save streams. I know about utilities and programs for saving streams. I prefer to move the tmp ones. Very simple, fast.

--Bruised

---

### Post by fmdex2011 on 2011-02-12
The location for flash files has changed

In Nautilus, click on View, then select Show Hidden Files,

then go to :

/home/yourlogin/.mozilla/firefox/xxxxxxxx.default/Cache

xxxxxxxx represents an 8 digit random string that your computer generates

Make sure you increase your cache size in Firefox to fit whatever you are watching, otherwise the file will vaporize after the download is complete. 

The default size is 50MB, I changed mine to 300MB to be safe. 

In Firefox click Edit, Preferences, Advanced, and the Network tab, use the Offline Storage spinner

Also, the files will stay in the Cache if you move to another web page, so make sure you have enough space

By the way. divx, xvid and avi files still go to /tmp/ 

Hope this helps     :)

---

### Post by chetancrasta on 2011-02-24
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by trimi on 2011-03-08
I tried to change the Offline Storage, and it goes up to 99 MB!! Why is it not going higher??

---

### Post by Marzata on 2011-03-09
Any way with the newest version of Adobe Flash to have the flash files in /tmp?

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

### Post by Broker on 2011-07-27
Thanks a lot Chetancrasta.:D
Script work fine. 
I have install Flash Player 11 beta in 64bit Ubuntu 10.04.3.
Video is in home folder.

Best Regards, Broker

---

