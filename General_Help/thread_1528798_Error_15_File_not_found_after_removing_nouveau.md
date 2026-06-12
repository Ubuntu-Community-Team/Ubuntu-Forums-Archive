---
title: "Error 15: File not found after removing nouveau"
date: 2010-07-11
forum: General Help
---

### Post by sham08 on 2010-07-11
Hello.Just upgraded from Ubuntu 9.10 to Ubuntu 10.04.But couldn't make Lucid detect my newly installed graphic card (Nvidia GeForce 8400 GS).Every time I rebooted,I had to reconfigured in System > Preferences > Appearance.Tried the proprietary driver,even it's showed activated but I knew that the new graphic card wasn't configured correctly because I couldn't enlarged this Google Chrome windows (just like when I used on-board graphic).So,I made some browsing on the Internet and found out that I had to remove 'nouveau packages' via Synaptic Package Manager to enable my new Nvidia graphic card to operate well with Ubuntu 10.04.Went to Synaptic,and type 'nouveau' in the Search box and there were 2 packages related to 'nouveau' (libdm - nouveau1 ver: 2.4.18-1 ubuntu3 and xserver-org- video-nouveau ver:1:0.0.15+git 201002).Because of my stupidity,I've marked both for completely removal.Even though there were red line appeared (sign for warning) and prompt messages : that the packages that I marked for removal was an essential packages,I just ignored it and clicked the 'Apply' button.And the chaos began.
I know that right now,I'm really in a big trouble and I can't boot in Ubuntu 10.04.Stuck with the message 'Boot from (hd,0) ext 3 862ab747-5010-413b-89d1-4436lb9165d6. Error 15: File not found.Press any key to continue...'and couldn't move further than these kernels options (on my PC screen right now).I'm afraid to make any action,since I'm really a newbie.Is there any way or options to recover from this crash?And also,I should inform that I have the installation CD (Ubuntu 10.04) from Canonical,that maybe useful to recover (if by chances there's any possibilities).Hope to hear from you guys,and thanks in advance for any respond.Please.

---

### Post by realzippy on 2010-07-11
Simulated this on my machine...kicks the whole system...kernel included,
thats why you get the error 15.Might be faster to boot the liveCD to
backup personnel data you need and start a fresh 10.04 install....

List  of uninstalled packages (might differ from yours..):

---

### Post by Frogs Hair on 2010-07-11
Hi sham08,
I have filed bug report # 602876 regarding the driver activated but not in use message . you are the third person in as many days to mention this and we all have the same graphics card . I my case the driver is working and I have a clean install of 10.04.

I know the driver is working because all 3D effects are activated and working. please feel free to add a comment to the bug report @ launchpad .net so I can get confirmation that I am not the only user affected. I have submitted my driver jockey log as requested by a person looking into the issue.

---

### Post by sham08 on 2010-07-12
> **realzippy said:**
> Simulated this on my machine...kicks the whole system...kernel included,
thats why you get the error 15.Might be faster to boot the liveCD to
backup personnel data you need and start a fresh 10.04 install....

List  of uninstalled packages (might differ from yours..):Ok,I should download liveCD.But,is it possible downloading liveCD edition using Vista?Because right now,the only way I can access the Internet is via my brother's laptop.By the way,which edition should I use for recovery (I mean desktop edition or alternate edition)?And sorry I can't provide the list of uninstalled packages.Because during the chaos,I could only cursing myself of the stupidity act.Thanks for your respond.

---

### Post by realzippy on 2010-07-12
Think you are better with the normal liveCd(alternate is no liveCD afaik,just an installer)Do not know if Vista's
burning tool can burn ISO files,but e.g. Nero can for sure...

---

