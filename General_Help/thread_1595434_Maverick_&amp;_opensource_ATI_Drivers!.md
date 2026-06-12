---
title: "Maverick &amp; opensource ATI Drivers!"
date: 2010-10-13
forum: General Help
---

### Post by cottfcfan on 2010-10-13
This may just be me. But ive noticed a big deterioration in the open source drivers from Lucid to Maverick.
I'm using Radeon HD2400 G/C, in lucid Graphic speed wasn't brilliant but fairly smooth. Now in Maverick its choppy and slow.
GLX gears bears this out with 1/2 the FPS over Lucid.
 Has anyone else noticed? or know what the problem might be?

---

### Post by danzvash on 2010-10-14
Yep - I did an upgrade yesterday from Lucid to Maverick, and the graphic performance has definitely gone way down.
Videos not in full-screen are really choppy. Window drawing and menus are sluggish.
I haven't done a glxgears test yet, but will do later.
I'm on a Radeon HD3200 and using the opensource radeon driver.

Glad I'm not the only one - perhaps we'll find the culprit soon ....

---

### Post by cottfcfan on 2010-10-14
Graphics performance was so poor for me that ive reinstalled Lucid.
The fglrx driver works ok, but find too many glitches using that, mainly screen tearing.
 One thing that i have found is that in Lucid if you add the ubuntu-xswat-ppa, and update, the graphics become as poor as Maverick.
 Obviously some regression in xserver-xorg.
 Just wondering if its possible to install Maverick and downgrade xorg?

---

### Post by mastablasta on 2010-10-14
> **cottfcfan said:**
> The fglrx driver works ok, but find too many glitches using that, mainly screen tearing.

 
did you install the correct one? There should be one made by AMD sort of "specially" for ubuntu. should be another catalyst 10.10 in existance i believe, while previous was 10.9 if i am not mistaking.

---

### Post by cottfcfan on 2010-10-14
> **mastablasta said:**
> did you install the correct one? There should be one made by AMD sort of "specially" for ubuntu. should be another catalyst 10.10 in existance i believe, while previous was 10.9 if i am not mistaking.

I just used the packaged one from "hardware drivers"
Boot & Login becomes a mess (i know theres a workaround) and when changing screens or logging in/out I get multicolored stripes on the screen for a second.
Dropped back to Lucid and the O/S drivers work fine.

---

### Post by SpEcIeS on 2010-10-14
I have also noticed the decrease in performance with the radeon driver in maverick compared to lucid. Even the fglrx drivers are worse than normal in Maverick. 

My system currently has a Radeon HD 3450, which is a big disappointment.

---

### Post by tarekeldeeb on 2010-10-16
Me too, same problem!

I have this:
```
$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
```

When I try to find `additional hardware drivers' I find nothing!

Did any1 find a clue?

---

### Post by ggsinclair on 2010-10-16
Hi.

I have a Radeon HD4870 and I cannot get the driver to work under the PAE version of 10.10 but it seems to work fine under the non PAE version - bizarre.

There is a new version of Catalyst available if that helps.

---

### Post by X5-655 on 2010-12-23
I'm seeing this too..

Though ironically, everytime I mention this, people point the finger to me saying it's my computer, or I installed Ubuntu wrong..  Right, whatever..

This thread among others is proof that I am not crazy.

---

### Post by PhantmKllr on 2010-12-23
I have noticed that these issues only arise with HD ATI/AMD graphics cards. I have an ATI Radeon Xpress 1150 mobile, and it works beautifully with Ubuntu 10.10

---

### Post by hannuh on 2011-01-04
> **PhantmKllr said:**
> I have noticed that these issues only arise with HD ATI/AMD graphics cards. I have an ATI Radeon Xpress 1150 mobile, and it works beautifully with Ubuntu 10.10

Not just ATI, same problem, however, not quite as bad happens with Nvidia too. The FPS readings of Nvidia 9800 and GT 220 are less than half of what they were under Lucid. But ATI is even worse, my ATI HD 5770 box is unusable for any serious video editing etc.
I am going to try Mandriva 2010.2 with that box, to see what happens.
Hannu

---

### Post by GargoyleK1 on 2011-01-04
I am brand new to Ubuntu I believe I have 10.10 installed. I replaced my old and tired xp with it. So far all of my questions have been answered but this graphics one. I have a radeon 200M that honestly has worked very good in the past. I have tried simple games like tuxracer and mu screen goes into a strobe effect. It does the same thing with other relatively simple games as well. This issue is new since the Ubuntu install and I would love to be able to fix this.

Any tips or advice would be great.

Thanks!

---

### Post by cottfcfan on 2011-01-05
Someone may correct me, but after checking the AMD/ATI website, it appears there is no proprietary driver for your Graphics card.
Looks like your stuck with the OSS ones until they improve.

---

### Post by Mark Phelps on 2011-01-05
> **GargoyleK1 said:**
> ... I have a radeon 200M that honestly has worked very good in the past. 

That's because, in the past, there WERE restricted drivers for that card that would work with the (then) current versions of Ubuntu.  That has not been true for years now.

The only working drivers today are the ones you have already installed.  There are no downloadable drivers that will work with your card and current versions of Ubuntu.

---

### Post by GargoyleK1 on 2011-01-05
So then.... There are no options?

---

### Post by GargoyleK1 on 2011-01-05
> **cottfcfan said:**
> Someone may correct me, but after checking the AMD/ATI website, it appears there is no proprietary driver for your Graphics card.
Looks like your stuck with the OSS ones until they improve.

Sorry I missed this post earlier. How would I check to see if it get improved? Is there a special area I can watch so I will know?

Thanks! I must say this is the first non-windows system I have ever installed and I like it! Hopefully an improvement is released so I can enjoy it even more.

---

### Post by cottfcfan on 2011-01-06
theres not much you can do, although many have noticed that the graphics seemed significantly better using 10.04lts rather than 10.10 which you have. So you could give 10.04 a go and see if that improves things.

---

### Post by clhsharky on 2011-01-06
GargoyleK1

> So then.... There are no options? 
Try turning off visual effects when playing games.

Sharky

---

### Post by Mark Phelps on 2011-01-06
> **GargoyleK1 said:**
> So then.... There are no options?

In terms of other drivers -- no.  What you have is all that is available.

In  terms of options, if you open a terminal and do a "man radeon", it will list options that are available -- some of which may improve your video performance.

---

