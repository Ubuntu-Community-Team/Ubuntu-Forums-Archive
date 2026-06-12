---
title: "Install problem on my Toshiba Laptop"
date: 2010-10-20
forum: General Help
---

### Post by RickHatalski on 2010-10-20
Hello to all, I am a newbee and heard from my son how great UBUNTU is as coppared to windows. So I thaught I would give it a try on my older Toshiba A135 lap top.
It runs a Intel Celeron M 1.6 GHZ CPU, windows Vista, 1.5 GB Ram and 73 GB HDD
I dowm loaded UBUNTU ver 10.10 and created a CD. I tried to install the softweare to the lap top and it goes so far and quits. Last thing it reported that it was trying to do something with my real tec? I am guessing the soundcard? I have tried the install process at least 3 times now and it goes so far and stops everytime. If more data is needed I will try the install again and take note of the exact thing the install reported before it stoped the install. I may be doing something wrong. Please help with any suggesstions or helpfull coments..Thanks in advance....Rick

---

### Post by searchfgold6789 on 2010-10-20
You may have to try to make another CD if the problem persists after 2 tries. For my Xubuntu install I had to make 4 cd's before it finally worked.
Remember to burn the CD at the lowest speed possible. Trust me and hundreds of other Ubuntu installers, this will help!
You might also want to Checksum, see this [_[COLOR=Blue]guide[/COLOR]_]("http://www.codejacked.com/using-md5sum-to-validate-the-integrity-of-downloaded-files/") for how to do that.
If all else fails, and you still have Windows, you can try [_[COLOR=Blue]Wubi[/COLOR]_]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer").
Good luck,
 - search

---

### Post by dabl on 2010-10-20
> **RickHatalski said:**
> 

 I tried to install the softweare to the lap top and it goes so far and quits. 


Some Toshibas (like my NB205) have very aggressive power-saving firmware, and they "go to sleep" in the absence of keyboard or mouse I/O (or a Windows driver poking it periodically ...).  Try tapping the spacebar when it stops, or tickle the mousepad if it has one, and see if installation continues.  You might have to nurse it along all the way until it finishes.  The good news is, once you have a GUI desktop, is should be fine.

---

### Post by matsuzine on 2010-10-20
Here are a few links to other people who have been installing on the same hardware:

[http://www.linlap.com/wiki/toshiba+satellite+a135](http://www.linlap.com/wiki/toshiba+satellite+a135)
[http://ubuntuforums.org/archive/index.php/t-684164.html](http://ubuntuforums.org/archive/index.php/t-684164.html)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363770](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363770)

There does seem to be a problem with the audio support, but there seem to be folks that have gotten some success.  In the first link, a guy says he had no problem after disabling acpi before instlling.  Hope it helps.

---

