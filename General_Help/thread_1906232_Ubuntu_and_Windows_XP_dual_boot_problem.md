---
title: "Ubuntu and Windows XP dual boot problem"
date: 2012-01-08
forum: General Help
---

### Post by thebasted on 2012-01-08
I had Windows XP installed and then I also installed Ubuntu 11.10. But, the screen to choose which OS to boot DOES NOT APPEAR and Ubuntu automatically boots. I would like to have the option to boot both OSes. I have checked the grub.cfg file and everything but I could not find anything...Could you help me?

---

### Post by zvacet on 2012-01-09
I´m not at Ubuntu comp right now,so read [https://help.ubuntu.com/community/Grub2%C2%A0#Timed_Display](https://help.ubuntu.com/community/Grub2%C2%A0#Timed_Display)

---

### Post by community on 2012-01-09
You just run the following command in terminal
**sudo update-grub**
Then restart your system and post the result.

---

### Post by raja.genupula on 2012-01-09
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)

install grub customizer & open it. click at preference and at general TAB at visibility click at show menu or give the time as 10 sec. 

look at the above link for clear info

---

### Post by muteXe on 2012-01-09
if none of the above suggestions work, do a 
```

sudo fdisk -l

```
and paste the results back here, just to check you still have an xp partition..

---

### Post by MartijnNL on 2012-01-09
> **thebasted said:**
> I have checked the grub.cfg file and everything but I could not find anything...Could you help me?

Is the Windows installation mentioned in grub.cfg at all (as a menuentry)? If not run update-grub and check it again.

---

### Post by muteXe on 2012-01-09
> **MartijnNL said:**
> Is the Windows installation mentioned in grub.cfg at all (as a menuentry)? If not run update-grub and check it again.

Yeah, this is why i was asking for an fdisk. Hope he/she hasn't wiped the windows partition.

---

### Post by MartijnNL on 2012-01-09
> **muteXe said:**
> Yeah, this is why i was asking for an fdisk. Hope he/she hasn't wiped the windows partition.

Well, I seem to see more posts with other OSes not being found by grub. So I'm thinking along the lines of an os-prober problem. But of course a wiped windows partition would cause the problem as well.

---

