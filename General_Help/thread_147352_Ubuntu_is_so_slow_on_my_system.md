---
title: "Ubuntu is so slow on my system"
date: 2006-03-20
forum: General Help
---

### Post by archer75 on 2006-03-20
I'm not sure why. My system specs are:

3.4ghz P4
3gb ram
Geforce 6800GT
Asus P4C800-E Deluxe
Soundblaster X-Fi 
WD Raptor drive
2x160gb Seagate drives
Sony DVD-Rom/CD-RW
NEC DVD burner 3550A


Windows is on a WD Raptor drive plugged into the onboard intel controller.

Ubuntu is on a 160gb Seagate drive plugged into the onboard promise controller.

Install of Ubuntu took about 3 hours. Boot up takes about 7 minutes. Opening firefox is about 15 seconds. The entire system just does'nt feel very responsive. 

I'm wondering if it's the promise controller? I could try put this drive on the intel controller and seeing if that helps. Any other ideas?

---

### Post by Perfect Storm on 2006-03-20
I can't help you on the boot, but there's diffently something wrong.

But you might install the right kernel:

Open the terminal (Application tab ---> Accessories ---> terminal)
```
sudo apt-get install linux-686
```

reboot.

and nvidia driver

```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```

reboot.

---

### Post by Zeroangel on 2006-03-20
Dapper Drake is very responsive, the bootup/startup speeds of some things like nautilus are nearly halved and it handles I/O better making the system more a little more reactive overall. Still in testing though.

There is a guide here somewhere about how to make Breezy more responsive.

---

### Post by Blunts on 2006-03-20
Please do not encourage a Dapper update for people that has questions already. Its for testing only as of right now. I know thats not what you said, but it implies.

---

### Post by archer75 on 2006-03-20
Any other ideas?

---

### Post by Hairy_Palms on 2006-03-20
hmm i wonder if theres a way to compile gnome 2.14 for breezy, although i doubt its worth it, 6.04 means dapepr should be out end of april

---

### Post by FLeiXiuS on 2006-03-20
Run 'top' just to see whats going on.  Check out the cpu/mem levels just to make sure everything is atease.

I'll post back later on with a followup...

Try enabling DMA on the hard drives and cdrom drives.

**$ sudo hdparm -d1 /dev/device**
Where /dev/device is your hard drive / cd-rom.

Any questions on any of this, let me know!

---

