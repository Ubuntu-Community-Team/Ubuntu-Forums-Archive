---
title: "Nvidia"
date: 2010-03-05
forum: General Help
---

### Post by evilman on 2010-03-05
Hi, i have bought asus  notebook with nvidia geforce GT 320m, and installed ubuntu 9.10 notebook remix, and i can't found any drivers for video card, iam new in linux, thanks for help.

---

### Post by crichard on 2010-03-05
Goto System-> Administration -> Hardware Drivers, it'll update automatically, if not find it here [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

---

### Post by evilman on 2010-03-05
> **crichard said:**
> Goto System-> Administration -> Hardware Drivers, it'll update automatically, if not find it here [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)


No certified downloads were found for this  configuration.

and System-> Administration -> Hardware Drivers dont found too.

---

### Post by darolu on 2010-03-05
There is not even a "Beta" driver for your video card at nvidia site; I'm affraid you'll have to wait until Nvidia releases it.

---

### Post by crichard on 2010-03-05
Then, Go for Asus Support *[http://support.asus.com](http://support.asus.com)*  otherwise you need to wait for another Asus  notebook with nvidia geforce GT 320m user's support.

---

### Post by cascade9 on 2010-03-05
GT310 is just rebranded GT210, GT340 is rebranded GT240. The GT320/330 are meant to be new cards, but they are still based on the GT2xx architecture. I'd try the GT220 driver... its the closest thing I can see. But there is no offial GT220m driver for linux (funny thing is that there is for the GT230m) 

If it makes you feel any better, any OS selection with the "300 series" results in "No certified downloads were found for this configuration". 

nVidia has really dropped the ball with the 3xx series. I guess the the 5xxx ATI cards have given them a  scare.....

---

### Post by evilman on 2010-03-05
> **cascade9 said:**
> GT310 is just rebranded GT210, GT340 is rebranded GT240. The GT320/330 are meant to be new cards, but they are still based on the GT2xx architecture. I'd try the GT220 driver... its the closest thing I can see. But there is no offial GT220m driver for linux (funny thing is that there is for the GT230m) 

If it makes you feel any better, any OS selection with the "300 series" results in "No certified downloads were found for this configuration". 

nVidia has really dropped the ball with the 3xx series. I guess the the 5xxx ATI cards have given them a  scare.....
 
yes but notebook come with windows7 dvd and drivers disk and i found in drivers disk drivers GT 320m for windows. Its really sad , becouse i need again start using windows =(

---

### Post by 3rdalbum on 2010-03-05
> **evilman said:**
> yes but notebook come with windows7 dvd and drivers disk and i found in drivers disk drivers GT 320m for windows. Its really sad , becouse i need again start using windows =(

Well, saying that you "can't find any drivers for it" is probably not correct. If Ubuntu boots and works without it asking you if you want to use low graphics mode, then you have an Nvidia driver. It's a 2D driver, sure, but it works.

I've gone weeks without 3D in the past when Nvidia's driver has caused problems, so just keep Ubuntu and keep checking for Nvidia to release something.

---

### Post by evilman on 2010-03-05
> **3rdalbum said:**
> Well, saying that you "can't find any drivers for it" is probably not correct. If Ubuntu boots and works without it asking you if you want to use low graphics mode, then you have an Nvidia driver. It's a 2D driver, sure, but it works.

I've gone weeks without 3D in the past when Nvidia's driver has caused problems, so just keep Ubuntu and keep checking for Nvidia to release something.


But its realy annoying its really slow and max resolution 800x600 without drivers.

---

### Post by haydoni on 2010-03-05
In the next release of Ubuntu the Nvidia driver installed as default will be much improved... (not that this helps you yet)

---

### Post by emifran on 2010-03-05
I've got the same card, but in a Sony Vaio instead of Asus... and I have the same problem, I´m not able to find any working driver.

H

---

### Post by goatkeeper on 2010-03-05
[SIZE=2]All of a sudden [/SIZE]9.10 broke on me. No desktop. So I loaded 8.04.4LTS which is supposed to be ultra stable. Had a little hardware glitch but the install went smooth. Went to enable the Nvidia driver and restart and I was rewarded with a dead and scrambled up screen. What's with that? Since I am a noob and actually do for real work on my machines, not play with them, I was unhappy. Reinstalled. Now what? I've got all the updates. The right hand two inches of my video is a black stripe and the type is smudgy and the whole thing looks uncool. If I enable the driver, which in 9.10 fixed the screen and type and the rest with it, will I meet with the same scrambled screen again. My new motherboard uses GF8200 internal video. Somebody?

---

### Post by winzipftp on 2010-04-18
I have to wait ... I cant find the drivers for Linux

---

### Post by winzipftp on 2010-05-18
&#20351;&#29992;nvida&#26032;&#21457;&#24067;&#30340;300M&#31995;&#21015;&#30340;linux&#39537;&#21160;	195.36.24&#25104;&#21151;&#23433;&#35013;&#65288;NVIDIA-Linux-x86_64-195.36.24-pkg2.run&#65289;&#65292;&#23613;&#31649;&#20135;&#21697;&#25903;&#25345;&#21015;&#34920;&#35828;&#26126;&#20013;&#24182;&#27809;&#26377;GT320M&#22411;&#21495;....
Notebook: ASUS X5DX667ID-SL(With GT320M video card)&#65292;OS: Debian 5.04(x86_64 version), 2010-05-18

---

