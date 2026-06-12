---
title: "System Crash"
date: 2010-02-09
forum: General Help
---

### Post by eranga1988 on 2010-02-09
Hey guyz, I have met with a huge prob.
I cant log on to ubuntu 9.10...After loading ubuntu icon it only displays black screen..What should I do???Is there any way to take ubuntu for an earlier state or recover without formatting hard disk????

Pls help me...

---

### Post by NightwishFan on 2010-02-09
Did it work previously? If so, you can boot into recovery mode to try to fix the problem. Perhaps you have some broken X packages. To boot into recovery mode, hold L shift when you turn on your computer until you see a menu. Choose "recovery mode" and then run DPKG to see if you have any broken packages.

Also, knowing what Graphics hardware you have will help as well. You can go into a root shell from recovery mode, and run this command:
```
lshw -C display
```

---

### Post by eranga1988 on 2010-02-09
> **NightwishFan said:**
> Did it work previously? If so, you can boot into recovery mode to try to fix the problem. Perhaps you have some broken X packages. To boot into recovery mode, hold L shift when you turn on your computer until you see a menu. Choose "recovery mode" and then run DPKG to see if you have any broken packages.

Also, knowing what Graphics hardware you have will help as well. You can go into a root shell from recovery mode, and run this command:
```
lshw -C display
```

thanx i will try.it worked for few months.today i did some updates and changed the kernel also to get 4GB RAM worked.bt it worked fine.then i started 2 browse web.suddenly the root shell (black screen)appeared showing firestarter is disabling.bt nothing happened.it stucked.after rebooting i cant log on to ubuntu

---

### Post by NightwishFan on 2010-02-09
Also, try an older kernel and see if it works. If it does, then you should disable the newer kernel until further notice. You can boot older kernels from GRUB.

---

### Post by xklein6891 on 2010-02-09
Really sorry to hear that man..
btw, just wanna share this site to you: [http://pcregistrycleaners.org/speed-up-computer/](http://pcregistrycleaners.org/speed-up-computer/) it has really interesting stuff that might help.

---

### Post by NightwishFan on 2010-02-09
^ Registry cleaning is utterly overrated. I am willing to bet it causes more problems than it fixes. Anyway, that is irrelevant to Linux, so disregard.

---

### Post by eranga1988 on 2010-02-09
> **NightwishFan said:**
> Also, try an older kernel and see if it works. If it does, then you should disable the newer kernel until further notice. You can boot older kernels from GRUB.
Oh dude..I uninstall the older kernel from the boot loader..But I think i may find a way to reinstall it.
Thanx...

---

### Post by eranga1988 on 2010-02-09
> **NightwishFan said:**
> ^ Registry cleaning is utterly overrated. I am willing to bet it causes more problems than it fixes. Anyway, that is irrelevant to Linux, so disregard.
Oh ohhhhh

---

### Post by NightwishFan on 2010-02-09
I believe you can install the older kernel by going into recovery mode and going to the root shell with networking. Then type:
```
sudo aptitude install linux-image-2.6.31-14-generic
```

---

### Post by eranga1988 on 2010-02-09
> **NightwishFan said:**
> I believe you can install the older kernel by going into recovery mode and going to the root shell with networking. Then type:
```
sudo aptitude install linux-image-2.6.31-14-generic
```
Ohhh..It installed successfully, but I cant log even from the old kernel...isn't there anything can do with sysresccd???

---

### Post by NightwishFan on 2010-02-09
There should be a new entry in GRUB for the old kernel.

---

### Post by eranga1988 on 2010-02-09
I think itz better for an clean installation of ubuntu....

---

### Post by eranga1988 on 2010-02-09
> **NightwishFan said:**
> There should be a new entry in GRUB for the old kernel.
Yeah I got the old kernel..But I met with the same problem from the old kernel toooooo...

---

### Post by NightwishFan on 2010-02-09
Perhaps a clean install would be best. I am sorry I could not help more.

---

### Post by eranga1988 on 2010-02-09
> **NightwishFan said:**
> Perhaps a clean install would be best. I am sorry I could not help more.
Itz OK nightwish..I will do it!!!

---

### Post by tanvi on 2010-02-09
hello.

i hav ubuntu installed in a separate drive and have dual boot in my system.

my ubuntu 8.04 got crashed. It is corrupt now.

how can i recover my ubuntu ..as i want my data back

plz help soon..

---

### Post by NightwishFan on 2010-02-09
Tanvi, you should create a new thread on this issue. My advice is to use an Ubuntu live CD to copy your data to a safe place. You can mount the installed Ubuntu drive from the CD.

---

