---
title: "Ubuntu 10.04 Startup Issue"
date: 2010-06-28
forum: General Help
---

### Post by gmanator on 2010-06-28
Ok ive been a distro hopper for some time but I have always considered Ubuntu as my neutral because it normaly does exactly what I want it to, when 10.04 came out I was testing a different distro and did not feel the need to install it at the time, I finaly had finished testing out the other distrobution (Zorin OS) and concluded that it was rather slugish. Thats when I decided to download the live disk for 10.04, when I try and use the live disk it goes, acts like its going to load then I get a black screen and stop getting signal from my computer to my screen, this was rather disipointing so I decided to reinstall 9.10 and upgrade from that, when it finished upgradeing I restarted my computer and went to start up 10.04 ready to log in and have me some linux, then it went to a black screen and I got an error message I assume like this.

"[drm] nouveau 0000:00:0d.0: misaligned reg 0x0060081d"

There were 2 of them exactly the same stacked on one another. 

After this I decided to download the Alternate installer disk and install it that way, I got the same results. I have an AMD sempron 64, 2gig ram, Nvidia 8400 graphics card, I have 2 hard drives but the one I was using as an install is 160gig.

---

### Post by dino99 on 2010-06-28
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

many issues with this 8400 card:

[http://www.google.fr/search?as_q=nvidia%2B8400%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=nvidia%2B8400%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

this is a video driver issue, so boot with video=vesa on the boot line, maybe you can try with nomodeset too

---

### Post by gmanator on 2010-06-28
Well I fixed it by booting in while using my integrated nvidia 6100 and downloading the nvidia drivers, then booted in with my 8400 and ran nvidia-xconfig as root and it fixed my issue.

---

