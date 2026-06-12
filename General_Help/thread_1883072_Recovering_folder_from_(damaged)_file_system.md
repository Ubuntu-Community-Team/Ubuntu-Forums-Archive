---
title: "Recovering folder from (damaged?) file system"
date: 2011-11-18
forum: General Help
---

### Post by Dantman78 on 2011-11-18
Hopefully, the title of this question isn't misleading in any way. Let me tell you the entire predicament, and maybe you guys can better help me. 

For the past month or so Ubuntu (run 11.04) would get extremely slow after a short amount of time. I'd log in and start surfing the web, and it would slow to a crawl and sometimes freeze up. Nothing ever crashed, and if I waited long enough I could resume without any problems. I found by restarting the system (if I was able to) would fix the problem for that session, but if I booted up again it would continue on the next boot. This could be a coincidence but it seemed to happen after the 11.10 upgrade message would pop up. So, one day it popped up and I decided to upgrade. End of the world. The installer must have crashed because the computer turned itself off and GRUB would boot into stage 1.5 error 24. 

A friend of mine burned a 11.10 live CD for me and I went in trying to fix the problem. I found that my hard drive was showing up as "314 GB File System" and it was unable to be mounted. I decided to just do a complete reinstall, after not finding any real way to fix the problem. The installer recognized my 11.04, and offered to upgrade it to 11.10. I took a shot and tried it, the installer crashed before it could even start, but lo and behold my file system mounted and I was able to go in and recover almost all of my files. This is where the problem comes in. 

The one folder I want, out of all of them, is unable to be copied, read, or moved. 

The error message:
```
You do not have the permissions necessary to view the contents of "YouTube Rips".
```This is the location, as you can see, Ubuntu is treating my file system as if it was a  simple USB drive:

```
/media/4ce65329-f09b-4aa4-8b68-d8e3eeab3b43/home/Dantman78/Videos/bmov/Youtube Rips
```The installer doesn't recognize my 11.04 anymore, and now when I boot, no more error 24, but it is unable to find (can't recall right now) something/root. 
[B]
So, my question is: Is there any way I can recover this folder, or is it a lost cause? [/B]Sorry, I wrote my entire life story here, hopefully that gives you the gist of my situation. As you can see, I'm no expert by any means, but if any of you can steer me in the right direction, it would help a lot.

---

### Post by ajgreeny on 2011-11-18
From the live CD you will need to use ```
sudo cp /media/4ce65329-f09b-4aa4-8b68-d8e3eeab3b43/home/Dantman78/Videos/bmov/Youtube\ Rips/* /media/*<destination>*
```You need the \ in **Youtube\ Rips** to escape the space, and you will need to show the destination folder correctly as well.   You will need to do it as root with sudo.

Alternatively you can use nautilus as root with ```
gksu nautilus
```and then drag and drop as normal.

---

### Post by Dantman78 on 2011-11-18
I tried that before but that pesky space. I guess in my frustration I forgot about it. 
Sorry for making such a big deal about such a run of the mill thing. :)

Thanks.

---

