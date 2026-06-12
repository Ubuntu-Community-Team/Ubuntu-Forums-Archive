---
title: "I3 Processor Problem... PLEASE HELP"
date: 2010-03-08
forum: General Help
---

### Post by schwabdale on 2010-03-08
I purchased a Sony Vaio with an Intel I3 Processor. 
I tried to install Ubuntu 9.1 via the CD in Windows.... It loads, then when rebooting into Ubuntu... Nothing.

I tried to boot off the CD and it boots until I click install.. Then nothing

I tried to install from a flash drive... nothing...


Please help, I purchased this without doing homework.

---

### Post by proxess on 2010-03-08
I recently bought for my gf's birthday an Acer 5740G with an Intel i3 330M, ATI HD 5470, 4GB DDR2 and 500GB HDD, and Ubuntu 9.10 x64 works flawlessly except for the annoying "Unsupported Hardware" due to the FGLRX drivers not supporting the ATI card yet.

From what you describe, your CD is what has the problem, it seems. Have you tried checking it??

---

### Post by schwabdale on 2010-03-08
Yes, I have tried two cd"s. Same problem. Any advice?

---

### Post by schwabdale on 2010-03-08
Can you give me a link to the x64 download?

---

### Post by proxess on 2010-03-08
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Press on the Alternate Download Options and select 64-Bit.

---

### Post by iponeverything on 2010-03-08
> **schwabdale said:**
> I purchased a Sony Vaio with an Intel I3 Processor. 
I tried to install Ubuntu 9.1 via the CD in Windows.... It loads, then when rebooting into Ubuntu... Nothing.

I tried to boot off the CD and it boots until I click install.. Then nothing

I tried to install from a flash drive... nothing...


Please help, I purchased this without doing homework.

I don't think it has anything to do it being an i3. 

I would grab the early 10.04 to try or the 9.04 to see if one of those work. I have noticed several machines of mine that 9.10 refuses to work on.. (runs great on my wife's x200s though)

---

### Post by anse on 2010-03-15
The Intel Arrandale family (which i3 belongs to) is not supported in the kernel that Ubuntu 9.10 is using or by XOrg. I think you will get the XOrg updates by making sure your installation is up to date. Have a look at this link for more information 

[http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10")

I also recently bough a Vaio and have fixed most of my problems (still have an issue with the wlan card).

---

### Post by teh603 on 2010-03-15
I've been able to boot my i3-based Dell laptop using Jaunty, although I don't recomend it because it uses the vesa driver and makes its 15" widescreen screen look awful and stretched. Karmic gives me a black screen of death.

I'd suggest waiting until Lucid, or trying the beta when it comes out in a few days. I've been alpha testing it, and it seems to be supported "fairly well."

---

### Post by proxess on 2010-03-16
Those are all GPU issues. What GPU do you have??

---

### Post by teh603 on 2010-03-17
> **proxess said:**
> Those are all GPU issues. What GPU do you have??If he's got an i3 system, its probably using the Arrandale chipset. That means not much support until Lucid.

---

### Post by proxess on 2010-03-18
It'll work fine if you've got Backports activated in the repos.

I actually rolled back from Lucid to Karmic on my girlfriend's laptop because ATI drivers don't support the latest Xorg (nor does it support her GPU, but it works with an annoying watermark if you activate experimental packages somewhere in Synaptic).

---

