---
title: "Failure to boot"
date: 2010-11-01
forum: General Help
---

### Post by Sylos on 2010-11-01
So I turn on my pc today, select ubuntu studio from GRUB and it freezes during the splash sequence - I hard shut down and the power back on and..........

.....nothing.

Hard drive light illuminates once then stays off. External HDD powers on. Processor light comes on but no graphics - no manufacturer stuff, no bios entry - nothing.

Anyone got any good ideas as to why this might be happening? Seems to have ominous hardware implications.

Thanks

---

### Post by TeoBigusGeekus on 2010-11-01
Take it out of the plug and press the power button for 5~10 secs.
Plug it again and try to boot.

---

### Post by Sylos on 2010-11-01
Sadly that didnt work. Now the processor light doesnt flicker either.

Could it be bad RAM?

---

### Post by TeoBigusGeekus on 2010-11-01
Even in the case of bad ram you would get something on screen.
Anyway, I think it's a hardware failure. 
Open up your box, detach and reattach whatever you can: ram, hds, power supply, etc. There's a chance that this will unblock your hardware.
...otherwise, I think it's either a destroyed graphics card and/or cpu  and/or (worst case) a fried motherboard.
Cross your fingers...

EDIT: Detach and reattach the motherboard's battery as well.

---

### Post by matt_symes on 2010-11-01
Hi

Sounds like some kind of hardware failure. Can you boot with a live CD? If so, you can run some hardware tests. Hard drive, memory etc the usual tests.

Kind regards

---

### Post by Sylos on 2010-11-01
matt_symes - already been there with the Live CD - i was a no go - the drive spins but nobody's home. Cheers anyway.

TeoBigusGeekus - already tried disconnecting the HDDs and drives but I guess its time to hit the rest. Damn I hope it isnt my sound card - that will be painful and expensive.

I may well be back with more info....


Thanks

---

### Post by coffeecat on 2010-11-01
> **TeoBigusGeekus said:**
> ...otherwise, I think it's either a destroyed graphics card and/or cpu  and/or (worse case) a fried motherboard.

I'll be slightly more optimistic. It could be a failing - but now failed - power supply. I saw something similar with a failing power supply - odd whirrings and lights, but not enough power to get the system booting up properly. With everything now dead it could be that the PSU failed completely.

Do you have another PSU to try?

---

### Post by matt_symes on 2010-11-01
Hi 

+1 coffeecat. Worth checking out the PSU. Do you have a multimeter? Check the supply with that

Kind regards

---

### Post by oldfred on 2010-11-01
After replacing power supply, motherboard and then video card, my system booted. I then looked closely at video card (Nvidia 7600) and I could see several capacitors were open, not flat/sealed on top. I did want new motherboard, but did not really need new power supply.

Shows not very good picture:
[http://yipcanjo.wordpress.com/2008/09/15/happy-monday/](http://yipcanjo.wordpress.com/2008/09/15/happy-monday/)

---

### Post by matt_symes on 2010-11-01
Hi

Blimey old fred, Did you take that back? That is shoddy workmanship. Another thing worth checking though. 

Kind regards

---

### Post by Sylos on 2010-11-01
Thanks for all the replies.

It turns out the culprit is..........(drum roll)....


A fried RAM stick.

I suspect this happened during the repeated power cuts we had last night. I went to turn it off as soon as it happened but the power had already tripped on/off about 5 times when i got there. I wonder if british (g)*** are going to refund me for 512mb of RAM ruined by their poorly maintained electricity supply network - No - I think not.

Oh well - guess I should be happy it wasnt something more valuable.

Now all that remains is to get through the disk errors I am getting on boot and we may be back in business.

Thanks everyone...

---

### Post by matt_symes on 2010-11-01
Hi

Maybe consider a UPS?

Kind regards

---

### Post by Sylos on 2010-11-01
Sorry, not sure what that is.

Can you elaborate.

---

### Post by TeoBigusGeekus on 2010-11-01
[http://en.wikipedia.org/wiki/Uninterruptible_power_supply]("http://en.wikipedia.org/wiki/Uninterruptible_power_supply")

Their prices have fallen the last few years. You can buy a decent one relatively cheap.

EDIT: Ram eh? Who would've thought... I had the impression that something would pop up on the screen even with bad ram. 
You learn something every day. :)

---

### Post by Sylos on 2010-11-01
Definitely gonna look into that.

Are surge protectors worth anything or not? (I have two but they are currently protecting higher value musical equipment)

---

### Post by TeoBigusGeekus on 2010-11-01
> **Sylos said:**
> Are surge protectors worth anything or not?

They can be of use in case of (minor) fluctuations in the power supply, but in case of total power failures they do nothing. 
Go for a UPS.

---

### Post by westom1 on 2010-11-01
[COLOR=black][FONT=Verdana]> **Sylos said:**
> Definitely gonna look into that.[/FONT][/COLOR]> **Sylos said:**
> 
 
[COLOR=black][FONT=Verdana]Are surge protectors worth anything or not? [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]View manufacturer spec numbers for those protectors. Where does it list protection from each type of surge? It does not. It is a £2 power strip with some ten cent protector parts that is selling for how much? Wouldn't you love to have that profit margin?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]UPS spec numbers list even less protection. Again, view numbers such as joules. A destructive surge is hundreds of thousands of joules. If a UPS has hundreds joules protection, then that near zero protection can be hyped to the naive as 100% protection. That is how myths are promoted by most without basic electrical knowledge and who ignore those manufacturer spec numbers.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]A power strip protector does nothing, may even contribute to appliance damage, and requires protection only provided by earthing one 'whole house' protector. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]UPS has only one function - to provide temporary power during a blackout. Again, view its spec numbers. All those other things people recommend a UPS to do are near zero. UPS switches to battery when voltage gets too low. And leaves electronics connected directly to AC mains when voltage is normal or excessive. UPS also needs protection from that one and properly earthed 'whole house' protector. The effective solution ends up costing tens or 100 times less money.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]View output of typical UPS when in battery backup mode. A 230 volt UPS can output 400 volt square waves with a spike exceeding 500 volts between those square waves. That is potentially harmful to small electric motors and power strip protectors. And why UPS manufacturers recommend no laser printers or power strip protectors on their UPS output. Power from a UPS in battery backup mode is some of the &#8216;dirtiest&#8217;. And that same power is perfectly ideal for all electronics. Why? Because electronics are so robust. Because a power supply is supposed to make that and so many other anomalies irrelevant. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Most functions performed by a UPS can performed better inside electronic supplies. That makes the 'dirtiest' power from a UPS irrelevant to electronics. That means when incandescent lamps dim to 50% intensity, that is also perfectly ideal power to all electronics. A UPS has one useful function. Provide temporary and dirty power during a blackout.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Minor fluctuations (bulbs dimming less than 50%) are completely irrelevant to any properly constructed computer. But with so many electrically naive computer assemblers selecting a supply only on money and watts, many supplies are dumped into the market missing essential internal functions. To sell that supply for £10 less, then many will recommend buying an £80 UPS to 'fix' it.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Had you measured as matt_sym recommended, then what caused your failure could be known. Power cycling does not cause hardware damage. But other problems (transients, defective power supply, etc) can, in cooperation with power loss, cause such failures. RAM is not even on the long suspect list. IOW this reply could also say what has failed or what is 100% good - without all those other 'it could be that' or 'might be this' posts. Another example of why numbers result in definitive answers.[/FONT][/COLOR]

---

### Post by matt_symes on 2010-11-01
Hi

@wetsom1. UPS's have been installed at _every_ company i have ever worked at and for a reason.

if unreliable power supply is an issue then that is the recommended solution. It gives time for the generators to kick in.

Kind regards

---

### Post by westom1 on 2010-11-01
[COLOR=black][FONT=Verdana]> **matt_symes said:**
>  UPS's have been installed at _every_ company i have ever worked at and for a reason.  Many locations with 'unreliable power' and the UPS did nothing.   Which 'unreliable' is to be solved?  Layman's terms are useless for defining a solution.  First define what problem must be solved.  Only then is a solution for that problem implemented.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  UPS is installed to only eliminate one problem.  To protect data from blackouts.  Show me a spec number for a battery backup UPS that claims anything else?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  Now, some companies install completely different UPSes to solve other problems.  Those cannot exist adjacent to a desk.  But again, there is no magic box that solves everything.  Different power anomalies get solved at different locations.  Temporary and 'dirty' power so that blackouts do not erase unsaved data.  A cheapest UPS does that and only that.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] What applies some of the 'dirtiest' power to computer hardware?  That same UPS.  A different anomaly solved inside every computer power supply long before the IBM PC even existed.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[SIZE=3][FONT=Times New Roman]  Why does a UPS exist?  Its existence says nothing useful.  May say the plant manager is easily scammed.   Always required are hard technical reasons why – with numbers.  What does that UPS solve?  Only answered in numeric specifications.[/FONT][/SIZE]

---

### Post by matt_symes on 2010-11-01
Hi

This is totally off topic and adds nothing to the OP. If you think UPS is an issue then start another thread.

You are entitled to your own opinion. No problem :)

Kind regards

---

### Post by Sylos on 2010-11-02
westom1 - Thanks for the post. I (obviously) am not very well up on the hardware side of my PC or general electronic engineering. Its been a long time since my electronics GCSE and I can barely remember which way up to hold a multimeter - which I no longer have anyway.

I know the only real way to find the source of the problem is take meter readings from the PSU connectors and at the relevant points on the board but my problem is: (a) dont have a meter and (b) wouldnt really know where to take the readings from wihtout causing more damage than good. 

I found by trial and error (removing each component and then trying to boot) that a stick of RAM was 'causing' the boot failure. I know your going to say that it may not be the real cause as this could be elsewhere due to another malfunction but I fear the destructive power of my further meddling. At the moment I have it working again with an old 256mb stick in the slot the dud came from and it appears ok. Part of me says I ought to find if another fault was the cause and part says if it aint broke....

I would ask you comments on this though - following the replacement of the RAM I found that both of my HDDs reported corruption at the boot sequence on both OS's I have installed. At the risk of you beating my skull with a multimeter I ask if that still sounds like PSU issues?

One final question - wouldnt a PSU just stop my PC going down. My ignorance believes that this wouldnt fry anything - only result in potential data loss. The frying (if it actually ever occurs) would be when the surge hits when it comes back on. Would the UPS stop that surge. Sorry if you already stated that but it isnt so clear to me.


Many Thanks to all

---

### Post by coffeecat on 2010-11-02
> **Sylos said:**
> following the replacement of the RAM I found that both of my HDDs reported corruption at the boot sequence on both OS's I have installed.

You had to do a hard shutdown when the problem first occurred. I would put my money on filesystem corruption in one or more partitions. Try a fsck on the partition(s) being reported as corrupted.

---

### Post by Sylos on 2010-11-02
Cheers Coffecat - I already did the fsck route having been prompted at boot time and all appears to have been fixed without my fumbling manual intervention (thank god). Still intrigued as the reason of the RAM failure. I guess it could just be coincidence that it failed just after the power failure. I suppose the fact that it began to boot the first time and then failed might suggest that it failed post power fluctuations. What do you think?

---

### Post by coffeecat on 2010-11-02
> **Sylos said:**
> What do you think?

Hmmm. Pass. Sorry. I've been unlucky enough to buy  a dodgy RAM stick which merely caused system freezes, but never had one fail spectacularly like that.

---

### Post by westom1 on 2010-11-02
[COLOR=black][FONT=Arial]> **Sylos said:**
>   I know the only real way to find the source of the problem is take meter readings from the PSU connectors and at the relevant points on the board but my problem is: (a) dont have a meter and (b) wouldnt really know where to take the readings from wihtout causing more damage than good. [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]I found by trial and error (removing each component and then trying to boot) that a stick of RAM was 'causing' the boot failure.  ... [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]I would ask you comments on this though - following the replacement of the RAM I found that both of my HDDs reported corruption at the boot sequence on both OS's I have installed. ... [/FONT][/COLOR]
[COLOR=black][FONT=Arial]One final question - wouldnt a PSU just stop my PC going down. My ignorance believes that this wouldnt fry anything - only result in potential data loss. [/FONT][/COLOR]
[COLOR=black][FONT=Arial] First, only thing meter probe can cause damage is a moving fan.  The procedure is clear and simple. Touch nothing on the board.  Only touch six wires inside a nylon connector – one minute of labor - to learn more facts than most all previous posts.  You need not (yet) know why or what those numbers report.  Having not done that, I cannot provide any useful information.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Moving on.  Shotgunning (must labor that puts all hardware at greatest risk) eventually implies a Ram, voltage to that Ram, or defectve ICs adjacent to that Ram.  A replaced Ram does not necessary mean the problem was that Ram.  However, a better method to find before replacing a defect is to use another powerful diagnostic tool - heat.  All semiconductors work at many perfectly ideal temperatures including well above 100 degrees F.  Use a hairdryer (or a hot summer room) is when memory diagnostics are best executed.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  For example, if a Northbridge circuit is defective (marginal and slowly getting worse), then heat would cause expose interface circuits when tested by a comprehensive hardware diagnostic.   Heat is especially useful in finding defective hardware before that hardware has yet caused crashes. To find defects months before intermittent failures start happening.  A technique long used (for generations) when failure must never happen - ie flight hardware.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Unfortunately, those who know only from observation see heat cause a failure.  Then cure symptoms - install more fans.  Amother example of why conclusions based only from observation - without underlying knowledge - results in popular myths and confusion. Your computer must work perfectly fine even in a room above 100 degrees F.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Most chips will work perfectly fine when voltages are defective.  Which could explain why only one chip (that Ram) might fail.  But chances are that you have found the defect.  A conclusion that can be confirmed by heating the RAM (and adjacent ICs) with a hairdryer on highest heat settings.  All electronics work fine even when heated to temperatures that are uncomfortable to touch.  Executing a comprehensive memory diagnostic (from the computer manufacturer or from a third party such as Memtst86) during higher temperatures is a powerful diagnostic.  How it was done long before PCs existed.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Could a voltage problem also corrupt disk data?  Yes.  But extremely unlikely.  Disk drives are never told that power is turning off.   Disk drives first learn about power off when voltages drop.  So a disk drive’s computer finishes what it is doing and prepares for further voltage decreases.  Yes, all power offs are completely unexpected to disk drives.  Low voltage (due to shutdown, yanking a cord from the wall, or statewide blackout) get the exact same response from a drive.  Which is also why low voltage is less likely to have corrupted disk data.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Better information would be possible if details of your disk corruption (ie facts and numbers from the disk diagnostic) were known.  And if details from the memory diagnostics said what exactly failed in that Ram.  With almost no information, we can only speculate that data corrupted by that RAM was written to each disk.   Without hard facts, the only thing we can do is speculate using knowledge about how computers work.  That computer knowledge is the difference between speculation and wild speculation.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Nothing done by a meter or by executing a memory diagnostics with heat will cause any damage.  But it could identify or avert future failures.  And might explain why you had failures.  Unfortunately too much as changed.  Too much useful information has been destroyed.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Of course, if the system now boots, you still have facts from the system (event) logs.  Windows finds problems, records the failure, then works around problems.  One reason why Windows is such a poor diagnostic tool and why those event logs are so critically important facts.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  And finally, not having a meter was not really true.  Because meters can (and are) used by 12 year olds, then they are available in most any store that sells hammers.   Also in K-mart and Wal-Mart for prices typically less than hammers.  Most people will not use the meter for only one reason - fear.  Far more dangerous than a digital multimeter are fans inside every computer.  But a majority would rather fear the meter only because so many have never touched one. Ignorance and fear of something so less dangerous than a hammer is the only reason why most will not use a meter.  Most every shopping center has at least one store that sells one because even 12 year old can use it.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Power supply - a functioning power supply either provides sufficient voltage or requests a power controller to turn it off.  A defective supply will boot and run a computer for months - then cause strange and intermittent crashes months later.  Generally data is not corrupted.  The computer crashes or a drive stops operating bluntly before disk data can be corrupted.  Filesystems are further redundant so that data corruption is eliminated.  Long before you might see data corruption, a drive (ie with SMART) will have been reporting data errors.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial] I speculate that your failures have what most all failures have - a common source.  In you case,  RAM or inputs to that RAM (interface chips or voltage).[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]   This is a short summary of how much is included in my analysis when you provide hard facts such as details from a comprehensive memory diagnostic or voltages from the meter.  With each hard fact, the same post becomes paragraphs shorter.  And speculation instead is a definitive answer. The reason for a longer post - no hard facts and no numbers were provided.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]   There is no surge due to power cycling.  That myth is from many who feel a surge must exist because advertising or friends tell them to believe.  Same myths that blame power cycling also blame heat.    A surge is a high voltage.  If your power supply is minimally acceptable (even meets standards that existed before an IBM PC existed), then a high DC voltage is virutally impossible.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  Surges exist when one without facts or with insuffficient knowledge saw a failure.  Then uses hearsay to blame something.  There is no power on surge.  Surges occur typically once every seven years.   And yet so many know it must have been a surge because surges happen every five minutes – the urban myth.  You appear to have a classic manufacturing defect.  And it may have been detectable even days or months before it finally caused a hard failure.  But again, more paragraphs due to generations of knowledge and experience combined with symptoms and insufficient hard facts.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]  To have a useful answer would mean executing diagnostics and getting numbers.  Otherwise just keep using the machine and doing lots of backups.[/FONT][/COLOR]
[COLOR=black][FONT=Arial][/FONT][/COLOR] 
[COLOR=black][FONT=Arial]  Provided are many ideas to obtain a more useful answer here.  Without hard facts, the best you can hope for is only speculation based in industry knowledge.  Or wild speculation based in hearsay.[/FONT][/COLOR]
[COLOR=black][FONT=Arial][/FONT][/COLOR] 
[COLOR=black][FONT=Arial]  If betting, you may have found a problem (the Ram) created by a manufacturering defect.[/FONT][/COLOR]
[COLOR=black][FONT=Arial][/FONT][/COLOR]

---

### Post by Sylos on 2010-11-03
> And finally, not having a meter was not really true. Because meters can (and are) used by 12 year olds, then they are available in most any store that sells hammers

An inescapable truth. I shall hopefully acquire a meter tomorrow and carry out the tests and post the results. I assume that to do the tests I should leave the supply connected to the MB and push the meter probe in the back of the connector?

Thanks for the help. Hopefully tomorrow I will have more info.

---

### Post by alphaamanitin on 2010-11-03
Does your computer Post?

AlphaA

---

### Post by Sylos on 2010-11-04
AlphaA - yes thanks - it is now booting ok - further investigation is now about making sure that there isnt another fault waiting blow more sticks of my precious RAM (when your computer is as old as mine every Kb counts).

Thanks

---

### Post by Quackers on 2010-11-04
I had to throw a ram stick away about a month ago. It had been fine for 2 years or more then one day BSOD with a 07D stop error (I think it was). It's been fine since then. It happens, I suppose.

---

### Post by alphaamanitin on 2010-11-04
I feel your pain man.  My girlfriends computer's power supply went and took the processor and ram with it.  Ended up just building her a new computer.  She is death on computers, not her fault of anything stupid, just bad luck.  PS died, three DVD drives died after 3 month, and latest was HD failure.  Now I have built her two computers in the last two years.  

AlphaA

---

### Post by westom1 on 2010-11-04
> **alphaamanitin said:**
> I feel your pain man. My girlfriends computer's power supply went and took the processor and ram with it. 
That is only possible when the computer is built with parts that violate industry standards that even predate the IBM PC. Somehow a power supply voltage was so massive as to then blow out the CPU's power supply? And protection in that CPU power supply did not exist so that the CPU was destroyed? Well, this does happen because so many computer assemblers have no electrical knowledge. These people make is extremely profitable for dumping of inferior parts into the domestic market.
 
Standard for any computer. A power supply failure must never cause component parts. A component parts must never cause power supply failure. By not providing these required functions (because so many assemlbers do not understand or read numeric specs), then a supply selling for a lower price also has a higher profit margin.
 
How to find a Ram stick that will be defective many months later? Heat routinely used in conjunction with a comprehensive hardware diagnostics to find completely defective parts that still boot and run a computer. Defective parts that will become worse with time.

---

### Post by alphaamanitin on 2010-11-05
> **westom1 said:**
> That is only possible when the computer is built with parts that violate industry standards that even predate the IBM PC... 


The original was a very cheap E-machines computer.  As for her other problems, I don't know.  I do know she does not do anything stupid, like cover up the fan vents, but I don't have the time to chase all this stuff down.  I am a PhD Biology student, not a Computer Science student.

But now this thread is getting off topic so...

AlphaA

---

### Post by westom1 on 2010-11-05
[COLOR=black][FONT=Verdana]> **alphaamanitin said:**
>  The original was a very cheap E-machines computer. As for her other problems, I don't know. I do know she does not do anything stupid, like cover up the fan vents, ...  Do engineering numbers. A covered chassis vent means a computer works just fine as long as air outside the chassis is 70 degrees F. One chassis fan means the same computer also works fine in a 100 degree F room.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]With gentle interior airflow, then any properly constructed computer should work just fine. Too many foolishly blame hardware damage on heat. A myth based in hearsay; not from learning hard facts. Tens of degree temperature differences causes no hardware damage. But that same trivial temperature change can identify defective components and marginal designs. Those trivial temperature changes can cause enough timing, threshold, or other temporary changes as to cause a system crash. No damage. Just a crash. A crash due to a 100 degree F room implies defective hardware when purchased and when it was also working OK at 70 degrees.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Heat is a diagnostic tool to locate defective hardware. Other examples of defective hardware that appears to work OK include a power supply that boots and runs a computer. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]What temperatures cause hardware damage? From a most recent issue of Electronic Products magazine. "Transistors are typically known to deteriorate at 250 degree C and leak electrons excite by those high temperatures." Not a surprise to anyone who learned about and designed hardware. How do trivial temperature (tens of degrees) changes cause hardware damage? They don't.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Most computer defects are traceable to manufacturing defects. Myths will blame surges, heat, and malware when existing is insufficient knowledge, hard facts, and experience. Better computer manufacturers trace their components to each manufacturer just to diminish a serious reason for failures. In a market where computers are constructed with 'dumped' parts, higher failures are observed by consumers and consumer magazines to be higher.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Obstructed chassis fan did not cause hardware damage. To have damage means the semiconductor junction temepratures must approach 450 degrees F. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]BTW, sometimes I will even fix a supply or PC board just to confirm the reason for failure. This e-Machine that I will restore to operation has a PCI bridge failure. How often do you trace failure to the actual defect?[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Just another reason why little respect applies to so many who would blame heat for semiconductor failure. Blame only using wild speculation. Blame without first learning facts. Trivial temperature increases do not cause hardware failures. But those trivial temperature increases (a powerful diagnostic) can identify hardware that was always defective.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]  An old engineering technique even when semiconductors were no where near as robust as they are today.  If you touch it and do not leave skin, then it is not too hot.  I also doubted that back then.  After so many decades of experience - I am repeating what they taught me.  You can confirm same by learning from numbers; not from hearsay.[/FONT][/COLOR]

---

### Post by alphaamanitin on 2010-11-06
Well, since I think this thread is kind of dead I will respond.  Anyway, when the first computer died I thought it was the ram, so I bought new ram.  It still didn't work.  I borrowed a power supply and then it would post but do nothing else.  Finally I just decided I would just build a new computer since her old one was crappy anyway.  Recently her computer started randomly freezing up, so I thought processor or hard drives maybe.  I decided to upgrade her computer and bought a new motherboard with dual core 3.0 Phenom II.  But I bought the wrong form MOBO for her case because I was not paying attention, and just built her an awesome new computer, for her that is.  

I wish I was better about actual computer engineering but I don't have time with my biology PhD program to really work on it.

AlphaA

---

### Post by westom1 on 2010-11-07
[COLOR=black][FONT=Verdana]> **alphaamanitin said:**
>  Anyway, when the first computer died I thought it was the ram, so I bought new ram. It still didn't work. I borrowed a power supply and then it would post but do nothing else. ... so I thought processor or hard drives maybe. Spending so much time and money is traceable to violating fundamental analysis as even described in fiction of CSI, "Follow the evidence." Arbitrarily selecting some suspect to blame only caused confusion. Shotgunning will even get a car mechanic fired.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Now, a first thing that can make everything else appear bad is the power system. Not just a supply. The system has many components. So a first thing done - and this only takes a minute - is to collect voltages from six wires between the power supply and motherboard. Voltages before and when the power switch is pressed. And voltages when the system is accessing (multitasking to) every component simultaneously.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Those numbers are full of too much information to summarize here. However, those numbers (to three digits) means the entire power system can be exonerated or a selected component becomes an obvious suspect. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Once a power system is exonerated, only then move on to other suspects. That includes history from the event (system) logs, comprehensive hardware diagnostics, and using other powerful diagnostic tools such as heat. Windows is often a poor hardware tool because Windows works around and avoids hardware problems.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]A first hardware part replaced is first identified as defective by simple tools and procedures. And without any speculation. Again, follow the evidence.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Meanwhile how a computer fails also says so much about the suspects. For example, if a system crashes, the list of suspects is short and obvious. If memory was on that list, then you know from system (event) logs or from a BSOD message. If not, memory obviously did not cause that fault. Memory exonerated from a very short suspect list.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]To find a problem means first taking voltage measurements. Otherwise perfectly good components act defective. Also consult system (event) logs and Device Manager. And perform comprehensive hardware diagnostics. Easiest when your computer is from the fewer and more responsible computer manufacturers who provide diagnostics for free on the computer, on a CD, and on their web site.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Summarized is how to avoid and why you should not have been using wild speculation to replace what were probably perfectly good parts.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]And finally, a perfectly good power supply can appear defective in some systems. A defective power supply can still boot some computers. Examples of why swapping parts (shotgunning) so often creates confusion. And why so many parts were replaced without success. [/FONT][/COLOR]

[COLOR=black][FONT=Verdana]BTW, fixing things is not to save money. Fix to learn. Described is what gets learned by doing; what is meant by follow the evidence. Most who watch CSI never get it because they do not also do it. Fix things first and foremost to learn from your mistakes.[/FONT][/COLOR]

---

### Post by Sylos on 2010-11-07
> Well, since I think this thread is kind of dead I will respond.

Not quite.....Im waiting on multimeter being delivered so I can follow Westom1's advice and take some readings.

In the meantime keep posting - Im learning a lot here.

Cheers

---

### Post by Sylos on 2010-11-14
After a lengthy wait for my ebay purchased multimeter I have finally taken some readings (hope somebody is still watchin :))

The readings where taken with the PC booted up to the login screen (not sure i thats the right way but here goes).

The results are as follows:

Pin1 - Yellow = 12.21V
Pin2 - Purple = 5.13V
Pin3 - Grey   = 4.93V
Pin4 -        = 0V
Pin5 - Red    = 5.11V
Pin6 - Black  = 0V
Pin7 - Red    = 5.11V
Pin8 - Black  = 0V
Pin9 - Orange = 3.44V
Pin10 - Orange = 3.44V

Pin11 - Red   = 5.11V
Pin12 - Red   = 5.11V
Pin13 - White = -5.09V (negative)
Pin14 - Black = 0V
Pin15 - Black = used as ground
Pin16 - Black = 0V
Pin17 - Green = 0.01V
Pin18 - Black = 0V
Pin19 - Blue  = -11.58V (negative)
Pin20 - Orange = 3.43V

This all looks pretty good to me but Im not sure. It may be worthy of note that Pins 1,2 and 20 all fluctuated by 0.01V - not sure if this is normal or not.

Westom1 or anyone else have any indications whether this looks normal?

Many Thanks

---

### Post by westom1 on 2010-11-15
[COLOR=black][FONT=Verdana]> **Sylos said:**
>    The readings where taken with the PC booted up to the login screen (not sure i thats the right way but here goes)...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Pin1 - Yellow = 12.21V[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Pin2 - Purple = 5.13V[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Pin5 - Red = 5.11V[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Pin9 - Orange = 3.44V[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Those are the four important measurements.  Any one wire of each color reports same.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  But first put the system under load.  IOW execute complex video graphics (ie a movie or advanced video game), whlle downloading from the internet, while reading a CD-Rom, while powering something via the USB port, while searching the hard drives, while ...  Now the system is loaded.  Multitasking to every hardware.  Only then are four voltages ready to be read.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  Well, those provided numbers are fine.  Actually significantly higher than they should be (especially the orange wire).  Implies the system is consuming too little power.  For readings to be valid, the system must have everything doing something - multitasking - demanding more power.   Hopefully the 3.3 volt orange wire will be closer to its expected voltage.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  Blue and white wires say nothing useful.  Black wires are connect to the chassis; should always be zero.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  Green wire must be well below 0.7 volts when power controller orders the supply to power on.   Gray wire must be well above 2.4 volts to report supply critical voltages are good.  Those ‘communication’ signals are well within limits[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] Fact that purple, red, orange and yellow wires are all consistently on the high side implies the computer is drawing minimal power.  Relevant measurements must be taken when the system is drawing maximum power. Then I expect those numbers to be closer to but still slightly above 3.3, 5, and 12 volts.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] I recall, the system has been running normal since memory was replaced. These numbers imply the entire power supply system is stable and good.  Would not cause intermittent memory failures.  Better numbers taken with load will say more.  But I expect them to be well in spec.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]   A final test would execute a memory diagnostic (ie Memtst86) with hardware heated to 100 degree F or higher.  IOW with memory and the adjacent large square motherboard chip heated by a hair dryer on highest setting.  Heat is a powerful diagnostic tool – especially for memory.  If that heated test works, your memory is probably 100% stable.   A test done only because you are not yet convinced the problem has been eliminated.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  I expect power system numbers with a load to be lower and still quite sufficient because the current lightly loaded numbers are so high.[/FONT][/COLOR]

---

