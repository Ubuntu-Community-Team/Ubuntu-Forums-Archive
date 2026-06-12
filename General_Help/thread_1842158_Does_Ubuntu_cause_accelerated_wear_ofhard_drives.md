---
title: "Does Ubuntu cause accelerated wear ofhard drives?"
date: 2011-09-10
forum: General Help
---

### Post by holadebob on 2011-09-10
I haven't found anything directly related to this problem, although there are posts a long time ago about hard drive failsafe operations every few seconds, and I'm not sure of a connection but would like to heard your thoughts.

I will be installing the third WD hd into my system withing two years of using 9.04 and 10.04. The first was a WD160 and I have also gone through two WD320's. I cringe when I write this, but I used a WD160 for four years non stop using XP (ouch-please don't think I am saying I am going to go back to W, something I wouldn't do unless all other OS's is the world vaporized!)

Coincidence, bad hdd quality, or overuse or abuse? or all three?  My wife and I use our computer about 5 hours/day and it stays on 15hrs/day about half the time and 24hr/s the other half.

Thank you

---

### Post by JonM33 on 2011-09-10
Why would it? Most hard drives come with hundreds of thousands of hours MTBF rating. Samsung's are 500,000 hours for example. That's over 57 years if you ran it 24/7.

---

### Post by Gatorade on 2011-09-10
I doubt that very much , and I'd be quite surprised if anyone can prove otherwise.

---

### Post by dcstar on 2011-09-10
> **holadebob said:**
> I haven't found anything directly related to this problem, although there are posts a long time ago about hard drive failsafe operations every few seconds, and I'm not sure of a connection but would like to heard your thoughts.

I will be installing the third WD hd into my system withing two years of using 9.04 and 10.04. The first was a WD160 and I have also gone through two WD320's. I cringe when I write this, but I used a WD160 for four years non stop using XP (ouch-please don't think I am saying I am going to go back to W, something I wouldn't do unless all other OS's is the world vaporized!)

Coincidence, bad hdd quality, or overuse or abuse? or all three?  My wife and I use our computer about 5 hours/day and it stays on 15hrs/day about half the time and 24hr/s the other half.

Thank you

I have read previously that the WD "Green" drives have reported issues with their fixed power-down times being a couple of seconds less than the standard Linux cycle of disk access, so every ten seconds or so (when basically idle) they are continually powering down and powering up a couple of seconds later.

This (apparently) does not occur with most other drives as they either do not auto power down or have longer timeouts that exceed the Linux cycle time.

If you are using the WD Green drives then this could explain some of you problems, if you are not then I don't know.

---

### Post by holadebob on 2011-09-10
My intention for this question is not to polarize, it is just curiosity. I thought it was a bit strange that I would lose 3 drives in two years with normal family use. 

It's hard for me to believe that WD QC could be that bad, especially only on the drives that I bought. :)

I'm going to switch brands, only because I don't know what else to do. I believe statistics say I should buy another WD. Cunundrum.

---

### Post by LowSky on 2011-09-10
I have 2 green drives, both are fine and still working a couple years after purchase.

The Linux destroying drive thing is an old legend, and a poor one at that. If it was so bad would you think so many companies would run Linux servers?

---

### Post by LowSky on 2011-09-10
> **holadebob said:**
> My intention for this question is not to polarize, it is just curiosity. I thought it was a bit strange that I would lose 3 drives in two years with normal family use. 

It's hard for me to believe that WD QC could be that bad, especially only on the drives that I bought. :)

I'm going to switch brands, only because I don't know what else to do. I believe statistics say I should buy another WD. Cunundrum.

Did you buy them from an online company, like Newegg? The issue is bad shipping packaging (no fragile labeling) and a shipping company that is notorious for throwing around boxes like a baseball pitchers. WD drives have long warrantees, time to call them up and say they died.

---

### Post by halibaitor on 2011-09-10
> **JonM33 said:**
> Why would it? Most hard drives come with hundreds of thousands of hours MTBF rating. Samsung's are 500,000 hours for example. That's over 57 years if you ran it 24/7.

I too have had hard drive failures, but i certainly don't think the OS has anything to do with it.  I think it is more likely the result of simple hardware failure.

As for the gigantic projected life figures on the drives, I take those numbers with a grain of salt.  To begin with, those numbers are only estimates, and I don't see how they can even be close to reality.  If the drives actually did last as long as the manufacturers claim, hard drive failures would be as rare as hen's teeth.  Nobody would even know anyone that has had a drive fail.

The prevailing wisdom however says that we should back up our systems, because it isn't a matter of _if_ we will get a HD failure, but rather _when_.  It seems to me that "when" happens a lot sooner then the manufacturers would have us believe. ;)

---

### Post by holadebob on 2011-09-10
I guess I pushed a button.....

The Linux destroying drive thing is an old legend, and a poor one at that. If it was so bad would you think so many companies would run Linux servers?

No, I bought them from three separate computer stores here in the Republic of Panama. 

I'll drop this subject. I really apologize for suggesting that Ubuntu or Linux may have caused my hard drives to fail. 

Not that it matters, but I'm not a person that would have fun regurgitating old legends.

---

### Post by Pariah819 on 2011-09-10
I would have to agree with halibaitor, hard drives never seem to last as long as manufacturers claim.  The numbers they project are best case scenario in a very well controlled environment.  You might actually want to check for things like excessive heat if all of these hard drive failures have occurred in the same PC.

---

### Post by halibaitor on 2011-09-10
> **Pariah819 said:**
>   You might actually want to check for things like excessive heat if all of these hard drive failures have occurred in the same PC.

Good point.  I actually had to install a second case fan for a friend of mine so that his computer would quit overheating.  (It burned out 2 WD hard drives before I figured out why.)

---

### Post by holadebob on 2011-09-12
I got a bit miffed at lowsky's remarks about me wanted to create hysteria over an old myth of ubuntu's. Well you needn't be concerned or be defensive. I think that I may have figured out a possible problem. 

After doing some searching, apparently Ubuntu shows more power dissapation than Windows. That power dissapation, lowsky, is known as heat, which could conceivable have heated my case up a bit more than when I was on windows, eh?

That may be the reason my old first WD160 lasted 3-4 years (can't remember exactly) on my old XP install, and the other WD's I mentioned above may have overheated because I didn't put more fans in my case. If I would have researched Ubuntu more, I might have discovered that one of the hidden requirements is more ventilation. 

Pariah819 made me suspicious that heat may have been the problem, and after realizing that I have had the same MB, cpu, sound card and box for the past 9 years, of which only two years when I have had Ubuntu installed, and the box has set in the same place for those 9 years, in my computer desk, except when it has been removed and cleaned out every six months, Feb and Oct, kinda points to another variable besides myth. 

Of course, you may slam me with another of your non supported myth stuff, but I am sticking with Ubuntu and you'll hear from me again if I need help. For now, I am getting one of those super quiet large fans and cooling this baby down, so I can run Ubuntu.

 

:)

---

### Post by Linuxisfast on 2011-09-12
On my brand new ASUS netbook which came with Windows 7 starter, the hdd would be constantly thrashing and running hotter, CPU load was also relatively higher than Ubuntu, both went away after Ubuntu install, hdd stays cooler, CPU temps are also down. Bear in mind that this unit has 2GB ram that should be sufficient to run Windows 7.

Same experience on my 16GB dual XEON desktop, the anti virus and other programs would constantly thrash the hdd with Windows XPx64, with Linux temps of both CPU and hdd would be relatively cooler. Seems like Phoronix is hell bent on creating anti Linux hysteria all around.

---

### Post by 3rdalbum on 2011-09-12
Heat shouldn't be an issue. I have a four-year-old WD Green 500 gig HDD in my computer. It's really big and chunky so you'd think it would require a lot of airflow to keep it cool... but it's just in a regular case with a regular fan and hasn't missed a beat. Not even a bad sector in all this time.

I don't believe Ubuntu could make the drive heat up more than on Windows. Ubuntu just passes data and data requests to the drive, and the drive controls itself.

You're probably just unlucky. I think most PVRs use WD drives, sometimes with minimal cooling (just a couple of vents above the HDD) and it's NEVER the hard disk that fails first in a PVR.

WD is probably the most reliable brand out there for hard disks.

---

### Post by joe916 on 2011-09-12
I've never had a drive last longer than 5 years

---

### Post by holadebob on 2011-09-13
I was thinking of the possibility of my cpu generating more heat, raising the temp of the inside of the case and crossing the threshold of reliable operation of my hdd's.

If my case internal temp was even 1 or 2 degress under the max temp for the hdd environ spec, just that 1 or 2 degree increase from a little higher dissapation from the cpu would cause my problems. I can't come up with (and no one has suggested yet) another possibility. 3 drives in two years is excessive in my way of thinking, and heat as the cause of the failures is logical, because I'm not subjecting them to anything else damaging. 

I'm going to ventilate the case better today (and see if I can find a temp probe here) and we'll see down the line what happens with the new drives I will be installing.

Back to you in a year.

---

