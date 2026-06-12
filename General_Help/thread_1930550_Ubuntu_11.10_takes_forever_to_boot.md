---
title: "Ubuntu 11.10 takes forever to boot?"
date: 2012-02-23
forum: General Help
---

### Post by frank0478 on 2012-02-23
starting cpu interrupts balacing daemon [OK] 



then it takes forever go from line to line 
  ex after that line,


[ 44,148085] ieee80211 phy0:wl_ops_bss_info_change:gos enabled:true(inplemented) 

[ 44.149096] ieee80211 phy0: brcmsmac:wl-ops_bss_info_changed:associated


  and it will go on like this, taking literately forever from line to  line. Gradually the number in the square brackets increases with the  line. Help, what exactly does this mean? I can't even get to the log on  menu. This all happened after I try to restart upon installing the ATI  drive for Linux. Now it's like this... What is up exactly?

---

### Post by idoitprone on 2012-02-24
> **frank0478 said:**
> starting cpu interrupts balacing daemon [OK] 



then it takes forever go from line to line 
  ex after that line,


[ 44,148085] ieee80211 phy0:wl_ops_bss_info_change:gos enabled:true(inplemented) 

[ 44.149096] ieee80211 phy0: brcmsmac:wl-ops_bss_info_changed:associated


  and it will go on like this, taking literately forever from line to  line. Gradually the number in the square brackets increases with the  line. Help, what exactly does this mean? I can't even get to the log on  menu. This all happened after I try to restart upon installing the ATI  drive for Linux. Now it's like this... What is up exactly?

I do not know your problem, but it looks like it taking forever for your broadcom card to load. brcmsmac is a broadcom wireless driver

---

### Post by Mark Phelps on 2012-02-24
The Radeon open-source video drivers have improved a lot in recent Ubuntu versions.  Unless you are running resource-demanding games that need 3D hardware acceleration, you don't really need the AMD proprietary drivers installed.

You should consider uninstalling them and going with the open-source default Radeon driver:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by frank0478 on 2012-02-24
What is an opensource driver? Sorry I am a noob XD 
I have ati 6550m on the laptop

I left my laptop on overnight and it was still stuck on those lines [number]...... man, what the heck is wrong =(

---

### Post by roelforg on 2012-02-24
> **frank0478 said:**
> What is an opensource driver? Sorry I am a noob XD 
I have ati 6550m on the laptop
[http://en.wikipedia.org/wiki/Open_source#Computer_software](http://en.wikipedia.org/wiki/Open_source#Computer_software)

---

### Post by frank0478 on 2012-02-24
So will the link you provided in the 3rd box work with gnome3? 
The reason I tried to install the ati driver in the first place is because everytime I tried to log into gnome 3, it booted me to gnome classic, with no animation. I looked around and found that it's because my computer didn't meet the "graphic requirement"  (which is strange because I did have gnome 3 functional at one point in time, but then I had to reinstall ubuntu and it hasn't worked since)
So I checked under system info and nothing was beside the Graphic section, hence me installing ati hoping it would work...but now it 's this stupid start up problem.

---

### Post by idoitprone on 2012-02-28
> **frank0478 said:**
> So will the link you provided in the 3rd box work with gnome3? 
The reason I tried to install the ati driver in the first place is because everytime I tried to log into gnome 3, it booted me to gnome classic, with no animation. I looked around and found that it's because my computer didn't meet the "graphic requirement"  (which is strange because I did have gnome 3 functional at one point in time, but then I had to reinstall ubuntu and it hasn't worked since)
So I checked under system info and nothing was beside the Graphic section, hence me installing ati hoping it would work...but now it 's this stupid start up problem.

wow 6550m ati. You definately surpassed the graphic requirement, but your card is not supported. Only the newer kernels can support your card. I recommend the priotory catalyst driver 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

