---
title: "zd1211rw problems"
date: 2009-11-01
forum: General Help
---

### Post by sensay on 2009-11-01
Hi, im a very new linux/ubuntu user and im having a few problems. I've done my best so far but its got to the point i really need some help!

I'm running a fresh install of 9.10, the only significant package ive added is the kubuntu-desktop package (to try out both kde and gnome) and the restricted nvidia drivers.

Basically, when i boot up, several things can happen,

A) It boots up
B) It boots up but hangs at a black screen when the login screen should load
C) It drops me to a command line after giving me the error [   44.320022] 1-3:10: zs1211rw error ioread32(CR_REG1): -110 (this error is present in scenario A as well but in that case booting is still successful)
D) A whole list of filenames appears and the machine hangs (this happened just once though)

I know that zd1211rw is the module for my wireless adapter but beyond that i have no idea what the problem is.

I have noticed a significant depreciation in signal quality too. I never had this error in 9.04 and i had much better signals. In fact, if i connect my wifi adapter to my windows pc, which is further from the AP than i am, i get nearly full strength but im getting about 10% connectivity on this box.

Sometimes my dish will disconnect itself too and i have to unplug and plug it back in, doing this will often cause the system to outright freeze, to the point that if my dish disconnects itself i have to save everything im doing before i dare plug it back in :(

When im at the desktop there is usually a crash report available but when i try to view it i get various errors (different each load) about why it cannot be processed.

It does not matter if i am in the kde or gnome interface either, same errors.
  
Please help oh wonderful linux gurus!

---

### Post by sensay on 2009-11-02
BUMP. Please help this is driving me crazy, i want to stay using ubuntu but if i cant resolve this i dont know what i can do!

30 views and not one reply, is my question that unanswerable? If more information is required just ask andill give it.

TIA

---

### Post by sensay on 2009-11-02
So, i see threads being answered pretty quickly but mine is getting loads of views and no answers.

Am i doing something wrong? I've given as much detail as possible, if you tell me what else to add i will. Im stuck with a barely working system, I chose ubuntu for its ease of use and good community support, this is the first problem ive had and i cant believe noone is willing to help me!

I ask one more time, please help me

---

### Post by sensay on 2009-11-02
/me installs opensuse and forgets about the nightmare that was ubuntu

Thanks for the ******* help

---

### Post by coffeecat on 2009-11-02
I know you've probably gone by now, but I thought I'd respond to some of your points, if only for the record.

First, sorry to hear of your problems with Karmic, but I'll limit myself to the wireless zd1211rw issue.

> **sensay said:**
> I have noticed a significant depreciation in signal quality too. I never had this error in 9.04 and i had much better signals. In fact, if i connect my wifi adapter to my windows pc, which is further from the AP than i am, i get nearly full strength but im getting about 10% connectivity on this box.

I too use a wireless device with the zd1211 chip on my main desktop with Jaunty, and it works very well in Jaunty for me as well. I haven't yet installed Karmic on this machine (I'm using Karmic without problems on my laptop) so I was interested to hear what you say. I'm now posting from the Karmic live CD on the desktop using the zd1211 and I can confirm that Network Manager reports a weaker signal and a speed of only 1Mbit/s. But frankly I don't believe this. I've done a bit of browsing and everything feels a lot snappier than that. Not a scientific impression I agree, but there is a bug with one of the Realtek chipsets which causes Network Manager to report the wrong signal strength and connection speed. Perhaps the same thing is happening here.

So - were you only going by the reported figures or was connectivity really slower and less reliable than in Jaunty? In fact, somewhat ironically, I heard from a reliable source that there is a bug in the Jaunty version of the zd1211rw driver that causes it to report a signal strength much **higher** than it really is. Perhaps you've got used to an erroneously high figure and the (possibly) accurate Karmic figure has discomposed you.

Just a thought.

> **sensay said:**
> So, i see threads being answered pretty quickly but mine is getting loads of views and no answers.

Am i doing something wrong?

No, you were doing nothing wrong. But the zd1211 chipset is relatively rare. There may not be many people using it, and even fewer using it in Karmic just yet. Without personal experience of this particular chipset, there's not much point in posting. Perhaps this is why you got no responses.

> **sensay said:**
> /me installs opensuse and forgets about the nightmare that was ubuntu

Thanks for the ******* help

Well, good luck with Suse. Use whatever works. However, if there truly has been a regression with the Karmic zd1211 driver then you may be in for trouble with Suse as well. Explanation: Jaunty uses the 2.6.28 kernel, which is where the wireless drivers are to be found. Karmic uses the 2.6.31 kernel and if this is a true regression, then this is a kernel problem not an Ubuntu one. I can't remember which version of the kernel the current version of Suse uses, but I'm sure it's earlier than 2.6.31. Which means that this problem (if problem there is) may come to bite the new version of Suse that is due to be released very soon.

---

### Post by sensay on 2009-11-02
Still Here. 

Apologies for my outburst its just pretty frustrating seeing posts answered left right and centre and finding myself on page 5 or something after 15 minutes!

Connectivity on the device is definately down. I used to download via synaptic at around 700 kb/s and from http at around 500, currently my synaptic downloads anywhere between 4000 BYTES per second - 200 kb/s but it varies wildy, its never a constant speed. HTTP currently gives me a sustained 300 kb.s maximum (why is http a contstant download speed but synaptic is a huge mess?) Web browsing however feels as fast as ever (probably ok as html pages dont take much to load).

What about the rest of my problems? Lets assume i could live with piss poor internet, what is to be done with the crashing and failing to load?

> **sensay said:**
> 
Sometimes my dish will disconnect itself too and i have to unplug and plug it back in, doing this will often cause the system to outright freeze, to the point that if my dish disconnects itself i have to save everything im doing before i dare plug it back in :(

When im at the desktop there is usually a crash report available but when i try to view it i get various errors (different each load) about why it cannot be processed.


> **sensay said:**
> When i boot up, several things can happen,

A) It boots up
B) It boots up but hangs at a black screen when the login screen should load
C) It drops me to a command line after giving me the error [ 44.320022] 1-3:10: zs1211rw error ioread32(CR_REG1): -110 (this error is present in scenario A as well but in that case booting is still successful)
D) A whole list of filenames appears and the machine hangs (this happened just once though)




Thank you very much for your reply, it was helpful and appreciated.

EDIT: Ok, i just tried a http download from firefox, terminal using wget and some updates via the update manager. This time i got a consistent speed between them all (around 600k) this is in the realms of normal speed for me and a speedtest confirms this, according to network manaqger im connected at 7%, obviously its bugged! However, a restart still gives me the error message i mentioned in the first post (ioread) and i have had failure to boot several times today.

---

### Post by coffeecat on 2009-11-02
> **sensay said:**
>  Connectivity on the device is definately down. I used to download via synaptic at around 700 kb/s and from http at around 500, currently my synaptic downloads anywhere between 4000 BYTES per second - 200 kb/s but it varies wildy, its never a constant speed. HTTP currently gives me a sustained 300 kb.s maximum (why is http a contstant download speed but synaptic is a huge mess?) Web browsing however feels as fast as ever (probably ok as html pages dont take much to load).

That's interesting. As far as  Synaptic is concerned, this may be a server issue - nothing to do with your end - I've often seen it. When the download servers get overloaded, they either slow down horribly or jump around in speed. Try changing your server (Synaptic > Settings > Repositories > Ubuntu Software Tab) and see if that makes any difference.

As for the other reported figures, this may be erroneous figures rather than a real slowdown. I've just proven to myself that the connection figure (at least on my machine) is just plain wrong. I've now transferred to my No 2 desktop and brought my zd1211 dongle with me. In Jaunty I get 100% signal strength (rubbish! :wink: ), but in Karmic (this time from a HD install) I get only 45-49%. And in Karmic NM reports the connection speed as 1Mb/s. **However**, no less than three broadband speed test sites report a download figure of between 3 and 4 Mb/s. Hmmm. A connection speed between a distant server and my desktop three times the connection speed between my desktop and my router. I don't think so!

**And also** :), I've just done a terminal apt-get install (in Karmic) and was getting reported download speeds just about the same as with the BB speed tests. I'm getting the impression that the performance of the zd1211 is going to be about the same in Jaunty and Karmic. It's just that the connection figures are all wrong - which I agree is irritating - but no more wrong than in Jaunty. It's just that they've gone the other way.

It's interesting that web-browsing feels just as fast for you.

> **sensay said:**
>  What about the rest of my problems? Lets assume i could live with piss poor internet, what is to be done with the crashing and failing to load?

Well, putting aside the piss-poor internet, I'm not going to be of much help. My experience of Karmic has been mostly positive. The few small problems I have I'm sure will be ironed out quite soon as bigfixes and updates filter through. 

I've read about some problems with nvidia drivers, so it's worth searching the forums for anything on that. For the other issues, include some details of relevant hardware when you do your searches. The fact that you're having problems which I'm not must be down to hardware differences.

If you're as frustrated with the forum search facility as most people here (it's acknowledged to be poor), here's a useful tip. Go to google and search for:

site:ubuntuforums.org your search string.

You get much better results.

**Edit:** I've just noticed your edit. So we're agreed that the download speeds are OK, just the reported statistics are nonsense. :p

---

### Post by sensay on 2009-11-02
The inaccurate representation of my network connectivity is annoying but certainly no major problem,i agree.

Having seen that i am capable of getting my correct speeds im happy enough.

Ok, i wanna get the business of crashing sorted out.

Specs: Asus M2N SLI Deluxe Motherboard
          Amd athlon 64 x2 @ 3.0Ghz
         1GB DDR2 RAM
          Nvidia 9800GT
         OCZ stealthXtreme 550w PSU
         5.1 Trust sc-5250 sound card (though im prsently using the onboard sound                    because my cables actually dont fit in the trust card......yea)

Is there a logfile i can post to shed some light? I dunno where id find one, sorry

---

### Post by coffeecat on 2009-11-02
> **sensay said:**
> Is there a logfile i can post to shed some light? I dunno where id find one, sorry

I'm back in Jaunty atm, and the best place to look in Jaunty would be System > Administration > Log File Viewer. I assume it would be in the same place in Karmic. "messages' would be the one to go for to see if there is anything logged at the time you get a crash. Or perhaps 'syslog'. The actual logs are in /var/log.

You might want to start a new thread about the crashing. This one is titled 'zd1211rw problems' so it might deflect members who would be able to help you but would be put off by the mention of zd1211rw.

Good luck.

---

### Post by madsmaddad on 2009-11-06
Don't go away! 

I have been following thread 1307396 in an attempt to resolve my wireless problems in 9.10. I upgraded over the air from 9.04, and then lost wireless. 

I am using the 3Com wireless USB stick that uses ZD1211 chipset. 

At the moment thinking about trying to downgrade to 9.04. unless I can get this working. Doing the things  mentioned in note 9 of that other thread does not work for me. 

Will post any further things I find. 
Here is a bit of my dmesg file: Note set to US settings. I would like to find out how to change those to UK. 

   22.748045] intel8x0: clocking to 48000
   23.627566] usb 1-1: firmware: requesting zd1211/zd1211_ub
   23.775704] usb 1-1: firmware version 0x4330 and device bootcode version 0x4721 differ 
   23.775713] usb 1-1: firmware: requesting zd1211/zd1211_ur 
   23.933507] usb 1-1: firmware: requesting zd1211/zd1211_uphr 
   24.013729] zd1211rw 1-1:1.0: firmware version 4605
   24.053717] zd1211rw 1-1:1.0: zd1211 chip 6891:a727 v4721 high 00-14-7c RF2959_RF pa0 g----   
   24.056857] cfg80211: Calling CRDA for country: US  
   24.060566] cfg80211: Regulatory domain changed to country: US   
   24.060573]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
   24.060579]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)   
   24.060584]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)   
   24.060589]  (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
   24.060594]  (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
   24.060599]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm) 
   24.088124] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
   28.285947] agpgart-sis 0000:00:00.0: AGP 3.5 bridge 
   28.285971] agpgart-sis 0000:00:00.0: bridge is in legacy mode, falling back to 2.x  
   28.285980] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode 
   28.286036] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode 
   35.640808] CPU0 attaching NULL sched-domain. 
   35.640821] CPU1 attaching NULL sched-domain.

---

### Post by coffeecat on 2009-11-06
If you mean [http://ubuntuforums.org/showthread.php?t=1307396](http://ubuntuforums.org/showthread.php?t=1307396) then I don't see that it has any relevance to your situation. You are using a zd1211 wireless nic. The OP is using an Intel and another poster is using a Marvell. Those chipsets use different drivers and firmware and, what with all the variables introduced doing an upgrade rather than a clean install, I doubt whether you can get anything useful from that thread.

I don't know why you lost wireless connectivity when you upgraded. As you can see from my and the OP's post, the zd1211 is working OK in Karmic, it's just that Network Manager reports wrong connection speeds (and probably a wrong signal strength as well - I'd put money on that).

Try this: boot up with the Karmic live CD with the 3COM stick plugged in. Now try to connect with network manager. Does it connect? If yes, then there's some issue with the upgrade that needs to be investigated - but **only** in the context of the Zydas chipset. If not, then - well I don't know. But try the CD.

---

### Post by madsmaddad on 2009-11-07
You are absolutely right. Thank You. I booted from a CD, set up wireless and it worked. Now all I need to do is discover how to install over my existing setup!

Thanks,

---

### Post by coffeecat on 2009-11-07
> **madsmaddad said:**
> Now all I need to do is discover how to install over my existing setup!

That's quite straightforward. If you mean you want to do a fresh install of Karmic, wiping out your present install in the process, simply boot up the live CD, start the installer up, and at the partitioning stage choose "manual". Select your current root (/) partition for the root (/) of the new install, choose the filesystem you want (ext3 or 4) and mark it for formatting. Don't worry about the swap partition, that will be picked up automatically. The installer will then reformat the root partition of the old install, write all the files for the new install to that partition, and do all the other stuff that is needed.

If you need any further help, just post back with some details of your present setup. In particular, open a terminal and post the output of:

```
sudo fdisk -l
```

That will give us details of your current partition layout.

---

### Post by madsmaddad on 2009-11-08
Coffeecat, Thanks for the help, I installed karmic to another partition that it created, and all is fine and happy now. Glad I didn't get rid of previous stuff as I needed to go into it to do a backup of evolution. Then I could import into the karmic evolution all my history. 

Eventually I'll empty my old partition and use it for data. 

But Thanks for help and advice. 

Now if we could only sort sensay out......

---

