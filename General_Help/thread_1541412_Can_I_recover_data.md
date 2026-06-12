---
title: "Can I recover data"
date: 2010-07-29
forum: General Help
---

### Post by Bertus_Nel on 2010-07-29
Hi Guys

I've been searching for a known working solution to my frustration.

Scenario:

I have a laptop that had Windows XP on it - XP crashed out and I couldnt retrieve my data of it, despite booting up in safe mode, it just didnt want to do anything. So i thought i will load ubuntu instead then try and recover my data - bad move. Now my question is, can I still retrieve the windows data of the hard drive despite having Ubuntu installed on the same drive? I know on windows there is an app called File Scavenger that recovers deleted files even after loading a clean slate of Windows on it. Is there something like that for Linux? I had photos on it that has some real sentimental value. The rest of the data I dont care about. Just the photos.

I didnt think before I reloaded it. :oops:

Does anyone know what I can do?

Any Help will be highly appreciated.

---

### Post by HermanAB on 2010-07-29
Howdy,

Relax and enjoy your feshly formatted, nice, new, squeaky clean system...

---

### Post by aeiah on 2010-07-29
its unlikely, but you can try.

first, stop using the hard drive you've ruined. run a livecd / usb of ubuntu and use photorec to try and recover your files. 

in future if something like this happens the general process is:
[LIST=1]
[*]stop using the hdd right away
[*]access the hdd via a livecd so you dont write any more data to it
[*]if the drive appears to have mechanical failure or corruption try to take a bit-for-bit copy using dd
[*]use this copy (or original if need be) with photorec and other tools to try to recover your data
[/LIST]

but really the best option is to make regular backups, either online or on another storage medium. i have 3 hdds in my desktop: one for the operating system, one for storage, and one for backups of important stuff. backups are done daily using backintime. if my operating system messes up, all my data is still safe, and only if two drives fail do i lose important stuff like photos and documents

---

### Post by Bertus_Nel on 2010-07-29
Thanks for your input, yeah I made a bad mistake man. And i knew I had to backup the data up. 

I will boot from a live cd now and try photorec, hopefully i can salvage some of the files.

Herman

I do enjoy the new clean system, but hey - **** happens I suppose... ;-)

---

### Post by aeiah on 2010-07-29
hey, ive been using ubuntu since 2005 and 6 months ago i managed to format the wrong partition and lost some data. always be vigilant whilst installing operating systems :p

---

### Post by Bertus_Nel on 2010-07-29
Yip, already bought an external that will serve the purpose as my backup drive - Now I can say been there done that, got the badge (from the wife) :D

Thanks for your help man, much appreciated.

---

### Post by aeiah on 2010-07-29
take a look at [backintime](http://backintime.le-web.org)

its easy to set up and will do snapshot backups, allowing you to go back in time to a specific data set, but because of the way it copies things (hard linking), it only copies changes to reduce filesize and copy time.

its available in synaptic

---

### Post by dino99 on 2010-07-29
use these tools: [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

