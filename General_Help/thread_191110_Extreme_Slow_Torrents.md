---
title: "Extreme Slow Torrents"
date: 2006-06-07
forum: General Help
---

### Post by b3an on 2006-06-07
I have recently moved over to 100% Ubuntu and loving it, however, I have a single problem: Torrents!

I can't seem to get decent speeds ever, they never go above ~30kb/s. Very rarely they will go to about 80kb/s. When I run windows with utorrent, I always max out my connection to ~230-240kb/s on torrents like openoffce.

I'm using Azureus latest beta (also tried non-beta) with jre 1.5. Tried KTorrent same results. Also tried utorrent with wine but no luck.

My ethernet connection is static ip connected to my netgear router. The port forwarding all seems setup fine.

I've got utorrent running in vmware server with bridged networking and I'm maxing the connection, but that's worse than running azureus with resources :-? 

My other machine is Debian Sarge and that can also max out Azureus, so it seems to be this ubuntu machine.

Any Ideas?

---

### Post by caldevil on 2006-06-07
Is the problem with torrnt files in particular or in general internet connection? Try running some bandwidth tester.

---

### Post by b3an on 2006-06-07
Yeah it seems to be only torrents, http connections I can max out. Tried a speedtest and they are both reporting that I can download at 240kb/s.

---

### Post by Kabal on 2006-06-07
Maybe your provider caps the speed of torrents?

I know some ISP's who do cap torrent and ftp connections.

---

### Post by b3an on 2006-06-07
No I don't think its that because in Windows and vmware server running windows and also my debian machine all have no problems downloading at 240kb/s

](*,)  This is so annoying, I just cannot think what it could be.

---

### Post by caldevil on 2006-06-07
I would say try bittorrent too as it is a very simple program. Also I guess you haven't installed some firewall like firestarter or something?

---

### Post by b3an on 2006-06-07
Tried gnome-btdownload with no luck. No firewall yet not had time.

Thanks for all the help guys.

---

### Post by jISh on 2006-07-16
Way for me to revive a long dead thread.
But seriously, I'm having the EXACT same problem, with port forwarding and all that being setup properly and other machines maxing speeds.

What gives?

---

### Post by DavidFL on 2006-07-16
I can only say that I am running utorrent in Wine and am seeing 300kB/s downloads which is higher than normal in windows for me.  I would suggest going back and checking the basics such as settings in utorrent.  Also if you have some sort of firewall running on Ubuntu look into that as it would be a logical culprit.  Regarding Azureus in Ubuntu, I never had any success with it for some reason, kind of ironic.

---

### Post by mrvw0169 on 2006-07-16
I have the exact smae problem... uTorrent in Windows (VMware) downloads at 600 kB/s consistently... Running gnome-btdownload or azureus barely goes at 1-2 kB/s... I'm not firewalled (NAT OK and DHT: 400,000 or so users)... What's worse is that azureus works for about 5 minutes at a time at 40 kB/s and then all torrents drop to 0 B/s for 30 minutes or so...

I think I'm just going to run uTorrent in wine...

---

### Post by jISh on 2006-07-16
Yea, I'm going to also run uTorrent in WINE. I could do it in my XP VmWare install, but that seems extremly stupid having to boot an entire extra OS to download torrents :P

---

### Post by compres on 2006-09-13
Still no solution? 

I am having the same problem here, just with torrents.  Very bad and probably the deal breaker when it comes to ubuntu on  my laptop.

Exactly the same problem as those guys above.

---

### Post by superzap on 2006-09-13
same here.
Azureus in windows = 250-270kB/s
but with azureus in gnome = 0.4-30kB/s
Same pc, same router.
](*,)

---

### Post by Rocketeer on 2006-09-13
here too.

Newly set up Server (Ubuntu LAMP Install) ... Windows is super fine. Ubuntu not (any client).

---

### Post by HAARP on 2006-09-13
Windoze (official client): Damn fast kb/s
Ubuntu (MLDonkey): Damn slow kb/s

:/

---

### Post by tuxbaby on 2006-09-14
i also was experiencing very slow torrents.
here is what i did:_

Install wine
then get utorrent and use it with wine.
Now go to utorrent preferences, the from there go to Bittorrent Option
Now you should see Protocol Encryption, use the Forced option.

This worked for me very well.
Might help for you too.

cheers
Tux

---

### Post by allix on 2006-09-14
Could this have something to do with [IPv6]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")? I use Azureus and I get great speeds up and down all the time. Usually around 850-1000kb/s.

---

### Post by foss on 2006-09-14
I also experienced something like what have been described above, i found another thread dealing with the problem:
[http://www.ubuntuforums.org/showthread.php?t=188149](http://www.ubuntuforums.org/showthread.php?t=188149)

So what i did was to install sun-java5-jre and configured the chosen java with 
```

sudo update-alternatives --config java

```

Now my download speed is back to normal, ~ 700-800 kb/sec

---

### Post by compres on 2006-09-15
Many thanks for the input.  Have you guys tried any of this and worked out?  I am not home now will try later tonight.

I'll post when I get the results.

---

### Post by compres on 2006-09-17
I have to admit I am no expert linux user but I did not consider myself noob enough for this:  I can't install java.

I am not confortable with the sudo "feature".  Can't access with root, if I use the sudo -i I can change the permision on a file to only find out latter I can still not execute, etc.

Very anoying...

Yes I am reading how to disable it on another thread...

I post my results later.

---

### Post by [Yatta] on 2006-10-23
I'mhaving the same prob where in vmware torrents go max 30kB while in ubuntu or my xp machine i get max... even from another machine where I'm running TorrentFlux i get max. 
For some strange reason torrents in my vmware go max 30kB ???  Was anytone abel to figure this out?

---

### Post by ser1alsn1per on 2006-10-24
open ports in the router i cant remember what ones they are but google it

---

### Post by HAARP on 2006-11-19
I think I may have a solution. Besides forwarding ports 6881-6999 in your router, you need to tell iptables to allow connections to them
In console, do this
```
sudo iptables -I INPUT -p tcp --destination-port 6881:6999 -j ACCEPT

```
followed by a
```
sudo iptables-save > iptables
```
Then move the file iptables into **/etc/sysconfig/**

I'm not sure if this really does the job, but it's worth the try.

---

### Post by MJN on 2006-11-19
Sorry to arrive late to this thread, but to all you guys having slow torrent downloads have you capped your upload speed? You ought to cap it to something below your max theoretical upload in order to allow TCP ACKnowledgements back out...

If you're running uploads uncapped then whilst all the other punters are happily sucking your connection dry you're unable to send out the necessary ACKs to keep your downloads up to speed.

It may be that your Windows Torrent clients are automatically throttling the uploads (perhaps configured as a result of it asking you for your connection speed) whereas your Linux one isn't.

As an example, I have a 4Mbps down, 384kbps up connection. I limit my uploads to 25KBps (=200Mbps, roughly half my theoretical max). You could allow somewhat higher, however I'm also running a web server which I want to allow swift access to (even whilst I'm busy downloading torrents).

Mathew

---

### Post by jayemef on 2006-12-02
I've experienced similar issues. I'm in a college setting, running Edgy while my roommate is running XP. Running similar client configurations, myself using Ktorrent and he using Azureus, he is pulling the latest episodes of House (350 mb) in an hour, while it takes me a week to pull 10% (no exaggeration). On average, I have a down speed of around .1-.3 kB/s, if anything at all. More often, I get the stalled message.

I've tried running uTorrent under wine, and at first was experiencing the exact same symptoms. However, as suggested by a previous poster, I went to Preferences > BitTorrent and set the outgoing encryption to Forced. Download speeds are now about 10kB/s, which is MUCH better than what I've been getting. But compared to my roommate's 60/70, 10 is nothing.

I'd really like to get this figured out...


Edit: I just connected to a fast peer and am pulling at over 100kB/s with no additional configuration changes. Don't know what to make of that, but I'm a happy camper for the time being...

---

### Post by HAARP on 2006-12-02
See my post, I've figured it out

---

### Post by istrebitjel on 2006-12-02
Funny, I had the same experience on my Edgy Eft x64, running the latest 64bit Azureus from sf.net: Dead slow torrents, barely moving.
But then I installed j2re 1.4.2.02-1 via Synaptic and set that java version as the default via 
```
sudo update-alternatives --config java
```
**After restarting Azureus the speed was fine!**
So maybe that is a problem with the default java that's installed. For me that was
```
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)
```

---

### Post by jayemef on 2006-12-02
[quote=HAARP]See my post, I've figured it out[/quote]

Already did -- that wasn't the problem. My problem was definitely not having encryption enabled. Just went into KTorrent, went to Settings > Configure KTorrent > General and checked both Use Protocol Encryption and Allow unencrypted connections, and down speeds are now normal.

---

### Post by aresgoddess on 2006-12-03
dunno if this will help anyone else, but this is what i did, and it seems to work. it's a combination of what people have posted so far.

-Uninstalled gij-4.1 and installed sun-java5-bin and sun-java5-jre with Synaptic
-Configured sun-java with the code in a previous post on this thread
-Put the cap on both download and upload at 100KB/s
-Restart Azureus.

After all that, it works until the school network says that my computer is exhibiting signs of virus activity and shuts down my connection for 15 minutes and recommends that i download Spybot, VirusScan, and Windows Service Packs... =/

---

### Post by DwalerXIII on 2006-12-09
I have the same problem with Azureus and tried teh command 

[I]sudo update-alternatives --config java
[/I]
I shose the java-1.5.0-sun. Now when I start Azureus it closes agian imediately.

here is the result when I do 
*sudo update-alternatives --config java* again.

[I]There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:[/I]

---

### Post by Tekovro on 2006-12-11
yeah im getting slow download with azureus too. in windows everything would be done over night even files that are 5GB. i love ubuntu but the bittorrent speeds just blow.

---

### Post by MJN on 2006-12-11
Have you tried throttling your upload speed as I suggested? If so, what to? (and what is your theoretical max?)
 
Mathew

---

### Post by xabbott on 2006-12-11
You can run utorrent in ubuntu just fine. I also find it less demanding on resources than native gui BT clients.

For help on how to set it up check out these two threads.
[http://www.ubuntuforums.org/showthread.php?t=191161](http://www.ubuntuforums.org/showthread.php?t=191161)
[http://www.ubuntuforums.org/showpost.php?p=1421017&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1421017&postcount=11)

---

### Post by MJN on 2006-12-11
xabbot, have you tried KTorrent? I find it practically a non-drainer even on my PIII/1GHz downloading at a maxed-out 4Mb/s.
 
Mathew

---

### Post by xabbott on 2006-12-11
> **MJN said:**
> xabbot, have you tried KTorrent? I find it practically a non-drainer even on my PIII/1GHz downloading at a maxed-out 4Mb/s.
 
Mathew

Since I use Gnome I generally don't use KDE apps. I have used it in the past and it reminded me a lot of uTorrent. If I were using KDE I would probably be running it.

I tried Deluge and configured it properly. Aside from slow downloads it took forever to even start the downloading process. So that is why I've stuck with uTorrent.

---

### Post by sha_man on 2007-01-21
ok, i have the same problem too, slow downloads with ubuntu, fast one with windows; same connection, same program (azureus), same settings (also for upload). With http, i can max out my connection on both...

```
sudo update-alternatives --config java
```
gives me:
```

There is only 1 program which provides java
(/usr/lib/jvm/java-1.5.0-sun/jre/bin/java). Nothing to configure.
```
(as i removed the others :) )

I think the problem may be with the firewall, or maybe ipv6 (though i disabled and reenabled it with no difference....), or a global connection limit?
Azureus theoretically only needs one port forwarding, so what else can it be?

It's getting really strange now :confused:

---

### Post by istrebitjel on 2007-01-21
I'm running azureus on this java jre version
*/usr/lib/jvm/java-1.5.0-sun/jre/bin/java*
and it's lightning fast (my harddisk almost couldn't keep up, when I downloaded the latest linux iso).... 
try following all the good advice in this thread regarding port and firewall config.

---

### Post by sha_man on 2007-01-22
ok, **problem solved** ! :D :D :D 

the answer was this: My ISP was *traffic shaping*! (throttling bittorrent!)
fortunately, this helped me: [http://www.azureuswiki.com/index.php/Avoid_traffic_shaping](http://www.azureuswiki.com/index.php/Avoid_traffic_shaping)

strangely, i enabled it one the windows machine (even though i can't remember when...)

btw: it was good it didn't figured this out first, for i learned a lot about iptables/firewalling/netoworking :) 

anyway i'm gonna change this crappy isp, even if the problem is fixed...

---

### Post by Maverickprowls on 2007-05-22
I found that my torrents sped up massively once I installed Sun's Java6 JRE.  Prior to this I was using gji, the gnu java environment, and whilst I'm not saying that this caused the slow or failed connections (I don't know enough to impugn the software.), Azureus definitely downloads a hell of a lot faster now.

I fetched everything with the following:

```
sudo aptitude install sun-java6-jre sun-java6-jdb sun-java6-source sun-java6-jdk sun-java6-plugin sun-java6-bin sun-java6-fonts sun-java6-javadb
```

I then forced open a couple of ports in iptables using:

```
iptables -I INPUT -p tcp --dport <azureus port> -j ACCEPT
iptables -I INPUT -p udp --dport <azureus port> -j ACCEPT

```

And finally I discovered that with the new JRE installed, Azureus would load and immediately crash, so I followed the advice given elsewhere in this forum (sorry for lack of accreditation)

```
rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*
```

I hope all that helps someone!  Thanks to the people who helped me out.

---

### Post by Maverickprowls on 2007-05-22
Addendum:

I suspect (though I do not know) that the iptables fix is unnecessary, and that simply installing the Java6 JRE fixed Azureus for me, as Azureus' behaviour was the same before and after I did the iptables fix (which was the first fix I tried). 

Just a note for the security-conscious among you.

---

### Post by hadn on 2007-11-04
There is a couple of hints for the low download rate problem in Azureus/Ubuntu:

1. Make sure you are using Java JRE or Java JDK instead of GCJ/GIJ. You can install Java JRE with Automatix. Also, check if you are using JRE, with the following shell command:

 sudo update-alternatives --config java

2. Disable the ipv6 protocol as described in [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4:](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4:)

 a) Open a terminal and type:
      gksudo gedit /etc/modprobe.d/blacklist
 b) Add this line:
      blacklist ipv6 
 c) Save the file and restart your computer

3. Set Azureus' parameters for working with your correct internet connection:

 a) Stop Azureus
 b) Remove Azureus' configuration directory - in a terminal, type: 
     cd ~
     \rm -rf .azureus/
 c) Run Azureus
 d) In the startup window, choose your internet connection type and speed

With these changes, I was able to improve Azureus' download rate by 2X to 3X. Nevertheless, uTorrent + Wine is giving me the highest (practically full) download rate. uTorrent website is [http://www.utorrent.com/](http://www.utorrent.com/)

Good luck
Hugo

---

