---
title: "How to reduce CPU usage?"
date: 2012-05-01
forum: General Help
---

### Post by OpenSourceRules on 2012-05-01
When I had 512MB of RAM, the main issue was memory.
Now I get 2G of RAM, but sometimes the CPU thingy gets up to 100%, especially when I have Thunderbird and Firefox both openned.  
Dropbox is openned in the background; possibly I may change its usage: from family uses to share themes and backgrounds.  
I‘m not particularly sure about the file system, though.  I was told that JFS is less heavy on the CPU, but.....
OK, I can always reinstall with Ext4, though.

---

### Post by squilookle on 2012-05-01
I take it you have looked at something like system monitor, top or htop to see CPU usage is at 100%, were you able to see if there was one process using the CPU? If you can isolate one, then you might be able to find a solution from there.  

Do you know what processor you have?

---

### Post by MorrisseyJ on 2012-05-01
Yes check the system processes, i know there was an issue a while back with Thunderbird consuming a  massive amount of CPU resources.

If you have an intel processor you might also want to try the following: [http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/](http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/)

And if its a laptop Jupiter is pretty handy: [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by robert shearer on 2012-05-01
You could supply some relevant information on your system by running
```
sudo lshw
```
in a terminal and pasting the output (within 'code' tags for formatting) here.

Though at a guess, given your comment about ram and 'the cpu', you are using older hardware with a single core cpu.

Same here and yes having apps grab 100% cpu time is not uncommon.
If you are running 11.10 or 12.04 you could consider installing a lighter desktop such as Lubuntu.
```
sudo apt-get install lubuntu-desktop
```
and restart..
 at the login screen expand and choose lubuntu then login and try the much snappier performance of that desktop.

---

### Post by OpenSourceRules on 2012-05-01
CPU usage functuates a lot, but I have Jupiter installed and set to maximum performance.

---

