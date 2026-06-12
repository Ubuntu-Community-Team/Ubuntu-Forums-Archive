---
title: "Very poor performance - 10.10"
date: 2011-10-08
forum: General Help
---

### Post by XEtedBear on 2011-10-08
Not sure which forum category this should be in - if I have chosen the wrong one, somebody please advise.

I just did a 'clean' install of 10.10 on a Fujitsu Scaleo EV desktop. The performance is so bad that there is something clearly wrong, but nothing obvious occurs to me.

Some qualitative data:
Install - took more than 1 hour after I had answered all the setup questions

Time to boot: about 3 minutes to Login Screen

Time to show desktop after login: about 3 minutes

Time to open a sub-menu Window from 'Places': about 20 to 40 seconds

Time to open OpenOffice Writer: about 40 seconds

All these timings are on the system as installed from the 10.10 distribution CD, without any modifications to the system.

About the hardware: 
Core 2 Duo Intel processor running at 1.86 GHz (unclocked); 3MB L2 cache.
2 GB DDR2 RAM
250 GB Seagate SATA drive 7200 rpm
Intel G965 onboard graphics (yeah, not great, but not this bad!)

DVMT mode set to FIXED (at 256 MB) in BIOS

HPET support enabled
AHCI support enabled

The system overall is far, far slower than a 10 year old, 2 GHz
1 GB DDR RAM, single core AMD Venice processor on an old ASUS K8V motherboard, with a slow disk.


Where should I be looking for a problem cause?

---

### Post by raja.genupula on 2011-10-08
look at your system start up application list. I think that list was heavy , so please remove useless application from startup.

 i think then everything will be fine.

---

### Post by ajgreeny on 2011-10-08
> **raja.genupula said:**
> look at your system start up application list. I think that list was heavy , so please remove useless application from startup.

 i think then everything will be fine.
That alone will not account for those times quoted by the OP.

@OP  Are you sure the CD you used was a good one and the iso file you burned was good?  Even on my old laptop ubuntu boots from power button to a desktop in about 90 seconds or less, I have not timed it for a long time now.

---

### Post by 2F4U on 2011-10-08
Did you look into the system log file if there are any errors reported?

---

### Post by Quackers on 2011-10-08
Were there any usb devices or drives plugged in at the time?

---

### Post by mastablasta on 2011-10-08
check the top command in terminal and system monitor to see if there is any applicaiton that is running and taking too much ram/CPU.

---

### Post by raja.genupula on 2011-10-08
htop also good one. you could try it.
```
sudo apt-get install htop
```

---

### Post by Jouke74 on 2011-10-08
Given the size and brand of your Harddrive, I guess it might have reached the end of it's life (a really big guess which might not be true at all). Could you check in the disk utility what the smart status of the drive is, if it show any warnings?

---

### Post by Gs Dewd on 2011-10-08
> **Jouke74 said:**
> Given the size and brand of your Harddrive, I guess it might have reached the end of it's life (a really big guess which might not be true at all). Could you check in the disk utility what the smart status of the drive is, if it show any warnings?

I don't think this is the case considering I am running 11.04 on a old Amd socket a system ( athlon 2500+ xp-m @ 2.2ghz (3200+ speed)2 gb pc3200 mem and a radeon 1550 xge ) and it runs very quick on it. I also installed 10.04 on a very old kt7a system ( athlon xp 2100+ , 768 mb pc133 mem, nvidia geforce fx 5700) and it runs quick also. To me it seems you don't need to have the top of the line hardware to run ubuntu. I think you may have look into the iso you burned. Something did not install right. If it was a vid problem I think it would install and boot fine just wouldn't have the 3d environment. Sound as if it has a botched install. Do a error report and post the findings here.

---

### Post by raja.genupula on 2011-10-08
I think op facing many problems.
I know some issues which are going to be cause for this.
 
1.His startup app list loaded with heavy things
2.In his current running applications , some applications are using high RAM
3.May be he is running some database's in his system
4.System updates may be not going.

these are the things i know.

---

### Post by Jouke74 on 2011-10-09
> **Gs Dewd said:**
> I don't think this is the case considering I am running 11.04 on a old Amd socket a system ( athlon 2500+ xp-m @ 2.2ghz (3200+ speed)2 gb pc3200 mem and a radeon 1550 xge ) and it runs very quick on it. I also installed 10.04 on a very old kt7a system ( athlon xp 2100+ , 768 mb pc133 mem, nvidia geforce fx 5700) and it runs quick also. To me it seems you don't need to have the top of the line hardware to run ubuntu. I think you may have look into the iso you burned. Something did not install right. If it was a vid problem I think it would install and boot fine just wouldn't have the 3d environment. Sound as if it has a botched install. Do a error report and post the findings here.

Yes I know Ubuntu runs well on old hardware, but if your harddisk is damaged (this one, not the ones in the other systems) the IO will dramatically slow down. Meaning it takes a long time to read and write everything from the drive. Given your first post this is possible... (and easy to check if your run the disk utility under System > Administration).

---

### Post by Gs Dewd on 2011-10-09
> **Jouke74 said:**
> Yes I know Ubuntu runs well on old hardware, but if your harddisk is damaged (this one, not the ones in the other systems) the IO will dramatically slow down. Meaning it takes a long time to read and write everything from the drive. Given your first post this is possible... (and easy to check if your run the disk utility under System > Administration).

Ah you mean the op might have drive probs. right? lol My drives are great. And the systems run great. So op that may be something else you can try. Check the drives integrity.

---

### Post by XEtedBear on 2011-10-10
> **raja.genupula said:**
> look at your system start up application list. I think that list was heavy , so please remove useless application from startup.

 i think then everything will be fine.

Thanks for your suggestion, but...
1. I am not aware of what a 'startup list' in a Linux environment, so I cannot tell you what is in it.
2. Following from this, how do you know that this list is heavy? Have you seen it? If so, can you tell me what is in it and how to remove items from it?

---

### Post by XEtedBear on 2011-10-10
> **ajgreeny said:**
> That alone will not account for those times quoted by the OP.

@OP  Are you sure the CD you used was a good one and the iso file you burned was good?  Even on my old laptop ubuntu boots from power button to a desktop in about 90 seconds or less, I have not timed it for a long time now.

I confess that I didn't do an MP5 check on the ISO file, but I have used the CD I burned from it to install on the old Asus K8V I mentioned in my original post. I also used it for my 'production' system (which I am using at this point to create this reply). So I think the evidence is that the ISO/CD are both good enough - or is that an invalid bit of logic?

---

### Post by XEtedBear on 2011-10-10
> **2F4U said:**
> Did you look into the system log file if there are any errors reported?

Thanks for this tip. I have never used the System Log Viewer before and am surprised at how many log files there are to view. I have opened the files 'syslog' and 'syslog1' but cannot tell if there are errors being reported or not - it's all information that I do not - for the most part - understand.

There are also several hundred lines in the log, so it is not possible to easily examine it all.

---

### Post by XEtedBear on 2011-10-10
> **Quackers said:**
> Were there any usb devices or drives plugged in at the time?

I'm not sure what you mean by 'at the time'. If you ean 'during installation;, I can say 'no' - having learned my lesson when installing Ubuntu last year with my main, critically important back-up USB drive connected and carefully wiped clean during install!

I can say that the presence or absence of USB devices does not seem to make any discernible difference during use.

---

### Post by XEtedBear on 2011-10-10
> **mastablasta said:**
> check the top command in terminal and system monitor to see if there is any applicaiton that is running and taking too much ram/CPU.

Thanks for this tip. Another command that is new to me!

top shows that the top 3 CPU users are taking about 25% of the compute resource and are either 'root' or my userid. No applications are listed in top as taking any significant amount of CPU.

The top 3 CPU users are using about 2% of RAm

System monitor show total RAM usage at about 12% of available resources, with total CPU utilisation at about 35% (plus,minus 15%) when there is nothing at all running on the machine and I am doing no typing (I'm creating this post on another Ubuntu machine). This CPU load surprises me - it's using about about 8 times more power doing nothing than I used to use to run my business on, with a 32 MB 120MHz PII last week (at least it seems that way....)

---

### Post by XEtedBear on 2011-10-10
> **raja.genupula said:**
> htop also good one. you could try it.
```
sudo apt-get install htop
```

Hmm, interesting: opening Terminal took 7 seconds, prompt for password after entering above command took 30 seconds. Install took about 15 seconds

Application shows average CPU at about 30%, 203 tasks running, 250 out of 1999 MB RAM being used.htop is largest CPU consumer by far - about 95^ of total load.

Performance still excruciatingly poor.

---

### Post by XEtedBear on 2011-10-10
> **Jouke74 said:**
> Given the size and brand of your Harddrive, I guess it might have reached the end of it's life (a really big guess which might not be true at all). Could you check in the disk utility what the smart status of the drive is, if it show any warnings?

Thanks for this advice. The utility appears to be another Linux 'content free ' application. 

No, correct that; 2 minutes after double clicking on the hard disk icon I do get some output (but this window greys out as if the system was going into sleep mode).

The 'Overall Assessment' is 'healthy'. The output from the SMART data report shows all attributes, except 1 as being either 'Good' or 'N?A'. The 1 failure is no. 190 (Airflow Temperature) which shows 'Failed in the past', with a current value of 47 Deg. Celsius. That doesn't seem like a problem now.

Total 'powered on' time is 182.2 days - so hardly used, with 2365 power cycles - very low numbers I would have thought.

---

### Post by XEtedBear on 2011-10-10
> **Gs Dewd said:**
>  Do a error report and post the findings here.

OK, I will do, but you could be more specific on how I generate such a report? Thanks.

---

### Post by XEtedBear on 2011-10-10
> **raja.genupula said:**
> I think op facing many problems.
I know some issues which are going to be cause for this.
 
1.His startup app list loaded with heavy things
2.In his current running applications , some applications are using high RAM
3.May be he is running some database's in his system
4.System updates may be not going.

these are the things i know.

1. Already commented about this - isn't 'startup list a Windows item ?
2. I'm not running any applications. This is just a freshly installed, updated system, that has not been used to do any work.
3. Point 2 also include databases - I class them as applications.
4. System appears to be updating correctly. Certainly no error message when ever I run update.

---

### Post by XEtedBear on 2011-10-10
> **Jouke74 said:**
> Yes I know Ubuntu runs well on old hardware, but if your harddisk is damaged (this one, not the ones in the other systems) the IO will dramatically slow down. Meaning it takes a long time to read and write everything from the drive. Given your first post this is possible... (and easy to check if your run the disk utility under System > Administration).

Previous reply shows hard disk to be healthy, but I will run tests again.

---

### Post by XEtedBear on 2011-10-10
I think I may have found the problem cause and the obvious solution:

For most attempts the system start for a long time in BIOS with the words 'checking DMI Pool...' - or words to that effect.

I disembowelled the box (not a straight forward 'open the case' process with this product), found the Clear CMOS jumper and did that.

Boot up and operation is now very much faster - comparable to my main Ubuntu dual core socket 939 AMD Athlon 3100 (running at 2 Gz, but with a small L2 cache).

I notice that the harddisk is a Barracuda and the connectors look like SATA2, so I am expecting good performance when I actually put this machine to work.

I will close this thread in a few hours, if there are no further comments. Thanks again for all the suggestions.

---

### Post by Johnb0y on 2011-10-11
glad to hear you got it running better, knew it wasnt Ubuntu to blame...lol!

p.s. dont forget to mark as solved if it is.... :p

---

### Post by Gs Dewd on 2011-10-11
Glad to hear you found your problem. I knew the hardware was more then plenty.

---

### Post by XEtedBear on 2011-10-13
Ah Wishful thinking.

One of the things  used to like about computers back in the early 60s was that they always responded in the same way to the same stimulus. Today, there is never a dull moment - or indeed a spare moment - when looking after a computer. Especially if Linux is installed - usually not the same result twice in my expereince.

Now, having made no change whatsoever in the system (but who know what others did ?0, I'm back to a 15 minute BIOS POST , a 7 minute cycle to log on and a 55 second time to load Firefox. Waking up from 'screen save' mode takes about 7 seconds.

I guess that Ubuntu 10.10 it just too much of a load for this modern technology. That 10 year AMD stuff seems much more robust....

---

### Post by XEtedBear on 2011-10-16
> **Gs Dewd said:**
> Glad to hear you found your problem. I knew the hardware was more then plenty.

You are quite right of course - the hardware is plenty.

After faffing about for days trying to understand the delay after the BIOS message "Verifying DMI Pool Data . . . " I concluded that BIOS wasn't the problem. I removed the 2 'conventional' adapter cards from the system and now it runs much closer to what I expect.

The 2 cards that I removed are:

1. An Asus combined TV/FM tuner card
2. An unidentified card which provides HDMI and S Video (Output I assume) for driving a TV. This card in turn has 3  cable connection to a daughter board which is connected to most of the back-panel audio & video connections (of which there are many).

I guess that Ubuntu has been over whelmed by trying to support this un-identified TV output card. Could this be possible? If so, is it possible that I could find a more effective driver? How could I identify this card?

---

### Post by dacoolbg on 2012-05-14
Anyone else affected by this bug: _[Poor performance on Intel® 965GM x86/MMX/SSE2]("http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/984452")_? If yes, then please go and vote for it as shown here: _[how to vote]("http://goo.gl/wqOjf")_ (*you have to be **logged in***). Thanks in advance, hopefully it will get fixed sooner.

---

