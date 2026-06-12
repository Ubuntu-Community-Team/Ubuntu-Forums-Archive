---
title: "Torrenting stops network activity"
date: 2011-08-23
forum: General Help
---

### Post by darthpbal on 2011-08-23
For some reason whenever I'm torrenting after a certain amount of time my networking ability just stops. My network traffic shoots down to zero and I can't bring anything like the ability to request a website back until I restart. Any idea whats happening?

---

### Post by donaldsmith on 2011-08-23
speed up downloads transmission. All programs will have their bittorrent communication flows freely in and out to achieve higher download speeds, and it's basically what this guide is about.

---

### Post by darthpbal on 2011-08-23
The problem isn't that transmission is making everything slow at all. The problem is that it brings all networking to a halt. Even when it's closed and quit the network doesn't revive until a restart. If that guide does help with this can you tell me where to find one?

---

### Post by kartabosh on 2011-08-23
> **darthpbal said:**
> The problem isn't that transmission is making everything slow at all. The problem is that it brings all networking to a halt. Even when it's closed and quit the network doesn't revive until a restart. If that guide does help with this can you tell me where to find one?

does the torrent client still work?

---

### Post by darthpbal on 2011-08-23
> **kartabosh said:**
> does the torrent client still work?

What do you mean by "still work?" It starts up and everything and shows that there is a torrent still there, but it's up and down speed are 0B/s. I mean that's all that happens. If you mean something else by your question I'd be happy to elaborate.

---

### Post by kartabosh on 2011-08-23
well, long time ago when i would start a torrent client it would take up all my bandwidth
as you said, everything else related to the internet would stop working
email client, web browser, radios, everything would stop working but the torrent was still downloading
that's what i meant 

did you have this problem with other distros?

---

### Post by darthpbal on 2011-08-23
Nope. I mean my internet connection is pretty fast, and once upon a time I didn't have this problem, I would just experience slight speed reduction. But seriously, what this is doing is killing my network fully but only for my machine. Because when I get on my network with my other laptop after the speed takes its dive bomb, I still have a speedy connection on the other laptop on the same network. I've only used Ubuntu 10.10 and 11.04, and I've had this problem on both. But initially I didn't. For a long time I could have a million torrents if i wanted, and all that would happen is speed reduction. But a while ago it just started to act screwy. Even when I installed fresh 11.04, it still had it for some reason.

---

### Post by kartabosh on 2011-08-23
did you change any piece of hardware in that time? 
like a new router? 
in my case, it was the bad router that stopped internet activity

---

### Post by darthpbal on 2011-08-23
Nope. Nothing has changed. If it was a bad router, why would everything be fixed when my laptop, which is not connected except by wifi, restarts?

---

### Post by darthpbal on 2011-08-23
Just happened again. I have system monitor open, and pandora wasn't able to switch a song, so I switched to system monitor and the graph showed aggressive activity all over the place. Then all of a sudden dead drop to zero activity.

---

### Post by kartabosh on 2011-08-23
so let me get this straight
you have a pc and a laptop connected to a router then the internet stops working but when the laptop drops the wlan connection the internet is back up?

---

### Post by darthpbal on 2011-08-23
I have two laptops and a desktop. One laptop starts to try to download a torrent. All machines can still download things and everything. After some time, the one laptop downing a torrent, while still connected to the wireless signal, suddenly stops downing or upping any amount of data at all. All while this is happening the other two machines are completely unaffected by any of this. They can still surf the web even after the torrenting machine's network activity stops. Nothing loses connection at all. And the bystander machines are always able to surf the web when the torrenting machine still has network activity. Sorry for not being very clear.

---

### Post by kartabosh on 2011-08-23
it could be that your router has a bad IP Flood Detection
that's what happened to me
it would confuse the ongoing torrent activity with a flood and it stopped the internet on that machine
i had to disable IP Flood Detection for it to work again 
you might want to check your router settings

---

### Post by darthpbal on 2011-08-23
How would I do such a thing? And why would it not do it before, but do it now? Because I haven't always had this problem, but I've always had that router.

---

### Post by kartabosh on 2011-08-23
i don't know all possible answeres, i am just telling you what happened to me, maybe it's related

[http://portforward.com/](http://portforward.com/) has most of the routers available 
pick yours -> "Click here to skip this advertisement...   "
choose any application and among the first lines you should have your router administration address 
mine is 192.168.1.1

---

### Post by darthpbal on 2011-08-23
That sucks, sounds like this is gonna take a while especially since I don;t fully know how to do this.

---

### Post by gbrowning on 2011-09-10
synopsis for my situation: Torrents slow to zero, then network activity stops.  Rebooting the machine gets torrents back to full speed and restores Web and email but they slow to a stop again with time.
   I have a good machine with a good Internet connection.  These symptoms appeared after moving up to Natty from Lucid. Thought the problem was with "Transmission" but the same symptoms appear now that I switched to "qbitorrent".
   My son uses WIFI through the same router on a windows laptop and does not have the same problem.  In addition I started a 5gb seed and had him start to leach at the same time.  We found each other and the files transferred very quickly.  At that point I was uploading so...it appears to be tied to length of time dowloading a torrent.
  Mentioned above is "Flooding". this may be the problem.....will try to work with that.

---

### Post by SeijiSensei on 2011-09-10
Many consumer-grade routers have small "NAT" tables that can fill up quickly if a torrent connects to lots of remote peers.  The problem you describe is a common symptom of this limitation.  Next time you suddenly cannot connect, try disconnecting the power from your router, waiting five or ten seconds, then reconnecting the power.  Can you surf once again?

If rebooting the router solves the problem, you need to look into reducing the number of simultaneous connections (note: not bandwidth) that the torrent client makes.  I find if I don't limit my client to 50 or so total connections, my router falls over.  The default settings in many clients are much larger than this.

---

### Post by gbrowning on 2011-09-10
checked the router settings and found that packet flood detection is not selected so that is not the problem.
    I do not know much about the protocols for torrent transfers.  Is it possible that the UDP session time-out has something to do with it?

---

### Post by SeijiSensei on 2011-09-11
Bittorrent uses TCP not UDP.  Did you try rebooting the router?  Limiting the number of simultaneous connections your client sets up?

---

### Post by gbrowning on 2011-09-11
Thank you Sieji, did not see your post before my last response.
    I have seen the peer limitation suggestion before but not directed at these exact symptoms. The NAT table seems like the a good suspect.  This has happened when downloading Torrents with a large number of seeders.  It happened yesterday when flipping through lots of web pages and no torrent was involved.  This computer is usually on for only several hours each day.  Yesterday it had been on for more than 24 hours before I had to reboot.
    A couple of questions about NAT tables.....re-booting the computer seems to clear the table.  Rebooting the router would also clear the table.  Are there other ways to clear the table or clear the oldest portions of the table? Is there a normally a time to live for the oldest table entries?
    I will be out of town for the next three days  and will be on an ancient Windows laptop.  If there is time today I will try to initiate an internet failure and try to re-boot the router.

---

### Post by Zephilinox on 2011-09-11
I had this problem when I was using windows, but only with torrents with many (hundreds) of seeders, lowering the max connections solved the problem, it should solve yours as well, in Transmission's settings go to the Network tab and lower "maximum peers per torrent" I'd suggest 50% of what it is currently set at, then gradually increase it if that works.

---

### Post by SeijiSensei on 2011-09-11
> **gbrowning said:**
> A couple of questions about NAT tables.....re-booting the computer seems to clear the table.  Rebooting the router would also clear the table.  Are there other ways to clear the table or clear the oldest portions of the table? Is there a normally a time to live for the oldest table entries?

I know of no other ways to clear the NAT table.  Rebooting the router is the quickest and easiest solution I've found. I'm sure all the connections have TTLs, but they're probably long enough that they fill the router's memory.

I hear that "gaming" routers have larger tables and don't suffer from this problem as often.  I also don't know whether replacing the stock firmware in the router with something like Tomato or DD-WRT would help.  After I reduced the number of simultaneous connections in KTorrent, I haven't had a lockup since.

---

### Post by gbrowning on 2011-09-11
It does not seem to be the NAT table but let me tell you what steps I have taken.
   unplugged the router for 10 seconds...no effect
   unplugged the router for 5 mins    no effect
   restarted Ubuntu (Natty)  no effect this time.

   unplugged my NIC (card) and plugged it into the native ethernet on the motherboard......viola.

   It is not a hardware problem but somehow the ethernet I/o is involved.  I purchased a card a month ago because internet stopped working.  Thought my son had been physically harsh with the computer.  I am now using the same ethernet port which stopped working a month ago.

  can this still be NAT?  I do not see how.   It is possible that the router did not lose power completely, it is part of my phone system and could be fed over the phone lines with their native 28 volts.
    do not have time to play, am off to the airport.... can read forums later but will not be able to physically attempt anything on this computer. until Thursday at the earliest and Friday is most likely

---

### Post by ubudog on 2011-09-11
May I ask what ISP you use?  It could be that your ISP is blocking bit-torrent.

---

### Post by gbrowning on 2011-09-12
I am using AT&T.

---

### Post by gbrowning on 2011-09-12
I read through this thread  [http://ubuntuforums.org/showthread.php?t=1837560&highlight=Torrenting+stops+network&page=2](http://ubuntuforums.org/showthread.php?t=1837560&highlight=Torrenting+stops+network&page=2)   Limiting the upstream traffic is suggested.  This is consistent with the symptoms in that the network does not seem to break until the torrents have been transferring for a while and there are plenty of files to be discovered through peers.
   It does not explain why changing NIC ports worked, that could be coincidence.  Soo...looking foreword to getting my hands back on the machine.

---

### Post by soryu on 2011-09-13
same thing here started happening on fresh install of 11.04.
limiting torrent bandwith seems to be working
sucks though doesn't happen on windows
+1 windows:confused:

---

### Post by gbrowning on 2011-09-21
OK, someone please check my math.  Upstream is limited to 5040 Kbps by the provider but Qbittorrent limits speed using KiB/s. 5040/8 = 630 KBps then 630*(1000/1024)= 615 KiB/s. I want to limit upstream to 75% of max so looking at 615*.75 = 461.
   I will give this number a shot and see if this solves the problem for me.  It seems to have solved the problem for others.

---

### Post by gbrowning on 2011-09-22
I took the step of limiting the upstream to a calculated 75% of the allowed bandwidth.  This has seemed to work.  I am not yet willing to call this quirk solved until it has run for a couple of days and has not crashed my network.
     This whole scenario does not make complete sense to me.  I could see why the upstream bottleneck could really slow the system down but the download speeds were essentially zero.  Why did this NOT happen under Lucid but now does happen under Natty? Why does this affect the LAN when it should only affect the link between the Cable Modem and the ISP? In my mind this fix should not work and yet....

---

### Post by ingramproductions on 2011-09-22
Here is a good article on how to configure Transmission so it doesn't bog down your connection:

[http://itswapshop.com/content/how-configure-transmission-ubuntu-no-network-lag]("http://itswapshop.com/content/how-configure-transmission-ubuntu-no-network-lag")

---

### Post by ubudog on 2011-09-22
> **ingramproductions said:**
> Here is a good article on how to configure Transmission so it doesn't bog down your connection:

[http://itswapshop.com/content/how-configure-transmission-ubuntu-no-network-lag]("http://itswapshop.com/content/how-configure-transmission-ubuntu-no-network-lag")

+1, great link!

---

### Post by SpatryX on 2011-09-22
I have encountered a similar problem with both transmission and deluge. I have found that it is usually best to reboot my modem when this occurs... My ISP could also be throttling my bandwidth... I have noticed that problem mostly happens when downloading torrents from public trackers... I never have issues when downloading torrents from private trackers...

Hope that helps...

---

### Post by gbrowning on 2011-09-23
OK! Thank you to all. Playing with the upload settings seems to have done the trick.
Summary as I understand it...please correct me if I have it wrong...
    Torrenting stops network activity.  After a period of time using a bit torrent client network activity grinds to only a few bits per second. No WWW and no email,  I could not even see my router through my browser.  Rebooting the computer restarted the network, rebooting the router did not. 
    Potential sources of the problem were suggested.  These included flood detection in the router, throttling by the ISP, NAT overflow, and Thrashing by the torrent software.
    The router was not set to detect flooding, an internet search could find no complaints of ATT throttling torrents, resetting the router (and thus the NAT) did not work but limiting the upload speed of the bit torrent is working, for now.
     I work construction so it is hard for me to understand things that do not look like nails but the number of connections required for Qbittorrent and for Transmission  (and apparently deluge) to try to maximize upload speed caused the system to thrash looking for more connections. 
     Close to correct?  with a bit of editing from someone here with more knowledge we can get this marked "solved"

---

### Post by r2u1s1h2 on 2011-11-17
I have the same problem. I will leave transmission running over night or for any length of time, and when I come back it has halted my network. Can't seem to find much on the issue, but I'll post any progress here.

[Edit]
This link suggests it might be that our gateways cannot handle many connections at the same time. Maybe try limiting the number of connections per torrent/overall. I will try this and post the results.

[http://askubuntu.com/questions/44268/transmission-causes-internet-to-stop-working-log-off-required-to-make-it-work](http://askubuntu.com/questions/44268/transmission-causes-internet-to-stop-working-log-off-required-to-make-it-work)

[Edit]
problem solved for me. I lowered the number of connections per torrent and overall both to 60 and I haven't had any dropped connections since.

Hope this helps someone else.

---

### Post by selopo on 2013-01-10
I created this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1098286](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1098286)

Please add your comments. This problem still occurs with 12.10.

---

### Post by overdrank on 2013-01-10
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

