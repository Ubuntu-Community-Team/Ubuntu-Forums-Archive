---
title: "Ubuntu 10.04 takes a long time to boot up!"
date: 2010-07-26
forum: General Help
---

### Post by TheNerdAL on 2010-07-26
After I installed a new hard drive, when I booted up into Ubuntu, it would give me this error: "failed command: WRITE DMA". So I tried the workarounds and I guess it just covered the log with the Boot Splash, now it's taking a long time just to boot up. Can anyone help me? Thanks.

---

### Post by TheNerdAL on 2010-07-27
bump

---

### Post by philinux on 2010-07-27
> **TheNerdAL said:**
> After I installed a new hard drive, when I booted up into Ubuntu, it would give me this error: "failed command: WRITE DMA". So I tried the workarounds and I guess it just covered the log with the Boot Splash, now it's taking a long time just to boot up. Can anyone help me? Thanks.

Hi.

Check out the General Help forum sticky.

---

### Post by wojox on 2010-07-27
Try the first solution. It worked for me. [How to speed up boot of Ubuntu 10.04 Lucid Lynx]("http://lgjsheron.wordpress.com/2010/07/06/how-to-speed-up-boot-of-ubuntu-10-04-lucid-lynx/")

---

### Post by cascade9 on 2010-07-27
> **TheNerdAL said:**
> After I installed a new hard drive, when I booted up into Ubuntu, it would give me this error: "failed command: WRITE DMA". 

I'd check your BIOS, you might have DMA turned off for that drive/channel.

---

### Post by TheNerdAL on 2010-07-27
> **cascade9 said:**
> I'd check your BIOS, you might have DMA turned off for that drive/channel.

Where would that be? o.o

---

### Post by cascade9 on 2010-07-27
> **TheNerdAL said:**
> Where would that be? o.o

Depends on your BIOS. 

I spose I could go looking for your motherboard model, then find out what type BIOS it uses, then go find out where the HDD settings are in the BIOS...but that would take me about 5 times longer than it would for you to look through the BIOS yourself. ;)

---

### Post by typal on 2010-07-27
> **TheNerdAL said:**
> Where would that be? o.o

When your computer is starting up, you should see a couple 'f' options on the screen. One for boot options, the other should get you to your BIOS. Usually f5, or something.

---

### Post by TheNerdAL on 2010-07-27
> **typal said:**
> When your computer is starting up, you should see a couple 'f' options on the screen. One for boot options, the other should get you to your BIOS. Usually f5, or something.

I'm not a noob. :P And I didn't find anything about DMA. My motherboard is quite old.

---

### Post by cascade9 on 2010-07-27
Your probably looking in the wrong place then.....

IIRC, you've got some horrid SiS chipset, so its (probably) in 

Intergrated Perpherials-> SiS IDE Device-> Primary Master (etc)-> UltraDMA. 

Like it is on this page (yes, its korean, doesnt make a difference for the BIOS settings)-

[http://www.ecs-korea.com/ecs/board.php?board=kkknewsmain&page=15&command=body&no=8](http://www.ecs-korea.com/ecs/board.php?board=kkknewsmain&page=15&command=body&no=8)

Edit- if you search for "Audio" on the page that link leads to (no quotes) the BIOS screenshot that shots the DMA settings should be the 1st hit.

---

### Post by TheNerdAL on 2010-07-27
> **cascade9 said:**
> Your probably looking in the wrong place then.....

IIRC, you've got some horrid SiS chipset, so its (probably) in 

Intergrated Perpherials-> SiS IDE Device-> Primary Master (etc)-> UltraDMA. 

Like it is on this page (yes, its korean, doesnt make a difference for the BIOS settings)-

[http://www.ecs-korea.com/ecs/board.php?board=kkknewsmain&page=15&command=body&no=8](http://www.ecs-korea.com/ecs/board.php?board=kkknewsmain&page=15&command=body&no=8)

Edit- if you search for "Audio" on the page that link leads to (no quotes) the BIOS screenshot that shots the DMA settings should be the 1st hit.

That's not how my BIOS looks like.

---

### Post by cascade9 on 2010-07-27
Then you've got a different BIOS type, but the options should still be there.

---

### Post by TheNerdAL on 2010-07-27
> **cascade9 said:**
> Then you've got a different BIOS type, but the options should still be there.

Nope, don't see it there. :(

---

### Post by cascade9 on 2010-07-27
It should be there. 

I forgot, you have a K8S-LA, which was made for compaq/hp, and therefore fidning the BIOS settings online is a pain.

---

### Post by TheNerdAL on 2010-07-27
> **cascade9 said:**
> It should be there. 

I forgot, you have a K8S-LA, which was made for compaq/hp, and therefore fidning the BIOS settings online is a pain.

Well it doesn't have many options. o.o

---

### Post by cascade9 on 2010-07-27
I'm 99% sure it would be there. 

BTW, you didnt add a SATA disc did you?

---

### Post by TheNerdAL on 2010-07-27
> **cascade9 said:**
> I'm 99% sure it would be there. 

BTW, you didnt add a SATA disc did you?

It's a PATA drive and when I click the hard drive in the BIOS, it only gives me two options that are set to auto.

---

### Post by cascade9 on 2010-07-27
That would probably be in the "IDE Drive Configuration Screen" but without actually seeing the BIOS, I dont know. 

Setting the UDMA mode is normally done from a different sceen. 

The only other thing I can think of is that you are runing a UDMA/ATA 66/100/133 drive on a 40 conductor IDE cable, not the 80 it should using....but from experweince, that should work, it just makes things much slower (it drops back to UDMA/ATA 33)

---

### Post by TheNerdAL on 2010-07-27
> **cascade9 said:**
> That would probably be in the "IDE Drive Configuration Screen" but without actually seeing the BIOS, I dont know. 

Setting the UDMA mode is normally done from a different sceen. 

The only other thing I can think of is that you are runing a UDMA/ATA 66/100/133 drive on a 40 conductor IDE cable, not the 80 it should using....but from experweince, that should work, it just makes things much slower (it drops back to UDMA/ATA 33)

Ahh, I did use the same cable from the previous hard drive on the new one. Would that be the cause?

---

### Post by cascade9 on 2010-07-27
Probably not, if you replaced the HDD with a new one. 

40 conductor cables have a more 'ridged' appearance, 80s look much more 'fine'. [IMG]http://www.pcstats.com/articleimages/200504/hddinstall_idecable.jpg[/IMG]

---

### Post by TheNerdAL on 2010-07-27
> **cascade9 said:**
> Probably not, if you replaced the HDD with a new one. 

40 conductor cables have a more 'ridged' appearance, 80s look much more 'fine'. [IMG]http://www.pcstats.com/articleimages/200504/hddinstall_idecable.jpg[/IMG]

So it's not the connector?

---

### Post by cascade9 on 2010-07-27
If its using a 80conductor cable, then it shouldn't be.

---

### Post by TheNerdAL on 2010-07-27
> **cascade9 said:**
> If its using a 80conductor cable, then it shouldn't be.

I think it's a 40conductor cable.

---

### Post by cascade9 on 2010-07-28
If its  40, then in theory it should just drop down to ATA33, but chipset weirdness has been known to happen.

---

### Post by TheNerdAL on 2010-07-28
> **cascade9 said:**
> If its  40, then in theory it should just drop down to ATA33, but chipset weirdness has been known to happen.

So getting a 80conductor cable would solve the problem?

---

### Post by cascade9 on 2010-07-28
Possibly, possibly not. Impossible to say. 

Odd that it would have a 40, if you had a ATA66+ drive in there originally it should have been an 80. 

I still think that there is a good chance its a BIOS settings problem.

---

### Post by varunendra on 2010-07-29
Why don't you post your BIOS version & HDD model? Maybe someone has experience with it & knows precisely if there is setting for DMA/UDMA in it or not!

One more thing I think you should make clear: did you have the same version of Ubuntu installed on the previous HDD booting faster? Trying a 80-conductor cable is also not a bad idea - just to make sure!! :)

---

### Post by TheNerdAL on 2010-07-29
> **varunendra said:**
> Why don't you post your BIOS version & HDD model? Maybe someone has experience with it & knows precisely if there is setting for DMA/UDMA in it or not!

One more thing I think you should make clear: did you have the same version of Ubuntu installed on the previous HDD booting faster? Trying a 80-conductor cable is also not a bad idea - just to make sure!! :)

I had 10.04 with my old hard drive, but the bad sectors on it kept growing so I got a new one and reinstalled 10.04.

---

### Post by varunendra on 2010-07-29
> **TheNerdAL said:**
> I had 10.04 with my old hard drive, but the bad sectors on it kept growing so I got a new one and reinstalled 10.04.
OK then, OS same, cable same and -if not altered manually- the BIOS settings too should be the same (please check & mention its version nevertheless). The only change is the HDD itself and possibly the criteria which Lucid is reinstalled with.

So what's the HDD model & BIOS version.

I don't have very good knowledge about these myself but supplying these info may yield you better suggestions.

---

### Post by TheNerdAL on 2010-07-29
> **varunendra said:**
> OK then, OS same, cable same and -if not altered manually- the BIOS settings too should be the same (please check & mention its version nevertheless). The only change is the HDD itself and possibly the criteria which Lucid is reinstalled with.

So what's the HDD model & BIOS version.

I don't have very good knowledge about these myself but supplying these info may yield you better suggestions.

WD Caviar Blue Desktop 3D3200JBRTL 320GB PATA ULTRA DMA/100 HARD DRIVE

I'll post the BIOS version when I reboot later because the reboot takes a long time. :P

---

### Post by cascade9 on 2010-07-29
Isnt there some issue with 10.04 reporting drive errors when they ay not exist? 

BTW, if you are using a 40 on the HDD...did you swap the cables when you rebuilt your computer? 

> **TheNerdAL said:**
> WD Caviar Blue Desktop 3D3200JBRTL 320GB PATA ULTRA DMA/100 HARD DRIVE

I'll post the BIOS version when I reboot later because the reboot takes a long time. :P

Wrong naming. 

Its actually a Western Digital Caviar SE WD3200JBRTL. (not a blue, and not a '3D3200', its 'WD3200').

Details, they are farily important in getting thjngs fixed, or building computers.

---

### Post by TheNerdAL on 2010-07-29
> **cascade9 said:**
> Isnt there some issue with 10.04 reporting drive errors when they ay not exist? 

BTW, if you are using a 40 on the HDD...did you swap the cables when you rebuilt your computer? 



Wrong naming. 

Its actually a Western Digital Caviar SE WD3200JBRTL. (not a blue, and not a '3D3200', its 'WD3200').

Details, they are farily important in getting thjngs fixed, or building computers.

Sorry, I guess I was tired while looking at the box. :P Well the BIOS version is 3.04. And I don't think I swapped cables when I rebuilt it.

---

### Post by cascade9 on 2010-07-29
I doubt that the BIOS version will make much difference.....not that you can tell what they have upgraded/fixed in the BIOS revisions, or at least I couldnt see a list of revisions. 

^&$%^ HP/Compaq.

---

### Post by varunendra on 2010-07-29
> **cascade9 said:**
> I doubt that the BIOS version will make much difference.....not that you can tell what they have upgraded/fixed in the BIOS revisions, or at least I couldnt see a list of revisions. 

^&$%^ HP/Compaq.

Ya, but maybe someone may realise that he/she has got the same BIOS and may tell if there is the mysterious DMA setting hidden somewhere in it....:-k

Or maybe it is just a bug???? (see [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/569680")) But if it were a bug, then the previous installation should have had the same problem, which is not the case (he hasn't mentioned it.... hmmmm)!

_**PS:**_ Ver. 3.04, but which BIOS is it? (award, phoenix,.... ??). I'll simply try to google for it based on the provided info.

---

### Post by cascade9 on 2010-07-29
> **varunendra said:**
> Ya, but maybe someone may realise that he/she has got the same BIOS and may tell if there is the mysterious DMA setting hidden somewhere in it....:-k

Its not just the BIOS type/version, its what the manufacturer has done with the BIOS. 

Its very common for 'corporate' manufacturers to strip out BIOS options (or, as in this case, Asus stripping out the optinos for someone). Mostly they remove things like overclocking options, etc, I havent heard of them remvoing the ATA/UDMA options, ever. 

I would guess that the options are either hiding somemore odd, or they have been given a name that makes TheNerdAl think 'thats not it'. 

BTW, its an award BIOS, and the product page is here- 

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00257657](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00257657)

---

### Post by varunendra on 2010-07-29
Wow! How do you know all that? Did he PM you or am I missing some post?

I thought he should have supplied all that info in one post (preferably in his first one) for all to see. However, given the research you've already done, it doesn't seem to make much sense now. :(

@TheNerdAl,
Does your BIOS look like [this]("http://www.computerhope.com/help/phoenixa.htm#04") one? This seems to have the DMA settings under label "ATA 66/100 IDE Cable Msg."
Maybe you've already tried it, but since it isn't mentioned in the thread so far..... ....

If it's not like yours, maybe posting screenshots of all the settings pages (taken from mobile??) may help us....8-[

---

### Post by cascade9 on 2010-07-29
> **varunendra said:**
> Wow! How do you know all that? Did he PM you or am I missing some post?

I thought he should have supplied all that info in one post (preferably in his first one) for all to see. However, given the research you've already done, it doesn't seem to make much sense now. :( 

I knew that because of a different thread, fairly old, where I was discussing hardware with TheNerdAl before. 

> **varunendra said:**
> 
@TheNerdAl,
Does your BIOS look like [this]("http://www.computerhope.com/help/phoenixa.htm#04") one? This seems to have the DMA settings under label "ATA 66/100 IDE Cable Msg."
Maybe you've already tried it, but since it isn't mentioned in the thread so far..... ....

If it's not like yours, maybe posting screenshots of all the settings pages (taken from mobile??) may help us....8-[

"ATA 66/100 IDE Cable Msg."is, I *think* a way to durn off ATA66/100 support. It should still run UDMA, just at a lower level. 

The way to set the UDMA levels should be under "SiS On Chip IDE Device" with the motherboard in that link (being a pheonix BIOS page, and the motherboard being used has a award BIOS, that doesnt mean much). 

Screenshots could help.

---

### Post by TheNerdAL on 2010-07-29
I found this on Google and that is what mine looks like: [http://h20000.www2.hp.com/bc/docs/support/SupportDocument/bph07110/c00814740.jpg](http://h20000.www2.hp.com/bc/docs/support/SupportDocument/bph07110/c00814740.jpg)

---

### Post by varunendra on 2010-07-29
What are the options under 'Advance' menu? Can you refer/post screenshots of the Advance menu (also sub-menus if possible)?
If you refer to some existing link, it should be exactly same as yours appears! Or it'd be better to post the screenshots of your own BIOS.

I know it may feel annoying, but is just a professional approach to be sure. It may help, maybe not! ;)

---

### Post by TheNerdAL on 2010-08-18
> **cascade9 said:**
> 
The only other thing I can think of is that you are runing a UDMA/ATA 66/100/133 drive on a 40 conductor IDE cable, not the 80 it should using....but from experweince, that should work, it just makes things much slower (it drops back to UDMA/ATA 33)

Would replacing my current 40 conductor cable with this 80 conductor cable help? 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812200039&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Cables-_-STARTECH-_-12200039](http://www.newegg.com/Product/Product.aspx?Item=N82E16812200039&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Cables-_-STARTECH-_-12200039)

Or does it have to be ULTRA-DMA?

---

### Post by TheNerdAL on 2010-10-09
Bump.

---

