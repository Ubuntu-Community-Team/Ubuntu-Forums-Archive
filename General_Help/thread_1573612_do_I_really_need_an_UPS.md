---
title: "do I really need an UPS?"
date: 2010-09-13
forum: General Help
---

### Post by ilna on 2010-09-13
My "hardware environment": sometimes AC voltage is above normal ~220-230V - up to ~250V. 

My "software demands": I don't perform any critical operation on the computer under question. The only aim is to be sure filesystems will be recovered after accidental power off. All partitions (except for /boot one) are ext4.

What do you think? What does your experience tell you?

---

### Post by CharlesA on 2010-09-13
Having backup power is almost always better then having no backup power.

As for me, I've got each of the machines at home (minus my htpc, that has no data stores on it) on UPSes.

Having a controlled shutdown is definitely better for yer data then a sudden outage.

---

### Post by ilna on 2010-09-13
> **CharlesA said:**
> Having backup power is almost always better then having no backup power.Agree :)
> **CharlesA said:**
> Having a controlled shutdown is definitely better for yer data then a sudden outage.As I have mentioned, the aim is to keep filesystems in clean healthy state, rather to prevent a loss of applications' data being writing.

---

### Post by CharlesA on 2010-09-13
> **ilna said:**
> As I have mentioned, the aim is to keep filesystems in clean healthy state, rather to prevent a loss of applications' data being writing.

The UPS will kick over to the battery if the line voltage is too high. That helps prevent spikes and surges from damaging components.

As for keeping the file systems healthy. It shouldn't really matter if you have a UPS or not, but if the power is lost when a file is being written, that file will be corrupted.

Best to run fsck after a power failure tbh.

---

### Post by v1ad on 2010-09-13
always wanted a UPS but those suckers are costly ... Someday.

---

### Post by ilna on 2010-09-13
> **CharlesA said:**
> that file will be corruptedCorrupted (or "incorrect", "invalid", "zero length") and "clean filesystem" are different terms, aren't they?

---

### Post by dcstar on 2010-09-13
> **ilna said:**
> My "hardware environment": sometimes AC voltage is above normal ~220-230V - up to ~250V. 

My "software demands": I don't perform any critical operation on the computer under question. The only aim is to be sure filesystems will be recovered after accidental power off. All partitions (except for /boot one) are ext4.

What do you think? What does your experience tell you?

An UPS continually consumes power itself, as well as costing money to obtain and keep operational (a new battery every 3 years or so), so you need a decent reason to have one. If you run a server that holds critical data then you should have one, otherwise.......

Modern PC power supplies can take from ~90VAC up to 280V without many issues (some may not even need to be manually switched from 110V to 220V).

---

### Post by CharlesA on 2010-09-13
> **ilna said:**
> Corrupted (or "incorrect", "invalid", "zero length") and "clean filesystem" are different terms, aren't they?

Are you referring to a "clean file system" like when you run fsck and it comes up as "clean" ?

---

### Post by ilna on 2010-09-13
> **CharlesA said:**
> Are you referring to a "clean file system" like when you run fsck and it comes up as "clean" ?Yes, I'm.

---

### Post by psusi on 2010-09-13
Not loosing my work and having to wait for a reboot because of a momentary brown out are reasons enough for me, and I don't consider $100 to be very expensive.  I'm still using the same CyberPower 1000 AVR I picked up about 8 years ago at best buy.  About every 3 years I order a pair of replacement batteries for $40.

---

### Post by ilna on 2010-09-13
> **psusi said:**
> Not loosing my work and having to wait for a reboot because of a momentary brown out are reasons enough for me, and I don't consider $100 to be very expensive.  I'm still using the same CyberPower 1000 AVR I picked up about 8 years ago at best buy.  About every 3 years I order a pair of replacement batteries for $40.
Agree. In fact, ATM I do have an UPS (CyberPower Value 500VA, above a year a little, reported as 240W by ups monitor). The thing is, recently I have upgraded hardware (motherboard, CPU, RAM, spent all current budjet :)), and at any peak (and mostly short) load ups monitor bothers me with notification about low battery runtime (2.5-3 minutes rather 8-10 minutes in idle state). And now I have dilemma - to spend extra cents for new (more power and, as a result, costly) ups, or to reject ups using at all. During this year there were 3-4 times ups worked in it's direct appointing.

---

### Post by migs73 on 2010-09-13
Did your UPS come on during a brown-out or loss of power, or when your input voltage spiked as you mentioned in your OP? If it is mainly spikes that are a problem there are many mains filters available that are considerably cheaper then UPS's, that'll do the same job.

---

### Post by ilna on 2010-09-13
> **migs73 said:**
> Did your UPS come on during a brown-out or loss of power, or when your input voltage spiked as you mentioned in your OP? If it is mainly spikes that are a problem there are many mains filters available that are considerably cheaper then UPS's, that'll do the same job.The UPS does swork without problems during these annoying notifications. As for AC - there are no spikes, rather continious rising at night hours. And have noticed at high input voltage output one is mutch lower - I think ups swicthes to battery during these high-voltage hours.

---

### Post by psusi on 2010-09-13
> **ilna said:**
> Agree. In fact, ATM I do have an UPS (CyberPower Value 500VA, above a year a little, reported as 240W by ups monitor). The thing is, recently I have upgraded hardware (motherboard, CPU, RAM, spent all current budjet :)), and at any peak (and mostly short) load ups monitor bothers me with notification about low battery runtime (2.5-3 minutes rather 8-10 minutes in idle state). And now I have dilemma - to spend extra cents for new (more power and, as a result, costly) ups, or to reject ups using at all. During this year there were 3-4 times ups worked in it's direct appointing.

Or you could just tell the monitor program to STFU ;)

---

### Post by migs73 on 2010-09-13
Here in the UK if your mains regularly tops 254V the electricity company responsible has to get it sorted, by law.
Where are you?

---

### Post by ilna on 2010-09-13
> **psusi said:**
> Or you could just tell the monitor program to STFU ;)I'm not great English expert and can not understand this abbreviation. Sorry. But I can imagine it is something like "stop to.. well, bother you". Is it correct? If it is the case - it is a shame, I have not found this ups monitor configuration value (I mean battery runtime limit to be named "low").

---

### Post by ilna on 2010-09-13
> **migs73 said:**
> Where are you?Probably, here, in small russian province, we live much more relaxed way :)

---

### Post by ilna on 2010-09-13
BTW, which ups monitor behavior/reports do you all use to judge about needeing to replace battery?

---

### Post by Zill on 2010-09-13
FWIW, having had power problems causing ext2/3 filesystem corruption *and* disk failures, I *did* install a new APC UPS a few years back.

I found it was more trouble than it was worth in our domestic environment as the thing would bleep and click due to the slightest power fluctuations that didn't bother the connected PCs at all.  This would wake up the household during the night and so it *had* to go!

Since then, I have been using the reiserfs file system with no UPS and everything has run perfectly.  After an outage the PCs just reboot quickly again with no apparent file corruption or disk damage.

Ext4 *might* be more resilient than ext2/3 but, personally, I will stick with reiserfs for as long as I can - it is far less trouble than a UPS IMHO.

---

### Post by ilna on 2010-09-13
> **Zill said:**
> Ext4 *might* be more resilient than ext2/3 but, personally, I will stick with reiserfs for as long as I can - it is far less trouble than a UPS IMHO.Have you, please, own use cases or some hrefs related to ext4 and reiserfs comparison (I mean current thread's context)?

---

### Post by msandoy on 2010-09-13
A UPS does more than just give you time to save your work. I have had power supply failures, network card failures, Main board failures due to power spikes. The power supply in my computer alone cost 200$, the UPS only cost 110$ It's a cheap offline version, and it will protect all the equipment from lightning and other spikes on the power grid. After buying the UPS 5 years ago, I have not had any failing equipment. And best of all, I still have internet when the power is out, for as long as I have battery power on my laptop. The ADSL modem and network router has it's own UPS.

---

### Post by Zill on 2010-09-13
> **ilna said:**
> Have you, please, own use cases or some hrefs related to ext4 and reiserfs comparison (I mean current thread's context)?
I can only advise based on my personal experience that I had problems after power outages when using ext2 and ext3 systems.  This did lead to boot problems with mysterious inode messages that were very difficult to clear using fsck tools etc.  In a couple of cases I did end up replacing the HDDs as the filesystem seemed unrepairable.

However, since switching to reiserfs, these problems simply do not occur - I have installed this fs on about six PCs with several versions of Linux and "it just works". :-)

I have no experience of ext4.

---

### Post by dcstar on 2010-09-14
> **ilna said:**
> The UPS does swork without problems during these annoying notifications. As for AC - there are no spikes, rather continious rising at night hours. And have noticed at high input voltage output one is mutch lower - I think ups swicthes to battery during these high-voltage hours.

There are basically 3 types of UPS that are available, Standby, Line-interactive & Online.

Unless you have the most expensive type - Online - then you will not get any voltage regulation as the other types are basically back-up power sources in case of power failure.

Many cheap UPSs are not true Online devices, and people fool themselves into thinking that they have something that protects them more that the device actually does.

Read more here: [http://www.pcguide.com/ref/power/ext/ups/types.htm](http://www.pcguide.com/ref/power/ext/ups/types.htm)

---

### Post by psusi on 2010-09-14
> **dcstar said:**
> There are basically 3 types of UPS that are available, Standby, Line-interactive & Online.

Unless you have the most expensive type - Online - then you will not get any voltage regulation as the other types are basically back-up power sources in case of power failure.

Many cheap UPSs are not true Online devices, and people fool themselves into thinking that they have something that protects them more that the device actually does.

Read more here: [http://www.pcguide.com/ref/power/ext/ups/types.htm](http://www.pcguide.com/ref/power/ext/ups/types.htm)

That is incorrect.  Even the most basic standby models will still kick over to battery if the line voltage gets out of the acceptable range.  They just don't keep it tightly regulated like the expensive ones do.  Of course, there really is no reason to do that other than a marketing gimmick to charge more for the UPS, since power supplies are designed to operate correctly over that entire voltage range, and shut down if the voltage gets outside it.

---

### Post by ilna on 2010-09-14
> **dcstar said:**
> There are basically 3 types of UPS that are available, Standby, Line-interactive & Online.

I don't see any contradiction (I mean that cited fragment of my message).

---

### Post by dcstar on 2010-09-15
> **psusi said:**
> That is incorrect.  Even the most basic standby models will still kick over to battery if the line voltage gets out of the acceptable range.  They just don't keep it tightly regulated like the expensive ones do.  Of course, there really is no reason to do that other than a marketing gimmick to charge more for the UPS, since power supplies are designed to operate correctly over that entire voltage range, and shut down if the voltage gets outside it.

The difference in how an UPS outputs is critical in many situations. **Only** an Online UPS will provide a continuous output regardless of what happens to the main input.

Other types of UPS may well kick in to **replace** the mains power when the conditions arise, but there is no guarantee that the changeover will not have any gaps or will be in phase with the previous mains supply.

Maybe your equipment can handle irregular power when an UPS kicks in, maybe it won't. Maybe the worst thing possible will occur and your equipment will seem to be working correctly even though the power spike caused by the changeover actually has caused a problem but not a big enough problem to totally reset or crash the equipment.

IT professionals know this and there are very good reasons why Online UPS systems are used in mission critical situations, and why they cost more.

---

### Post by ilna on 2010-09-15
> **dcstar said:**
> The difference in how an UPS outputs is critical in many situations. **Only** an Online UPS will provide a continuous output regardless of what happens to the main input.

Other types of UPS may well kick in to **replace** the mains power when the conditions arise, but there is no guarantee that the changeover will not have any gaps or will be in phase with the previous mains supply.

Maybe your equipment can handle irregular power when an UPS kicks in, maybe it won't. Maybe the worst thing possible will occur and your equipment will seem to be working correctly even though the power spike caused by the changeover actually has caused a problem but not a big enough problem to totally reset or crash the equipment.

IT professionals know this and there are very good reasons why Online UPS systems are used in mission critical situations, and why they cost more.
Yes, there is 2-5mS switching gap. But I have not see even a single report a UPS-switching causes a problem - I mean consumers with switching PSU (PC, monitor, ...). There is another problem - UPS must supply a peak current needed to start PSU. It arises a wellknown problem of "UPS and PSU compatibility". And, unfortunately, it is common manufacturers practice to omit this parameter in specifications, provoking additional heap around PC hardware :)

//-------------------

OK, I have educated enough to order (done) new UPS :)

---

### Post by FahadMKS on 2010-09-15
Always use an UPS, it is always best for the Computer.

It will help you to prevent the damages on the HDD as well as the SMPS(Power Supply on the computer)

---

### Post by ilna on 2010-09-15
> **FahadMKS said:**
> Always use an UPS, it is always best for the Computer.

It will help you to prevent the damages on the HDD as well as the SMPS(Power Supply on the computer)
The aim of the thread is to understand rather to share banal slogans ;)

---

### Post by psusi on 2010-09-15
> **dcstar said:**
> The difference in how an UPS outputs is critical in many situations. **Only** an Online UPS will provide a continuous output regardless of what happens to the main input.

Other types of UPS may well kick in to **replace** the mains power when the conditions arise, but there is no guarantee that the changeover will not have any gaps or will be in phase with the previous mains supply.

While this is true, it does not matter one bit.  Power supplies simply do not care.

> **dcstar said:**
> Maybe your equipment can handle irregular power when an UPS kicks in, maybe it won't. Maybe the worst thing possible will occur and your equipment will seem to be working correctly even though the power spike caused by the changeover actually has caused a problem but not a big enough problem to totally reset or crash the equipment.

There isn't any maybe about it.  The supply is designed to handle it.  There is enough l-c ( inductance and capacitance ) in a power supply to ride out a few ms drop.  I once had a server with an oversized supply ride out a brownout that was long enough for the lights to noticeably go out, so about 300+ms.  An offline UPS makes the switch in about 15ms.

> **dcstar said:**
> IT professionals know this and there are very good reasons why Online UPS systems are used in mission critical situations, and why they cost more.

No, ones that have been duped by marketing buzzwords *believe* this.  There is no evidence that it is actually true, and quite a bit that it is not.  Just because people buy snakeoil and believe it works doesn't mean it does.

---

