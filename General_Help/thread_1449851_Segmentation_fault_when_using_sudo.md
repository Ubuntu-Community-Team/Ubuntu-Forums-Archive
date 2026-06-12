---
title: "Segmentation fault when using sudo"
date: 2010-04-08
forum: General Help
---

### Post by el33t on 2010-04-08
Ok, so I got myself this 4GB flash drive and did a FULL installation of ubuntu in it. Now I'm using it as a Live USB.

So, I tried installing qt but I'm getting this segemntation fault error when using sudo. Here's what I did in detail :-

1) Downloaded the latest qt SDK from the below link :
   [http://qt.nokia.com/downloads/sdk-linux-x11-32bit-cpp](http://qt.nokia.com/downloads/sdk-linux-x11-32bit-cpp)

2) According to the instructions in the above link, I ran the following command :
chmod u+x qt-sdk-linux-x86-opensource-2010.02.bin


[FONT=Verdana]3) According to the instruction in the above link, I ran the follwoing command:

[/FONT]./qt-sdk-linux-x86-opensource-2010.02.bin

[FONT=Verdana]Now, here I'm getting a 'segmentation fault' error .

So I tried running the following command:

[/FONT]sudo ./qt-sdk-linux-x86-opensource-2010.02.bin


[FONT=Verdana]But I'm still getting this 'segmentation fault' thing. 

Here is a screenshot of what I did:

[IMG]http://i41.tinypic.com/acedzq.png[/IMG]

I have just started using Linux, so I request for a easy to follow response.  

Regards,
[/FONT]

---

### Post by sisco311 on 2010-04-08
qt-sdk is in the repositories. Use Synaptic (System -> Administration) to install it. You may have to enable the universe repository (System -> Administration -> Software Sources).

See: [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by el33t on 2010-04-08
Well, thanks! 

 But can't I install from that .bin file? And what is the cause of that 'segmentation fault' ? (Suppose I want to install qt on a linux live USB without internet)

---

### Post by sisco311 on 2010-04-08
Any chance that you are using the 64bit version of Ubuntu?

Please post the output of:
```
uname -a
```

---

### Post by el33t on 2010-04-08
No, its the 32-bit version. 

And here is the output of uname -a :

Linux el33t-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by sisco311 on 2010-04-08
Well, I downloaded & installed it without any errors.

Maybe your download is corrupted.

Run:
```
md5sum qt-sdk-linux-x86-opensource-2010.02.bin
```
the output should be:
```
bffb40784e2ca53548f5e06681651e99  qt-sdk-linux-x86-opensource-2010.02.bin
```if not then try to download the file again.

---

### Post by el33t on 2010-04-08
lol, yeah! The MD5 sum is different. Ok, I'll download it again and then try.

But let this thread be open, I'll post the result tomorrow.

---

