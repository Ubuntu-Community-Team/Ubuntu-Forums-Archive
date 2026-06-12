---
title: "What is the difference between Ubuntu 32-bit and 64-bit?"
date: 2012-05-13
forum: General Help
---

### Post by robawalsh on 2012-05-13
From  what I understand, 32-bit is more compatible with hardware etc., but newer hardware should all support 64-bit, which is superior. 

Am I correct? 

However, if I install 64-bit, will this affect software in any way?

---

### Post by kc1di on 2012-05-13
> **robawalsh said:**
> From  what I understand, 32-bit is more compatible with hardware etc., but newer hardware should all support 64-bit, which is superior. 

Am I correct? 

However, if I install 64-bit, will this affect software in any way?

There should not be many instances any longer where you can't run certian software on a 64bit system if you have the hardware go for it i'm using it on two machines here and have had no problems.

one of the biggest drawbacks of 32 bit is the amount of ram it will support only 3gb.  64 bit will address much more. there are ways around that in 32 bit.  but for all my purposes I find 64 bit works fine.

---

### Post by kolinab on 2012-05-13
The way I look at it, it depends on your processor architecture. If you have a 64 bit capable processor, then you will probably have faster performance with the 64 bit install. 

There's a long discussion of this question here:

[http://askubuntu.com/questions/7034/what-is-the-difference-between-32-bit-and-64-bit-and-which-should-i-choose](http://askubuntu.com/questions/7034/what-is-the-difference-between-32-bit-and-64-bit-and-which-should-i-choose)

And a little more from the Community wiki:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by zombifier25 on 2012-05-13
> **kc1di said:**
> There should not be many instances any longer where you can't run certian software on a 64bit system if you have the hardware go for it i'm using it on two machines here and have had no problems.

one of the biggest drawbacks of 32 bit is the amount of ram it will support only 3gb.  64 bit will address much more. there are ways around that in 32 bit.  but for all my purposes I find 64 bit works fine.

Ubuntu 12.04 32bit uses the PAE kernel by default, which means it can use more than 4GB of RAM.

---

### Post by robawalsh on 2012-05-13
I think I might go with 64-bit. 

Just to check, I assume this processor supports 64-bit? 

2nd generation Intel® Core™ i3-2350M processor (2.30 Ghz, 3M cache)

---

### Post by 3rdalbum on 2012-05-13
> **robawalsh said:**
> I think I might go with 64-bit. 

Just to check, I assume this processor supports 64-bit? 

2nd generation Intel® Core™ i3-2350M processor (2.30 Ghz, 3M cache)

Yep.

Just so you know, the filename of the 64-bit ISO includes the term "amd64". Don't worry, this is the correct ISO for 64-bit Intel CPUs too. Not just AMD CPUs.

---

### Post by flemur13013 on 2012-05-13
Some things actually run considerably faster with 64 bit, mostly audio and video processing. You'll probably use more memory under 64 bit, but not twice as much.

Other than that I saw no effective difference between 32 and 64 bit with 10.04.  On Win7 a lot of 32 bit programs act funny under the 64 bit OS so I went back to 32 bit there; there was also little or no speed difference, but linux seems to have done the 64 bit OS and programs properly.

---

### Post by robawalsh on 2012-05-13
> **flemur13013 said:**
> Some things actually run considerably faster with 64 bit, mostly audio and video processing. You'll probably use more memory under 64 bit, but not twice as much.

Other than that I saw no effective difference between 32 and 64 bit with 10.04.  On Win7 a lot of 32 bit programs act funny under the 64 bit OS so I went back to 32 bit there; there was also little or no speed difference, but linux seems to have done the 64 bit OS and programs properly.

Thanks. I'll get the 64-bit. 

Is it necessary to get the 32-bit libraries at all?

Also, I saw that there are/were some issues with Flash in 64-bit. Is this still the case or is this fixed?

---

### Post by kc1di on 2012-05-13
> **robawalsh said:**
> Thanks. I'll get the 64-bit. 

Is it necessary to get the 32-bit libraries at all?

Also, I saw that there are/were some issues with Flash in 64-bit. Is this still the case or is this fixed?

If you install wine it will pull some 32 bit libs.

---

