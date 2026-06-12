---
title: "Battery problems with 10.04 desktop edition"
date: 2010-04-29
forum: General Help
---

### Post by lou002 on 2010-04-29
Hi gang!

So I had 9.10 desktop edition on my netbook, an Acer Aspire One 532H netbook and then upgraded to 10.04.

Loving it except for one problem. When I first log on, it will say "your battery is old or dead. it only has a 35.9% (or 35.6% the very first time i logged on)."

But when I plug in the A/C adapter, it says it's fully charged..so I take the adapter out real quick and it goes from 10 hours 25 minutes to 6 hours 25 minutes to 5 hours 45 minutes. 

Is this a problem with my battery? With 10.04--perhaps a glitch since it is release day.

I really don't want to go back to Windows7Starter, or use the Netbook Edition..so any help or advice that can be given would be appreciated. 

Thank you! And if more info is needed, I'll be glad to give it.

---

### Post by lou002 on 2010-04-29
Very oddly, as a side note. it hasn't happened at home, just at the library i was at. 

Very strange, from this noobs perspective.


Well..at least the pop doesn't come up any more; but the battery drains REALLY fast. Faster then I've ever seen it drain.

---

### Post by SnickerSnack on 2010-04-29
Have you tried using the netbook edition?

---

### Post by lou002 on 2010-04-29
I'd honestly prefer not to. 

I could; but I didn't have this problem with Desktop Edition 9.10, so I figured I'd give 10.04 a try.

---

### Post by SnickerSnack on 2010-04-29
Install powertop and sun it (with sudo) from the command line; it'll give an idea of what is using the most power.  That may help you whittle your running processes down to a more reasonable level.

---

### Post by lou002 on 2010-04-29
I guess I wasn't being clear enough. This is completely my fault.

When I say it's draining **REALLY** fast I mean that the moment I turn on the machine it says it has 5 hours 25 minutes then goes down "you have about 10 minutes left!" mode. This is with **_nothing_** running, when it first logs on and loads. I'm putting emphasis to ensure I'm clear.

This stuff DIDN'T happen in 9.10 which I had installed up until about 1pm today or so, when 10.04 first dropped.

I guess I'll go download the UNE for the flash drive then. Even though I didn't want to.

Thanks for the help though.

---

### Post by lou002 on 2010-04-29
Okay, so I installed the 10.04 Ubuntu Netbook Edition onto the netbook..and I got the same message, "your battery may be broken and only has a 35.9% charge"

I mean it's not super 100% important as i keep it plugged in generally anyways; but im posting this A) For others who might have this issue as well as for the 'what-if' issues that may arise..like what if im at a place that has no plugs.

---

### Post by jlking3 on 2010-04-30
It appears that when the power manager or battery manager is doing its regular check, it reports back incorrect data about the battery's "Energy (design)" setting, sometimes reporting the design as being able to hold over 700Wh.

When the Energy (design) is reported at 700Wh, the computer then reports 1 or 2% percentage, and proceeds to automatically suspend/hibernate/shutdown, depending on the setting.

If there were a way to force the "Energy (design)" setting to remain at a particular number, this issue would be resolved with that workaround until it was fixed permanently in a software update.

---

### Post by lou002 on 2010-04-30
umm..thanks. I think. I'm not really that technically inclined, so it was a little hard to understand what you mean. So basically, it's an Ubuntu problem that's causing my battery to be seen as more powerful then it is, and thus it will not only drain faster but be seen as 'broken' because of it? And this will more then likely be fixed in a software update?

If I understood you correctly, of course.

---

### Post by BaroqueBloke on 2010-05-01
With any luck it will be.  Im on my 532h now and the battery icon is glowing red and says I have only minutes left and threatening to shut down.  But, its also been doing this for the past 45 minuets with now change.  The problem is with Ubuntu, not your computer.  Sometimes I can get this to go away by logging/restarting but not always.  So far 10.04 is really nice and snappy but I may switch back to 9.10 or 9.04 as more things worked for me then.  Namely the side scroll bar and no battery glitches.  My multi card slot, multi touch on track pad, and internal mic are still on the fritz though.  

Good luck with your netbook!  and rest assured if and when a solution is found it will be released in an update or at the very least posted on this forum.

---

### Post by lou002 on 2010-05-01
> **BaroqueBloke said:**
> With any luck it will be.  Im on my 532h now and the battery icon is glowing red and says I have only minutes left and threatening to shut down.  But, its also been doing this for the past 45 minuets with now change.  The problem is with Ubuntu, not your computer.  Sometimes I can get this to go away by logging/restarting but not always.  So far 10.04 is really nice and snappy but I may switch back to 9.10 or 9.04 as more things worked for me then.  Namely the side scroll bar and no battery glitches.  My multi card slot, multi touch on track pad, and internal mic are still on the fritz though.  

Good luck with your netbook!  and rest assured if and when a solution is found it will be released in an update or at the very least posted on this forum.

Thanks Baroque. I decided I'm going back to UNR 9.10 for now. When 10.04 becomes better and they fix that issue, then I'll upgrade.

For now, though, 9.10 has worked for me, and it was stable enough for me to like it.

---

### Post by revkult on 2010-05-01
Hi there,

I'm not sure why this thread is marked "solved", I don't see any solutions for the problem. I too have an Acer Aspire One 532h and have the same battery problem. The battery indicator fluctuates consistently giving random percentages. Usually saying only 5% left when it's really 90%. Any real solutions to fix this would be appreciated. I'll continue to look for an answer and post one here if I find it. Thanks!

---

### Post by lou002 on 2010-05-02
> **revkult said:**
> Hi there,

I'm not sure why this thread is marked "solved", I don't see any solutions for the problem. I too have an Acer Aspire One 532h and have the same battery problem. The battery indicator fluctuates consistently giving random percentages. Usually saying only 5% left when it's really 90%. Any real solutions to fix this would be appreciated. I'll continue to look for an answer and post one here if I find it. Thanks!

It was solved for me personally as I went back to 9.10 UNR and everything works fine. However, I can mark it unsolved if you wish so that others can view it and try to offer a 'real solution' as you put it.

The 'real solution' I can personally offer is to  either go back to 9.10 or wait it out for any updates to 10.04 that may or may not come. As others have pointed it out--it's obviously not our machines, especially not mine as it's not even a month old; it's the newest version of this OS, which I imagine will be fixed in an update.

But it's open source, and as I'm learning, you gotta take the bad with the good.

---

### Post by ken.gledhill on 2010-05-03
This appears to be a 10.04 and Aspire One 532h problem. And it is not solved, as I have the same issue as everyone else. However, I really like 10.04 (using desktop version) and will await a fix.

Ideas please? Should this be reported as a bug?

Cheers, Ken

---

### Post by lou002 on 2010-05-03
> **ken.gledhill said:**
> This appears to be a 10.04 and Aspire One 532h problem.  

I don't know if it's an Aspire problem. It sounds more like it's an Ubuntu software glitch or something.

>  Ideas please? Should this be reported as a bug?

Cheers, Ken

Honestly..I think someone should report it as a bug. I wish I had thought of that, to be honest.

---

### Post by revkult on 2010-05-03
I'm using the 10.4 desktop version as well. I love it. Perhaps a bug. I'm not sure how you report bugs, so if someone wants to go ahead and do that. I'm going to continue to use 10.04, It's been a few years since I'v used Ubuntu, but I'm having too much fun with it to go back to an older version.

---

### Post by lou002 on 2010-05-03
This issue, so far has been *knocks on wood* fixed for me. I downgraded to 9.10, then today reupgraded so I could take full advantage of gwibber and so far everything's working great. I didn't get an error message, and the battery's indicator is working great.

---

### Post by revkult on 2010-05-03
While I was writing the previous post I the battery icon gave me the low battery warning, then a few moments later the battery went back to normal. I've attached the images. (at least I think I did).

---

### Post by lou002 on 2010-05-03
> **revkult said:**
> While I was writing the previous post I the battery icon gave me the low battery warning, then a few moments later the battery went back to normal. I've attached the images. (at least I think I did).

you did. and that's close to what I've gotten too. I've also gotten "your battery is old/dying and you have a 35.9% charge"..but now, it seems to have somewhat normalized.

Okay, revkult, I'm starting to get that problem. Except the indicator hasn't gone back up for me, and it's saying 14.5% but everything else says like 5hours and some odd minutes. So I'm running on pure battery right now to see what it does

---

### Post by DWally on 2010-05-04
I am having the same problems with an Acer Aspire 5737z. Installed 10.04 Desktop Ed. a few days ago, after using 9.10 for ages with no problems at all. On bootup, I get a message saying that my battery is broken or faulty, and only has 44% available. When I unplug ac power, battery level drops from full to critical in only a few minutes, but laptop still runs for quite a long time after this. Seems to take normal time to recharge once pugged back in. Annoying, but as I normally use laptop on ac, I will keep using it and hope for a fix. 10.04 is fantastic, no complaints and desktop cube and visuals are great!

---

### Post by lou002 on 2010-05-04
> **DWally said:**
> I am having the same problems with an Acer Aspire 5737z. Installed 10.04 Desktop Ed. a few days ago, after using 9.10 for ages with no problems at all. On bootup, I get a message saying that my battery is broken or faulty, and only has 44% available. When I unplug ac power, battery level drops from full to critical in only a few minutes, but laptop still runs for quite a long time after this. Seems to take normal time to recharge once pugged back in. Annoying, but as I normally use laptop on ac, I will keep using it and hope for a fix. 10.04 is fantastic, no complaints and desktop cube and visuals are great!

I fully agree no complaints other then this; and I use it primarily on the AC as well, so I'm not super-duper-worried about it either. But better to let people know then to stay ignorant.

Otherwise 10.04 is great.

Note: I just got the "your battery is broken or old" AGAIN at the time of this point..after two days of nothing wrong.

---

### Post by revkult on 2010-05-06
I think the latest update might have fixed our problem. Testing now and battery indicator appears stable. We'll see how the day goes.

---

### Post by lou002 on 2010-05-06
it's stable. 

But then again, my netbook shut down on me after a half an hour this morning when the battery indicator said I had an hour left on the battery.

And mind you, this is a brand new battery in this machine; it's a brand new machine. and I've check all the external connectors to it.

---

### Post by DomesDKG on 2010-05-06
ah yes, I was hoping the new kernel would fix this, I'll check it out today as well.

---

### Post by /G\ on 2010-05-07
Did the upgrade fix the problem for you guys? I don't think it did the trick here...

---

### Post by lou002 on 2010-05-07
It fixed it for me. No complaints from me here. Fully charged, no "your battery is dead/old" no shutting down on my prematurely. I got a full 5 hours 15 minutes from it today; i took it off the a/c at noon and it ran on the battery till 5:15pm (EDT)

---

### Post by ragman563 on 2010-05-08
I am having issues with the battery notification warnings as well on my 532H. Some times I boot back into Windows just to make sure my battery is ok... We aren't screwing our batteries up using 10 are we?

---

### Post by lou002 on 2010-05-08
> **ragman563 said:**
> I am having issues with the battery notification warnings as well on my 532H. Some times I boot back into Windows just to make sure my battery is ok... We aren't screwing our batteries up using 10 are we?

No way. There has been update in the past couple of days. Check it. Mine's worked fine since the update.

---

### Post by ragman563 on 2010-05-10
My 532h shows it is on AC when it is running on batteries at times now.. Anyone else?

---

### Post by /G\ on 2010-05-11
This is just bizarre. Now my battery charges really slowly and then reaches only 63% charge. The time given when running on battery seems to be some randomly generated number or something.

It is not a problem with Ubuntu, it is a kernel problem I think. Other distros that are not based on Ubuntu gave me the same problem (running the current kernel)...

I am starting to doubt it is my battery that is faulty...there is one way to know: reinstall window$.

---

### Post by Menelkir on 2010-05-12
I think it's a software problem. Reporting the same problem in IBM Thinkpad R51 and Lenovo Thinkpad SL400. (Very different hardware machines).

---

### Post by lou002 on 2010-05-12
I don't get that problem. In fact, my system's working 100% now. I'm very happy now with 10.04

---

### Post by Menelkir on 2010-05-12
Maybe it's some "specific" ACPI problem with "specific" hardware, because I have the same problem with my machines. (I know that some ACER notebooks have a long long history with ACPI incompatibities, but Lenovo/IBM are always 100% linux compatible, I don't get it).

If someone wants some log, feel free to ask, I'm here to help. :)

---

### Post by lou002 on 2010-05-12
It was fixed with a recent update though, at least on my end. A previous writer was using the same model (Acer) and Model number (532H) as myself, so all he/she should have to do is update the software.

---

### Post by Menelkir on 2010-05-12
Here the problem persists. My Ubuntu is fully updated from 4 hours ago (I see now, there's only some gvfs updates).

---

### Post by /G\ on 2010-05-14
Alright so I installed windows, checked the battery's behavior and then uninstalled. The battery is working perfectly in windows. I am using the same acer (532h) that others have reported they're using and their problem was solved yet mine isn't. I'll just wait on more updates for now I guess..

---

### Post by treetop on 2010-05-16
I really don't know how old this problem is but I also have the same problem "your battery seems to be broken...". I'm using an eeePC EPC900B which seems to function correctly in every case with 10.04 netbook version. It's just the irritation of having the pop up visible every time I boot. Haven't found anyone with an answer yet. Anybody know if this is being worked on or if a solution has been found?

---

### Post by juniper1982 on 2010-05-18
I have a dell i6000 and the battery meter has two annoying problems.

1)  I can't display percentage.  It appears this is by design and people far and wide have noticed
2)  more seriously, the meter really fluctuates, especially when it is low on charge.  it will say 50 mins remaining, then a minute later 25 mins remaining and then a minute later 50 mins remaining.

---

### Post by lou002 on 2010-05-23
I get a problem that says "unable to detect available WMID devices" I never have a problem with Mint (other then its slow on a netbook) or jolicloud as far as the battery goes. Only Ubuntu, this is getting ridiculous, especially on an LTS edition.

---

### Post by li_feng on 2010-05-24
I have used ubuntu 10.04 on my hp cq41-110au with AMD processor , but then I used it at AC power not in battery mode it appeared normal, but when I used it at battery mode the notebook was restarted suddenly , so I logged again but before I logged in and before filled my password , it  was restarted suddenly again ! Any idea to fix this mess ! but I have installed 9.10 before but appeared normally.

---

### Post by BergmanW on 2010-05-27
Did you ever had windows 7 on your laptop ?
google for "Battery problem windows 7" (without the quotes) and you will see your not the only one. Join (like me) the other 96.800.000.

Of course MS$ denies it saying : Microsoft has received 20 customer service incidents and states none of  these have shown anything other than degraded batteries. [IMG]http://forum.ubuntu-nl.org/Smileys/default/huh.gif[/IMG]

---

### Post by lou002 on 2010-05-29
> **BergmanW said:**
> Did you ever had windows 7 on your laptop ? 

I had Windows 7, didn't have a problem
Ran Ubuntu 9.10 desktop edition on my netbook, didnt have a problem

upgraded to 10.04, had problems
went to 10.04 UNE, had problems

ran jolicloud, mint, peppermint, didnt have problems with battery

went back to 10.04 UNE had battery problems

went back to 9.10 desktop edition, no battery problems.

Obviously, 10.04 is the problem. And that's coming from a fan of ubuntu

---

### Post by bautvill on 2010-05-30
I try fix some of the battery problem in my Acer 532h. I try with  upgrading my BIOS.
I flash my BIOS to version 1.22. I did some testing and the problem was still there, but some times it detect the battery right.

---

### Post by snoopdomm on 2010-05-31
Try this temp fix!!!

I have been having the same problem on my acer one netbook running ubuntu 10.04 desktop edition. 

This is what I have found works until a software fix comes out, its pretty easy but can still cause problems.  Like I said it works for me, and will probably work for you.

when my battery is fully charged and i shut down first then unplug it to take with me is when i get the error/battery is drained message, but if when my battery is fully charged and i unplug it first then shut down and take it with me there is no problem what so ever. So to everyone in this forum please try unplugging then shutting down and it should fix the problem. Its a pretty easy fix but can be annoying if you forget to unplug first like I have a few times now, arg.

Let me know if this helps,
Dom

---

### Post by be1952 on 2010-06-10
> **snoopdomm said:**
> Try this temp fix!!!
...
Let me know if this helps,
Dom
no, unfortunately. i have a presario cq41 it had win7 pre-installed and battery power was ok, after installing 10.04 over it, the battery power problem started. if i try and clean boot or return from hibernate with the AC unplugged it goes into a reboot cycle. works fine on AC.

will try loading another OS onto a pendrive and report back.

cheers
bruce

---

### Post by w1ll1am on 2010-06-12
Hello I am having the same problem it is only on my acer 532h that this happens it works fine on my other laptop. I hope that they can  get this problem fixed soon it is very annoying.

---

### Post by be1952 on 2010-06-14
its definitely a ubuntu problem and more specifically it appears to be a gnome problem. booting to a console session works fine, problems only start when booting into X. i disabled gnome-power-manager and my laptop worked ok on battery power. still testing...

---

### Post by w1ll1am on 2010-06-22
I really hope this is fixed soon it is very annoying i use my netbook more than any computer i have and i would love to not have to keep it plugged in. If anyone knows a fix let me know as soon as you can thanks

---

### Post by lou002 on 2010-06-23
> **w1ll1am said:**
> I really hope this is fixed soon it is very annoying i use my netbook more than any computer i have and i would love to not have to keep it plugged in. If anyone knows a fix let me know as soon as you can thanks

I'm going to upgrade again and see if it's fixed or anything. I'll need my netbook that's for sure as I have to do a recovery (With the discs) on my windows machine.

---

### Post by bhuvi on 2010-06-23
type this in the terminal to see if it temporarily fixes your problem:

> gconftool-2 --type=bool --set /apps/gnome-power-manager/general/use_time_for_policy false

---

### Post by w1ll1am on 2010-06-24
Holy crap check this out. I decided enough is enough, and I am going to go back to an earlier release of ubuntu. So I thought of the most stable and maintained release that I could think of and it had to be 8.04 LTS. I downloaded the desktop version and installed it on my netbook and what the hell! No wireless support. I tried 9.04 ahhhh still no wireless. I figured I would just deal with the battery thing and hope there was going to be a fix soon. I reinstalled 10.04 LTS and the battery started to work and I was amazed. I am not sure what happened but this is what I did.

I had 10.04 LTS installed on my flash drive I installed it on my netbook. I did not do the I_nstall Ubuntu_ I did the _Try Ubuntu without changes to your computer_ then installed from there. I had my netbook plug in and charging the entire time I did not unplug it until I restarted and it showed it was charging I am not sure if this will help anyone or not but it is working for me so far. I hope someone else can benefit from this information. Good luck.

---

### Post by lou002 on 2010-06-25
See I tried:

-9.10 desktop--worked fine. no problems, wireless, battery everything
-10.04 desktop-battery issue, everything else worked fine
-10.04 UNE (i personally hate the UNEs period), see the desktop edition
-Mint-worked fine.
-Jolicloud-worked fine, may go back to when it's a final release.
-went back to 9.10 desktop, worked fine.
-went back to 10.04 desktop (via upgrade), it didn't.
-went to Kubuntu 10.04-worked fine, but Kubuntu was confusing.
-went to Xubuntu 10.04-worked fine.

it's amazing that it can work fine in the Derivatives of Ubuntu, but not the main one.

---

### Post by w1ll1am on 2010-06-25
> **lou002 said:**
> See I tried:

-9.10 desktop--worked fine. no problems, wireless, battery everything
-10.04 desktop-battery issue, everything else worked fine
-10.04 UNE (i personally hate the UNEs period), see the desktop edition
-Mint-worked fine.
-Jolicloud-worked fine, may go back to when it's a final release.
-went back to 9.10 desktop, worked fine.
-went back to 10.04 desktop (via upgrade), it didn't.
-went to Kubuntu 10.04-worked fine, but Kubuntu was confusing.
-went to Xubuntu 10.04-worked fine.

it's amazing that it can work fine in the Derivatives of Ubuntu, but not the main one.

That is really strange. I guess that I just got lucky and it installed correctly. When I had UNE 10.04 LTS installed on mine my battery did not work and I also tried to upgrade and it did the same thing. It is really weird but when ever I have any of them installed on a flashdrive and boot up from it the battery will work. It is onlt once it is installed that it didn't well except for this time lucky me I guess. Well good luck.

---

### Post by lou002 on 2010-06-25
> **w1ll1am said:**
> That is really strange. I guess that I just got lucky and it installed correctly. When I had UNE 10.04 LTS installed on mine my battery did not work and I also tried to upgrade and it did the same thing. It is really weird but when ever I have any of them installed on a flashdrive and boot up from it the battery will work. It is onlt once it is installed that it didn't well except for this time lucky me I guess. Well good luck.

I did the flash drive thing too, Will. It's the only way to install on a netbook (besides buying a USB cd/dvd drive).

What I find strange is that every version or derivative works just fine, but 10.04 doesn't.

---

### Post by Graeme.ross on 2011-04-11
I think I have found a solution to this problem. 


[LIST=1]
[*]Go to the  configuration editor tool (gconf-editor)
[*]Go to the gnome-power-manager -> general settings.
[*]Deselect use-profile-time and use-time-for-policy settings
[*]The battery charging symbol should disappear from the info bar
[*]Reselect the settings you have deselected
[/LIST]
If you go to the battery statistics panel now it should show that the system has recalculated the amount of charge stored in the battery (should be at 100% now)

This worked for me:D

---

### Post by lou002 on 2011-04-11
I found that moving to 11.04 beta makes my PC with Ubuntu on it run great!

---

