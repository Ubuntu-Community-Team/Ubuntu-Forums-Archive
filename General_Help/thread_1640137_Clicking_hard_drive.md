---
title: "Clicking hard drive"
date: 2010-12-07
forum: General Help
---

### Post by sarsar on 2010-12-07
Hey guys, 

Ok, heres the background: Im running an Acer Aspire One netbook (not the new one, the one that came out 2/3 years ago) with 10.10 desktop edition (using GNOME not UNITY) with an 80GB hard drive i put in myself. Anyway last night my hard drive started clicking. Normally this requires me getting out the screwdrivers and reconnecting the ribbon cable. 

However i am currently living away from home and have no access to screw drivers. Stranger thing was when i turned the laptop on this morning it loaded straight away, normally when the hard drive clicks it defaults straight to boot menu. 

As of yet... the laptop is working fine, been running it all day with no restarts, using it as the fully fledged laptop it normally is. 

Could there be something else causing my hard drive to click? Does anyone else encounter this problem?

Thanks Sarsar

---

### Post by sarsar on 2010-12-07
By the way, its been clicking on and off for the past 2 days, EVERYTHING IS BACKED UP!!!! It was the first action i took.

---

### Post by rkillcrazy on 2010-12-07
> **sarsar said:**
> Hey guys, 

Ok, heres the background: Im running an Acer Aspire One netbook (not the new one, the one that came out 2/3 years ago) with 10.10 desktop edition (using GNOME not UNITY) with an 80GB hard drive i put in myself. Anyway last night my hard drive started clicking. Normally this requires me getting out the screwdrivers and reconnecting the ribbon cable. 

However i am currently living away from home and have no access to screw drivers. Stranger thing was when i turned the laptop on this morning it loaded straight away, normally when the hard drive clicks it defaults straight to boot menu. 

As of yet... the laptop is working fine, been running it all day with no restarts, using it as the fully fledged laptop it normally is. 

Could there be something else causing my hard drive to click? Does anyone else encounter this problem?

Thanks Sarsar

I've been doing hardware work for years.  In my experience, most clicking HDDs are toast!  Either this is a different clicking noise than I'm used to or you're quite the lucky one!  In most cases, the clicking meant I wasn't going to be recovering data from that drive!  I'd be backing up all I could, if I were you...

---

### Post by rkillcrazy on 2010-12-07
> **sarsar said:**
> By the way, its been clicking on and off for the past 2 days, EVERYTHING IS BACKED UP!!!! It was the first action i took.

In that case, I'd say replace the HDD (with an SSD?) ASAP.

---

### Post by sarsar on 2010-12-07
Ive still got the SSD! I will have to wait until i can get home [another week to last]. 

Ive got everything all backed up on memory sticks, through google docs, through ubuntu one. Im taking no chances. 

Its the normal terribly bad clicking noise. For some reason it hasn't died yet (ive reconnected the ribbon cable a few times as well). If i was to put a Hard Drive in it, which make would you recommend? Or would you say it was a bad idea?

---

### Post by matt_symes on 2010-12-07
Hi

If it has SMART capabilities check the drives health.

System->Administration->Disk Utility and select the  disk.

Does not sound good though.

Kind regards

---

### Post by sarsar on 2010-12-07
Done that: i have smart capability. It says: Disk has a few bad sectors

---

### Post by matt_symes on 2010-12-07
Hi

I would recommend choosing the same model hard drive you already have, even though this one sounds like its failing.

What is the current model?

Kind regards

---

### Post by rkillcrazy on 2010-12-07
> **sarsar said:**
> Ive still got the SSD! I will have to wait until i can get home [another week to last]. 

Ive got everything all backed up on memory sticks, through google docs, through ubuntu one. Im taking no chances. 

Its the normal terribly bad clicking noise. For some reason it hasn't died yet (ive reconnected the ribbon cable a few times as well). If i was to put a Hard Drive in it, which make would you recommend? Or would you say it was a bad idea?

Having never used many SSDs, I don't know what to recommend there.  We still use a lot of Western Digital HDDs in our shop. I'd hit up NewEgg & read, while always considering the source ;), as many reviews as you can prior to purchase.  Generally, those who have been making quality RAM for years have been doing well in the SSD market.  I've seen a few PNY SSDs floating around our shop over the past year or two.

---

### Post by sarsar on 2010-12-07
Just wondering guys, is it worth doing a file system check? And seeing if ubuntu can repair anything? Or is this a pure hardware problem. Its a bootable hard drive by the way. And i just realised its only a 60GB hard drive. In fact ill post it up here so people can see what im talking about.

---

### Post by rkillcrazy on 2010-12-07
> **sarsar said:**
> Just wondering guys, is it worth doing a file system check? And seeing if ubuntu can repair anything? Or is this a pure hardware problem. Its a bootable hard drive by the way. And i just realised its only a 60GB hard drive. In fact ill post it up here so people can see what im talking about.

No SFC has ever fixed a clicking HDD in my experience.  In fact, the extra load may cause it to fail sooner than later.  It's already on its way out so I wouldn't provoke it right now...

---

### Post by sarsar on 2010-12-07
Ok, so its not letting me upload my picture for some reason. But basically its a Samsung HS06THB.

---

### Post by sarsar on 2010-12-10
Just to close the post. 2 hours after posting this, the hard drive completely died. I have a new laptop now, its an Asus.Unfortunately it is on Windows (i managed to get xp, they were having a sale on seen as its now discontinued). Thanks for all the support, just so you all know its all backed up.

---

### Post by sarsar on 2010-12-23
I know im opening an old post, but there has been a development. Im finally home and had access to the screwdrivers. The whole issue is connected to the fan and battery. We managed to get the fan out and gave it a good clean.The battery is pretty much dead after 10 minutes of run time, the fan was dusty and had got badly clogged (that was actually doing the clicking, not the hard drive - i misdiagnosed it as when i put the hard drive in, we stuck it right next to the fan as it was the only place it would fit). Anyway, the battery was getting hot, everything was over working (seen as i do more on it than surf the net and write an odd document) and i believe it was an over heating issue, especially as even with a working fan, we are hitting critical levels after just 3 minutes. 

Going to fix the battery, by taking it apart and inserting new batteries into it. Just wondering, has anyone done this before? My father, has replaced batteries like this before,(hes an electrical engineer) and seems pretty confident we can get it back to full working order, just wondered if anyone had an advice/ success?

---

### Post by rkillcrazy on 2011-01-18
> **sarsar said:**
> Just to close the post. 2 hours after posting this, the hard drive completely died. I have a new laptop now, its an Asus.Unfortunately it is on Windows (i managed to get xp, they were having a sale on seen as its now discontinued). Thanks for all the support, just so you all know its all backed up.

There an easy, and not very intrusive, fix to your Windows problem....  Check out [Wubi]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer").

---

