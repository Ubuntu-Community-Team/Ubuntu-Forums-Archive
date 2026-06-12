---
title: "Upgrade Firefox 3.0.13 to v. 3.5 ?"
date: 2009-09-02
forum: General Help
---

### Post by JEBB on 2009-09-02
Ubuntu 9.04 UNR on Dell Mini 9

The Firefox version from the repository is 3.0.13.  I would like to upgrade it to version 3.5 but the "Check for Updates" command in the Help menu is disabled (grayed out).  How can I get around that roadblock?  Thanks.

---

### Post by ryanfx on 2009-09-02
simple google search...

[http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm](http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm)

---

### Post by lovinglinux on 2009-09-03
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by scouser73 on 2009-09-03
Hi, I've used the instructions in this tutorial: [[COLOR="Red"]**Install Firefox 3.5**[/COLOR]]("http://www.ihackintosh.com/2009/07/install-firefox-35-ubuntu-linux/")

I used the second method to install Firefox 3.5.

---

### Post by lovinglinux on 2009-09-03
> **scouser73 said:**
> Hi, I've used the instructions in this tutorial: [[COLOR="Red"]**Install Firefox 3.5**[/COLOR]]("http://www.ihackintosh.com/2009/07/install-firefox-35-ubuntu-linux/")

I used the second method to install Firefox 3.5.

I don't recommend method 1 from that tutorial, which is the same as method 3 of my tutorial, because the ubuntu-mozilla-daily repository will update too often, including unstable development releases.

---

### Post by JEBB on 2009-09-03
Although I had done Google search, I worded it differently and did not get the same results as did ryanfx.  Anyway, I followed the directions at the link he gave needing, I thought, only step 3 since I already had 3.0.13 on my DM9.  What I got was Shiretoko browser which shows up as Firefox 3.5.2 in Help>About Shiretoko.  That's fine.  

A lot of files were downloaded so I looked under Synaptic, search term firefox.  There are a number of seemingly redundant files labled the same except for the version number.  

Question:  can I delete those duplicates that are NOT version 3.5 or 3.5.2?

---

### Post by TechVamp on 2009-09-03
Ubuntuzilla works great!!

use that!

---

### Post by bodhi.zazen on 2009-09-03
> **scouser73 said:**
> Hi, I've used the instructions in this tutorial: [[COLOR=Red]**Install Firefox 3.5**[/COLOR]]("http://www.ihackintosh.com/2009/07/install-firefox-35-ubuntu-linux/")

I used the second method to install Firefox 3.5.

+1, simply download the tar from Mozilla.

If you wish it to be available for all users put it in /usr/local

---

