---
title: "what a disaster I cannot understand how this could happen"
date: 2010-10-26
forum: General Help
---

### Post by agurkas on 2010-10-26
Hi guys. Today I had a very disastrous situation.
I hope someone could explain how I managed to loose data as I need to avoid it in the future by all means. We are running small but important business office with mostly Ubuntu desktops.
So there is a desktop that I am running Ubuntu 10.04 on fake software raid 1 ext4 filesystem.
I thought raid mirror is a good option as data integrity is very important. (was not sure if fake raid is a good idea though, on some boxes I run linux software raid and on server true hardware raid and Centos Linux)
So today we noticed couple of files on that box were corrupt (binary garbage instead of plain text of just empty files). I suspect it is possible that box was not shut down properly this morning.
I have a backup. I decided to force fsck on next reboot. I did not see fsck running on reboot as expected and to my complete amazement some entire folders with thousands of files went missing after next reboot in the home folder. It seems those were files that were recently created (today).
As I say fortunately I have a backup. If not I would have to shoot myself.
But how this could possibly happen, and how to avoid it? Is it fake raid to blame or fsck or ext4 or what? How can data just disappear without any warning and option to recover? I am completely lost and worried very much.
I cannot afford to loose any data like that. Now I am very nervous about all those linux machines in the office as you can imagine. Some are running Ubuntu 10.10 with fake raid 1 and ext4 as well. Should I use software raid instead fake raid? Should I use ext3 instead ext4?
Should I avoid fsck? But Ubuntu forces it every 40 boots or so so it supposed to be safe to run it anyway I thought till today... Could it possibly be Ubuntu issue and I should use another distribution?
In the boot logs I have found only this suspicious line possibly on disaster boot:
EXT4-fs (dm-1): 12 orphan inodes deleted.
Later I run fsck and it did not complain a word.
Any ideas what happened? I am running various Linux distros for 10 years and it is first time my data went missing. I don't have experience in this particular area.
I would appreciate your support. Thank you.

---

### Post by night_fox on 2010-10-26
I'm not at all clued up on RAID, but if you run fsck.ext2 on some versions of ext4, it can't tell the difference and really screws it up.

---

### Post by agurkas on 2010-10-26
> **night_fox said:**
> I'm not at all clued up on RAID, but if you run fsck.ext2 on some versions of ext4, it can't tell the difference and really screws it up.

OMG. Should I disable fsck entirely on boot then or even better reinstall everything using other filesystem? Is ext3 the best option? The thing is ext4 is default and I thought it is safe and mature enough to use it. 

I never had disaster like that on ext3. Just this year we started using ext4 on 4 new linux boxes running Ubuntu 10.10 and 10.04.

Thank you for your prompt reply. 
If someone could comment on raid as well I would appreciate.

---

### Post by night_fox on 2010-10-26
I dunno. It might not be fsck.ext2 because your systems have survived thus far. It's worth checking which versions of fsck.ext2 this is a problem for, and if it's possible that it happened to you. ext3 is generally very safe, ReiserFS is quite good (apparently 15x faster for smaller files), also they're bringing out a new one soon.

---

### Post by ezsit on 2010-10-26
I have never had any problems with ext3 and still use it under Ubuntu 10.10. I see no reason to jump to ext4 since the supposed benefits do not affect my needs as a desktop user. If I did want an industrial strength file system I would choose JFS or XFS since those two have decades of development behind them. I have seen too many complaints with ext4 to consider it.

Then again, if your backup habits are as good as they seem to be, forget the RAID stuff and rely on backups alone. It could be the RAID business that is screwy.

---

### Post by yetiman64 on 2010-10-26
Please note the quote from the [--community documentation--]("https://help.ubuntu.com/community/FakeRaidHowto") (link provided) for fake raid,

> FakeRAID is not supported by Ubuntu. Trying to  install Ubuntu on such a partition could easily result in the loss of  all your data.This may explain what you are seeing.

Edit: I run 10.04 desktop with ext4 partitions (have used ext4 with 9.10 as well) and never noticed any problem with fsck. However I do not use RAID and my data is probably nowhere near as important as in your situation. Glad to hear you have good backups.

---

### Post by Quackers on 2010-10-26
Just as an outside possibility, is it possible a hard drive is failing?

---

### Post by agurkas on 2010-10-27
thanks guys for your valuable input. 
After reading your experience I think leaving active  fake raid SB700 controller was a very bad idea. I am inclined to think that disks went out of sync then synced and I lost some data on deleted nodes if I understand that properly (I am software not hardware guy). I never had an issue on linux software raid like that so I guess best option is to disassemble fake raid1 and build software raid1 on all those boxes.
Not sure if I should leave ext4 perhaps to stick to something more reliable perhaps ext3. 
(I will investigate my options - I hear what you mention about other file systems)

So in short my plan is software raid1 + possibly ext3+ daily backups.

I don't think my disks could be failing as those are brand new and disk smart status is OK (if I can rely on it).

Could someone recommend a good tool for hard disk testing so I run it just to be 100% sure it is fine.

Many thanks

---

### Post by Grenage on 2010-10-27
I'd personally stick to hardware RAID, or no RAID at all.  I've never 'seen' fakeRAID 1 go wrong, but there's a first time for everything.

---

### Post by agurkas on 2010-10-27
> **Grenage said:**
> I'd personally stick to hardware RAID, or no RAID at all.  I've never 'seen' fakeRAID 1 go wrong, but there's a first time for everything.

Grenage, why you say 'or no RAID at all' ?
Why you think it is a bad idea to use Linux software raid for data redundancy?
We cannot afford hardware raid on every desktop. But if I have just daily backups then I don't have real time backup this is why we want RAID1. Daily backup is just for worst case scenario.
Are you saying linux software raid1 is not reliable option?

many thanks

---

### Post by agurkas on 2010-10-27
> **Grenage said:**
>  I've never 'seen' fakeRAID 1 go wrong, but there's a first time for everything.

actually I have seen it before. We have another Ubuntu desktop with some different fake controller than this box. So it used to go out of sync and trying to resync like crazy for hours. Box was unusable while syncing. So I dropped fake raid and installed software raid on that box and all the problems went away.

---

### Post by Grenage on 2010-10-27
Oh no, not at all; there are many people out there who use Software RAID - even we have one server running it (we were in a pinch).

My opinions is that redundancy isn't that important on the average office PC; data is stored on a server, and that server probably has RAID and a backup solution.  While I've seen a lot of PCs run software RAID ok, I've also seen plenty of 'degraded array' messages when there was no good reason for it.

It's horses for courses; we don't run RAID on any office workstations.

---

### Post by yetiman64 on 2010-10-27
> Could someone recommend a good tool for hard disk testing so I run it just to be 100% sure it is fine.A commercial tool (~90 US Dollars) is available from grc.com called Spinrite. It may suit your purposes. [--LINK--]("http://www.grc.com/intro.htm"). It is a utility that is loaded to bootable media and uses free-dos as its environment. It recognizes and works on Linux filesystems as well.

I use it myself here to check the integrity of my HDDs if any problems are occuring.

---

### Post by agurkas on 2010-10-27
> **Grenage said:**
> Oh no, not at all; there are many people out there who use Software RAID - even we have one server running it (we were in a pinch).

My opinions is that redundancy isn't that important on the average office PC; data is stored on a server, and that server probably has RAID and a backup solution.  While I've seen a lot of PCs run software RAID ok, I've also seen plenty of 'degraded array' messages when there was no good reason for it.

It's horses for courses; we don't run RAID on any office workstations.

Grenage, I see what you mean now. Yes we run most valuable data on rack server.
But still users have many important document files on their home directories handy, emails etc. So those cannot be lost as well and if needed restored ASAP so they can continue work same day. 

I understand using network mounted home directories from the single server on LAN  
would be another option but again if server is gone all will stop working so we stick to RAID on every workstation. We thought it is a better approach.

This is why every workstation has 2x500 GB storage with RAID1.

BTW. server has hardware RAID1 but I have found many people are in favour of LINUX software RAID even on server. You say you are running it as well. Problem with hardware raid is as I understand if controller is gone (dead) you may need exactly the same controller to assemble array back. Software raid would not have this issue.

---

### Post by Grenage on 2010-10-27
Valid points, but in the last 15 years I have seen only one hardware RAID card die.

I might consider software RAID for RAID 5 or 10, if the server hardware was limited to RAID 0 and 1.

While servers can and do give a central point of failure, proper server hardware is _so_ much more reliable than desktop PCs.  Ultimately there is no wrong or right way; it depends very much on how the business works, so you're the only one who can decide that.

---

### Post by HermanAB on 2010-10-27
Software RAID has always worked for me.

Do you have a UPS?  That is the singularly best improvement you can make to any Linux machine.

---

### Post by agurkas on 2010-10-27
> **HermanAB said:**
> Software RAID has always worked for me.

Do you have a UPS?  That is the singularly best improvement you can make to any Linux machine.

Yes I know it is important. Unfortunately newly arrived workstations do not have ups yet. The problem some workstations are left unattended for quite a long time during the day. So in theory we need quite a powerful UPS for every workstation which is expensive. It is hard to convince management to buy it at once. I am not sure if there is a cheap solution for this power shortage problem.

thank you for pointing this out, I will work on it.

---

### Post by agurkas on 2010-10-27
> **Grenage said:**
> Valid points, but in the last 15 years I have seen only one hardware RAID card die.

I might consider software RAID for RAID 5 or 10, if the server hardware was limited to RAID 0 and 1.

While servers can and do give a central point of failure, proper server hardware is _so_ much more reliable than desktop PCs.  Ultimately there is no wrong or right way; it depends very much on how the business works, so you're the only one who can decide that.

Grenage, we will have to think about our networking once again, thank you for your valuable thoughts !

Many thanks

---

### Post by CharlesA on 2010-10-27
The point of a UPS is to ensure that the system is shutdown properly. You don't really need a "super powerful" one to do that. The one I've been using gives me about 5-7 minutes of power once the power goes out, which is enough time for the machine to shutdown or hibernate to preserve the data.

As for the "data is being stored in their home directories" thing, is it being backed up automatically, or is it just up to the users to back that data up?

---

### Post by Grenage on 2010-10-27
I wish you the best of luck in whatever setup you choose. :)

---

### Post by agurkas on 2010-10-27
> **CharlesA said:**
> The point of a UPS is to ensure that the system is shutdown properly. You don't really need a "super powerful" one to do that. The one I've been using gives me about 5-7 minutes of power once the power goes out, which is enough time for the machine to shutdown or hibernate to preserve the data.

As for the "data is being stored in their home directories" thing, is it being backed up automatically, or is it just up to the users to back that data up?

> gives me about 5-7 minutes of power
yes I understand what you say. up to 10 minutes UPS is not expensive. We could use it and just warn people in the case of power down to run to workstations! I mean I would be more glad to have at least 30 minutes ups everywhere but those are more expensive.

> or is it just up to the users to back that data up?[/

users home directory data is backed up automatically to the single data server after work hours daily, we have a gigabit LAN for that. 
More technical users still have an option to initiate backup if they need to e.g lunch time or more frequently. As I say most valuable data is on servers, users are accessing that data through web application on local intranet so that data is secure all the time. 
We are talking about user home directory data now which is on daily backup. But still is important. 
Perhaps we should use mounted network directories from data server in the future but this setup has some drawbacks as well. Not sure about this yet.

Many thanks

---

### Post by CharlesA on 2010-10-27
I cannot fathom why you'd want 30 minutes of battery power for a desktop machine. Server, sure, but not a desktop.

If there is a power outage, it's not like you are going to get work done.

---

### Post by Grenage on 2010-10-27
If you are in a rural area prone to short power cuts, it's not unusual to have a UPS capable of powering the PC for 30 minutes.

---

### Post by agurkas on 2010-10-27
> **CharlesA said:**
> I cannot fathom why you'd want 30 minutes of battery power for a desktop machine. Server, sure, but not a desktop.

If there is a power outage, it's not like you are going to get work done.

I think you are right. I must be paranoid :). I thought if someone is outside for half an hour this might happen. But that would be a really bad luck. We will buy 10 minute ups for workstations. You convince me.

I think one possibility in case people are away from desktops is to bring down all the boxes through network halt command if power outage is more than couple of minutes, to avoid hard crash.  I will think about this.

Many thanks

---

### Post by CharlesA on 2010-10-27
If you do get a bunch of UPSes, but sure to get ones that hook up to the PC. I use APC brand battery backups, since I can configure apcupsd to shutdown the machine when it's running on battery power for a certain amount of time.

I think you can do hibernate instead of shutdown, which would save any data that was open to the hard drive and then shutdown the machine, but I don't know how you'd set it up.

---

### Post by agurkas on 2010-10-27
> **Grenage said:**
> If you are in a rural area prone to short power cuts, it's not unusual to have a UPS capable of powering the PC for 30 minutes.

It is not a rural area actually, this particular office branch it is a one of manufacturing factories in Eastern Europe that has local office to manage all the manufacturing process, our main data server is in UK.
What sometimes happens in that factory even if all the power switches are clearly marked, when some people need to stop machinery they shut power down on wrong department.
Hard to imagine but it is true.

---

### Post by Grenage on 2010-10-27
Ah, that explains it then; 10 minutes would likely be fine.

Be thankful, we've got two UPSs the size of a van :(

---

### Post by agurkas on 2010-10-27
> **CharlesA said:**
> If you do get a bunch of UPSes, but sure to get ones that hook up to the PC. I use APC brand battery backups, since I can configure apcupsd to shutdown the machine when it's running on battery power for a certain amount of time.

I think you can do hibernate instead of shut-down, which would save any data that was open to the hard drive and then shut-down the machine, but I don't know how you'd set it up.

I actually never thought I could use this on Linux. apcupsd seems definitely a good option. I have seen ups with software available for windows (we don't have windows at all). But i did not investigate what options are on linux. I am too busy and since in that small town we have no linux guru I try to help how I can when I can when I arrive there or remotely with my limited hardware and networking skills. I am software developer actually. 
But you guys help me a lot here !

Many thanks

---

### Post by agurkas on 2010-10-27
> **Grenage said:**
> Ah, that explains it then; 10 minutes would likely be fine.

Be thankful, we've got two UPSs the size of a van :(


you must be running a data centre I guess :)

---

### Post by Grenage on 2010-10-27
> **agurkas said:**
> you must be running a data centre I guess :)

No, just a company that has ridiculous uptime requirements. :)

---

### Post by CharlesA on 2010-10-27
> **agurkas said:**
> I actually never thought I could use this on Linux. apcupsd seems definitely a good option. I have seen ups with software available for windows (we don't have windows at all). But i did not investigate what options are on linux. I am too busy and since in that small town we have no linux guru I try to help how I can when I can when I arrive there or remotely with my limited hardware and networking skills. I am software developer actually. 
But you guys help me a lot here !

Many thanks

The only one I know of is APC, There are other brands, but I don't know if they have similar software for Linux (they probably do for Windows tho).

> **Grenage said:**
> No, just a company that has ridiculous uptime requirements. :)

I worked at a company who had a couple huge diesel generators for when the power went out. No downtime, but I'm sure it was a bit expensive.

---

### Post by Grenage on 2010-10-27
> **CharlesA said:**
> The only one I know of is APC, There are other brands, but I don't know if they have similar software for Linux (they probably do for Windows tho).



I worked at a company who had a couple huge diesel generators for when the power went out. No downtime, but I'm sure it was a bit expensive.

Aye, we've a generator that kicks in at the same time - maintenance costs are rather high!

I'd second APC, by the way; their products are excellent.  It is however worth shopping around when you need new batteries, because you can save a lot buying them elsewhere.

---

### Post by CharlesA on 2010-10-27
> **Grenage said:**
> I'd second APC, by the way; their products are excellent.  It is however worth shopping around when you need new batteries, because you can save a lot buying them elsewhere.

Aye. Big +1 for shopping around for the batteries. I know you get a discount of some sort if you recycle the old ones with APC, but if you are able to get them at a cheaper price, go with the cheaper price.

---

### Post by agurkas on 2010-10-27
> **CharlesA said:**
> The only one I know of is APC, There are other brands, but I don't know if they have similar software for Linux (they probably do for Windows tho).

Charles, thanks for pointing APC. If you say it works with Linux software then I don't need to shop around for other brands. I did check their prices on Dell UK site I usually buy hardware. Prices are cheap for what I need. Will buy definitely.

That will be absolutely perfect solution for short cuts we have.

Many thanks !

---

### Post by CharlesA on 2010-10-27
No problem.

You can find some info on how to configure apcupsd [here]("https://help.ubuntu.com/community/apcupsd").

---

