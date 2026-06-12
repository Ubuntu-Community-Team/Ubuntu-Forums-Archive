---
title: "i got a good feeling that someone here can help me"
date: 2010-07-07
forum: General Help
---

### Post by fuyao on 2010-07-07
before i joined this forum i was messing around with my xubuntu installation, my laptop from 2006 can no longer run windows well so i installed xubuntu on it, at first i installed the new 10.04 version, but i went though a video driver hell. so right now im forced to install 8.10, which i heard is at the "end of life" (what?? cant you guys just say that the support for this version ended?? why the fancy terms??)

anyway, my laptop model is a ThinkPad R51e, with ATI Radeon Xpress 200M as my video card, in 10.04, i first tried the fglrx driver with some special configuration i got from googling around, but then the result is super slow lag when playing games, like my desktop freezes for 2-3 seconds before moving on another frame (some of you might already know what im talking about, is that bug)

so i installed the open source driver instead, but i want to play all those fun games from Windows, so an open source driver is not gonna cut it, so i dumped 10.04, and downgraded to 8.10, no problems with the driver now cause in this version my card is still supported

so now is what i want to ask you guys, after some use with 8.10,  i found that many softwares are outdated, so i want to upgrade my way back to 10.04, but then the video card driver issue stopped me, now im conflicting, should i upgrade or not? and if any of you knows how to make my video card function in 10.04, it would be great too

im still a newbie to linux/xubuntu

---

### Post by fuyao on 2010-07-08
c'mon now, help me guys

---

### Post by nothingspecial on 2010-07-08
Funnily enough 8.04 is supported for longer than 8.10

Why dont you try that until 10.10 to see if they`ve sorted your problem out.

---

### Post by QIII on 2010-07-08
Welcome to Ubuntu!

A little bit of explanation about how this forum works might be in  order.  We are all here voluntarily, on our own time and when we can be  here.  It may be that there is just the right person to answer your  question, but if he lives in Bangalore he may not be right on your post.

So 24 hours is the accepted bump time.

On to your problem. 

The place to start is this:  Operating Systems do not support OEM  hardware.  OEMs write drivers that work with OSs.  For instance, there  is a common misconception that Windows supports GraphicsCardX.  That is  not the case.  The manufacturer of GraphicsCardX has written a driver  that they have made sure works in a Windows environment.  Microsoft  makes no effort to accommodate the hardware.  That is on the OEM.

Yours is not an Ubuntu problem.  

AMD/ATI has "legacied" your card with  regard to Linux, by which I mean that they have discontinued driver  support improvements.  In the state it was left, it will not work  with the X Server currently used with Lucid.  It probably does work with  Intrepid, which is why you see the difference.

Consider AMD/ATI's options here:  As a businessman, how much effort and how many resources would you commit to maintaining the functionality of a piece of hardware that is by now pretty rare and has long exceeded its expected mechanical lifetime?  Frustrating for you, yes.  But good business sense.  How would the users of newer cards feel if AMD/ATI were to expend effort to support an older card and not support a newer one?

(Don't let anyone try to convince you that nVidia is any different.  They have legacy cards that are no longer supported and no longer work with more recent versions of X Server.  Try to get a GeForce 2 MX400 to work with Lucid.)

There is an open source driver, as you know, but it does not support 3D  at this point.  Understand that this is not the "fault" of the  developers.  They try very hard to figure out the best solution to fit a  dizzying array of possible solutions to hundreds of different GPUs and  their interaction with hundreds of different motherboards and other  hardware.  That is no easy task when they are basically backwards  engineering to a black box for which the OEM has not released  proprietary information.

The solution boils down to one of 3 things:

1.  Use the open source driver and understand its limitations.

2.  Use 8.04, which is supported until April, 2011.

3.  Purchase a newer graphics card.

---

### Post by fuyao on 2010-07-08
> **QIII said:**
> Welcome to Ubuntu!

A little bit of explanation about how this forum works might be in  order.  We are all here voluntarily, on our own time and when we can be  here.  It may be that there is just the right person to answer your  question, but if he lives in Bangalore he may not be right on your post.

So 24 hours is the accepted bump time.

On to your problem. 

The place to start is this:  Operating Systems do not support OEM  hardware.  OEMs write drivers that work with OSs.  For instance, there  is a common misconception that Windows supports GraphicsCardX.  That is  not the case.  The manufacturer of GraphicsCardX has written a driver  that they have made sure works in a Windows environment.  Microsoft  makes no effort to accommodate the hardware.  That is on the OEM.

Yours is not an Ubuntu problem.  

AMD/ATI has "legacied" your card with  regard to Linux, by which I mean that they have discontinued driver  support improvements.  In the state it was left, it will not work  with the X Server currently used with Lucid.  It probably does work with  Intrepid, which is why you see the difference.

Consider AMD/ATI's options here:  As a businessman, how much effort and how many resources would you commit to maintaining the functionality of a piece of hardware that is by now pretty rare and has long exceeded its expected mechanical lifetime?  Frustrating for you, yes.  But good business sense.  How would the users of newer cards feel if AMD/ATI were to expend effort to support an older card and not support a newer one?

(Don't let anyone try to convince you that nVidia is any different.  They have legacy cards that are no longer supported and no longer work with more recent versions of X Server.  Try to get a GeForce 2 MX400 to work with Lucid.)

There is an open source driver, as you know, but it does not support 3D  at this point.  Understand that this is not the "fault" of the  developers.  They try very hard to figure out the best solution to fit a  dizzying array of possible solutions to hundreds of different GPUs and  their interaction with hundreds of different motherboards and other  hardware.  That is no easy task when they are basically backwards  engineering to a black box for which the OEM has not released  proprietary information.

The solution boils down to one of 3 things:

1.  Use the open source driver and understand its limitations.

2.  Use 8.04, which is supported until April, 2011.

3.  Purchase a newer graphics card.

i think some softwares dont work on 8.04, instead they support 8.10. and yea buying a new video card is what i realized i have to do in the end, but im not a computer hardware expert so i cant do it on my own, and i hope that the open source developers will eventually implement 3D acceleration

---

### Post by QIII on 2010-07-08
It may be that with your laptop, installing a different GPU would be impossible.  Your current one is integrated (that is, it is installed on the motherboard itself) and there may be no way to install a different one.

I really hate to give advice that costs money, but ...

Option 3 may be no option for you without a suitable replacement motherboard, which would probably be cost prohibitive -- if it can even be done.

Depending on where you live, there may be a used computer store or a private network of sellers that would allow you to pick up a slightly newer used machine for a reasonable cost.

If you go that route, then I would suggest coming back here with some specifications of your potential purchase and ask for advice with regard to how the GPU/driver combination would work with the current state of X Server.

---

### Post by fuyao on 2010-07-09
> **QIII said:**
> It may be that with your laptop, installing a different GPU would be impossible.  Your current one is integrated (that is, it is installed on the motherboard itself) and there may be no way to install a different one.

I really hate to give advice that costs money, but ...

Option 3 may be no option for you without a suitable replacement motherboard, which would probably be cost prohibitive -- if it can even be done.

Depending on where you live, there may be a used computer store or a private network of sellers that would allow you to pick up a slightly newer used machine for a reasonable cost.

If you go that route, then I would suggest coming back here with some specifications of your potential purchase and ask for advice with regard to how the GPU/driver combination would work with the current state of X Server.
this laptop is brought in China back in 2006, it's an old model now, went thru many many OS reinstallations.
the college im going to give every new incoming freshmen a new laptop, and the laptop is mine to keep after i graduate (means it's the university's property until i graduate), so the 2006 laptop will become a xubuntu computer, just for my linux learning experience

and here is some new information on my system, today i upgraded 8.10 to 9.04, and although during the upgrade the upgrade tool warns me that my games will run very slow due to my video card no longer supported in 9.04. but that is not the case, after i finished upgrading to 9.04, every single games installed runs smoothly. just like how they should run in 8.04 or 8.10, and the screen flickering is gone.

it seems that there is some stuff from 8.04 floating around after i upgraded to new versions, im now upgrading to 9.10 and see if the games still run smoothly

---

### Post by fuyao on 2010-07-11
new update on my system:

on 9.10, everything runs good, not perfect, it's now that i went to an even higher level by upgrading to 10.04, and problems with games and video drivers came back

guess i'll have to wait for 10.10 then huh, i wish in Maverick ubuntu developer will have a fix for computers with older video cards like mine

---

### Post by x1a4 on 2010-07-11
Hi,

First try 10.4 and use the 'Hardware Drivers' tool.  If that doesn't install the correct driver have a look at the ATI website and see if they have a Linux driver.  If that doesn't work install 8.4.  Unfortunately, ATI doesn't support Linux well. nVidia is a good choice when running Linux.

---

