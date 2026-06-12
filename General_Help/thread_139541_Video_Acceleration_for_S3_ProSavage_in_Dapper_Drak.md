---
title: "Video Acceleration for S3 ProSavage in Dapper Drake?"
date: 2006-03-04
forum: General Help
---

### Post by diogoschneider78 on 2006-03-04
Greetings! :D

My system has an on-board S3 ProSavage video adapter but it has no 3D acceleration support in Breezy Badger. I know the latest DRI code has at least "testing" support for this chip, so I'd like to know if there's any chance to get 3D hardware acceleration on my system if I upgrade to Dapper Drake. :-k

Useful information:

$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

$ glxinfo | grep direct
direct rendering: No :(
OpenGL renderer string: Mesa GLX Indirect

Many thanks!
Diogo

PS: Sorry if this is not the best place in the forum to ask this kind of stuff, but I have tried everywhere else already and still got no answer for my question... :cry:

---

### Post by evilgold on 2006-03-04
Perhaps: [http://drivers.s3graphics.com/en/download/drivers/legacy/SavageMX-IX_290-299/Savage_4.0.3_binary.tgz](http://drivers.s3graphics.com/en/download/drivers/legacy/SavageMX-IX_290-299/Savage_4.0.3_binary.tgz)

I have an S3/VIA card on one of my motherboards but i didnt really pay much attention to acceleration, even on windows its not too great. The above driver might work, but i installed a nvidia card on my box before i tried to find out.

---

