---
title: "Torrenting kills browsing"
date: 2009-06-30
forum: General Help
---

### Post by ICDeath on 2009-06-30
This issue seems to be common on many Linux distros but as a comparatively novice user I experienced it only in Ubuntu cause, well, I used only Ubuntu.

I noticed it tends to appear randomly. I had 6 seedings with a total upload speed of like 300 with about 15-20 connections and I could browse just fine. Later I added 1 download with speed like 30 and seeding speed was about 150-200 of my max 5Mbit down and up and no web pages would open at all. Next there was only 10 connections and total down and up speed was like 50 and I couldn't browse at all too. But that's nonsense - 10 connections and 50Kb/s totally disables other internet...? I was using Deluge and Transmission and both had this ptoblem.

I've never encountered such issue on Windows with Utorrent. Even when it maxed out my connection I still could browse, yes it was slower but I just knew that browsing made my torrent speed a bit lower when opening web pages and at the same time pages took a little bit more to load due to max torrent speeds. But they were in synergy, exchanging speeds when it was needed. In Linux, as I already mentioned, it kills browsing completely, like I got disconnected. 

So far this is the most frustrating and irritating problem I've encountered in Ubuntu and Linux overall. Looking forward to any advice you guys can provide.

---

### Post by hibliss on 2009-06-30
Go to [http://speedtest.net]("http://speedtest.net") and post the results of the speedtest.

You need to stop all of your torrents first, and no streaming video or heavy internet traffic should be happening during the test as it can interfere with the test. 50kBps is a common upload cap from Cable companies. I will explain more after you post the test results.

You are most likely saturating your upstream bandwidth and it is not allowing enough upstream for communication so pages are timing out.

This has nothing to do with Linux and happens in Windows all the time. It is due to incorrect settings in your torrent client.

[http://www.google.com/#hl=en&q=torrent+kills+internet&aq=0&oq=torrent+kills+&aqi=g8&fp=Z0kzoBTid-E]("http://www.google.com/#hl=en&q=torrent+kills+internet&aq=0&oq=torrent+kills+&aqi=g8&fp=Z0kzoBTid-E")

[http://www.google.com/#hl=en&safe=off&q=torrent+kills+browsing&aq=0&oq=torrent+kills+br&aqi=g1&fp=Z0kzoBTid-E]("http://www.google.com/#hl=en&safe=off&q=torrent+kills+browsing&aq=0&oq=torrent+kills+br&aqi=g1&fp=Z0kzoBTid-E")

utorrent has settings in their speedguide where you set your upload speed and it auto adjusts to cap at 80% of available upstream and limits connections for each torrent and globally for all torrent connections based on available upstream bandwidth.

---

### Post by ICDeath on 2009-06-30
My conection is 5Mbit both down and up. 

No, my utorrent global upload limit is 0=unlimited and NOT automatic. And I didn't use any speedguide. My global connections in Utorrent is 400 with maximum number of peers per torrent 100. It is maxing both my download and upload at ~600Kb/s and I can still browse just fine.

With Deluge in Linux no pages would open with 100 global connections and overall torrents speed around 100Kb/s both down and up. Talk about saturating.

---

### Post by hibliss on 2009-06-30
Where is the speedtest?

---

### Post by lavinog on 2009-06-30
Many consumer routers cannot handle more than 50 open connections. If you set your max connections to more than 50 your computer is going to attempt to make that many connections.  Ex: if your max is 250, your torrent program will try and connect to 250 seeders. Even if only 10 start sending you data, your router is still trying to track the other 240 connections until they time out. When they do time out, your torrent program will try and connect again.

It is best to reduce your max to a lower number, try 30, then bump it up as needed.

---

### Post by t4thfavor on 2009-06-30
I use utorrent on windows, and the standard Transmission on Linux, I never have an issue. Check your router to make sure its not getting stressed by holding on to old connections. 
There was a problem at one time with Linksys routers tracking so many connections they would fill up the ram and nearly crash (or crash). Most home routers are not capable of handling even a small amount of regular bittorrent traffic due to memory contraints.

EDIT: 
TOO SLOW AGAIN!

---

### Post by lavinog on 2009-06-30
> **t4thfavor said:**
> There was a problem at one time with Linksys routers tracking so many connections they would fill up the ram and nearly crash (or crash). Most home routers are not capable of handling even a small amount of regular bittorrent traffic due to memory contraints.


Linksys routers also had an issue if you had logging enabled too.

I have come across some updates to some routers that fix some of the torrent issues. You may want to see if there is an update to your router.

---

### Post by t4thfavor on 2009-06-30
I have found an update for Linksys routers, its called Tomato. No more issues with connection tracking. 

[www.polarcloud.net](www.polarcloud.net)

---

### Post by lavinog on 2009-06-30
> **t4thfavor said:**
> I have found an update for Linksys routers, its called Tomato. No more issues with connection tracking. 

[www.polarcloud.net](www.polarcloud.net)

Unfortunately it doesn't work on wrt54g v5+

---

### Post by ICDeath on 2009-06-30
I'm using Linksys WRT54GL v1.1 with Tomato Firmware v1.23.8515 .4 RAF ND (a modification of original Tomato by [http://victek.is-a-geek.com/](http://victek.is-a-geek.com/)). 

I still can't see your reasoning guys. My router can handle w/e the amount of connections with 400 limit in Utorrent but can't handle w/e the amount with 100 limit in Deluge?

I had around 20 active torrents with a lot of peers in Utorrent and no troubles at all. In Deluge already 3 torrents start making troubles.

---

### Post by lavinog on 2009-06-30
> **ICDeath said:**
> I'm using Linksys WRT54GL v1.1 with Tomato Firmware v1.23.8515 .4 RAF ND (a modification of original Tomato by [http://victek.is-a-geek.com/](http://victek.is-a-geek.com/)). 

I still can't see your reasoning guys. My router can handle w/e the amount of connections with 400 limit in Utorrent but can't handle w/e the amount with 100 limit in Deluge?

I had around 20 active torrents with a lot of peers in Utorrent and no troubles at all. In Deluge already 3 torrents start making troubles.

I see your point.
One thing that was found out on [this thread](http://ubuntuforums.org/showthread.php?t=1174741) was that windows doesn't use tcp_windowscaling while ubuntu does. This has caused some sites to slow down to a crawl on ubuntu but load just fine in windows. While this might not be the case normally, could it be possible that the torrent connections are triggering the windowscaling down.

---

### Post by ICDeath on 2009-06-30
> **lavinog said:**
> I see your point.
One thing that was found out on [this thread]("http://ubuntuforums.org/showthread.php?t=1174741") was that windows doesn't use tcp_windowscaling while ubuntu does. This has caused some sites to slow down to a crawl on ubuntu but load just fine in windows. While this might not be the case normally, could it be possible that the torrent connections are triggering the windowscaling down.

Hardly it's the reason. I tried opening dozens of web-sites totally diferent in content and structure. And the case you provided has nothing to do with torrents running or not ;)

---

### Post by Slim Odds on 2009-06-30
Also, make sure that you throttle the upstream data rate for the torrent client so that it doesn't use all of your upstream bandwidth.

Otherwise, your acknowledgments get delayed and will affect browser performance.

---

### Post by hibliss on 2009-06-30
> **ICDeath said:**
> My conection is 5Mbit both down and up. 

No, my utorrent global upload limit is 0=unlimited and NOT automatic. And I didn't use any speedguide. My global connections in Utorrent is 400 with maximum number of peers per torrent 100. It is maxing both my download and upload at ~600Kb/s and I can still browse just fine.


I am running rtorrent/libtorrent with a 20/5 connection and a WRT54GS running Sveasoft Talisman firmware. With the settings I described, I get 550kBps constant upload speeds, 2.5mBps download, and still no issues browsing. I assure you the issue you are having is not with Ubuntu, though I have never tried Deluge.

You do have a very nice router. It is fully capable of handling a lot of connections.

Hard for me to help troubleshoot because I am not sure of how Deluge settings work. Have you tried any other Linux clients? Transmission 1.7x is accepted everywhere I have seen, and rtorrent is accepted everywhere (and is the best Linux client in my humble opinion). ktorrent is another option.

---

### Post by pytheas22 on 2009-07-01
ICDeath: have you tried running utorrent on Ubuntu?  It works fine in wine.  If your issue is application-specific, this would probably fix it.

---

### Post by hibliss on 2009-07-01
> **pytheas22 said:**
> ICDeath: have you tried running utorrent on Ubuntu?  It works fine in wine.  If your issue is application-specific, this would probably fix it.

I don't really understand why people do this over using a native Linux client. You will always get better performance from a native application designed to run on your platform.

---

### Post by moster on 2009-07-01
> **hibliss said:**
> I don't really understand why people do this over using a native Linux client. You will always get better performance from a native application designed to run on your platform.

Because Utorrent is fastest torrent downloader on planet. That is no secret to heavy torrent addicts. In linux world, only vuze (former azuerus) can compete with utorrent. Problem is that Utorrent is athlete and Vuze fat java bast*rd.

Utorrent is completely compatible with wine, developers say it, and if you do not want, Vuze is your last option if you want top speed.

There are many possible causes of your problems, but first, when you are unable to browse, check your upload. But not in your torrent app but in system monitor. It must be lower than you maximum upload. That is most common reason people are not able to surf while downloading. Your torrent prog can say 34 kb/s upload but with many connections at same time that number can be really double.

---

### Post by Slim Odds on 2009-07-01
> **hibliss said:**
> I don't really understand why some people do this over using a native Linux client. You will always get better performance from a native application designed to run on your platform.

I understand that people have a philosophical problem with using a non-native application when there are native ones available that do basically the same thing (I'm actually somewhat like that myself).

However, there is no real performance hit for using WINE. It is NOT an adaption layer. It is an implementation of an API. It seems that people commonly confuse this issue.

I repeat... WINE does NOT add another layer on top of anything. Many applications will run **faster** with WINE than in their native OS.

WINE IS NOT (an) EMULATOR.

---

### Post by hibliss on 2009-07-01
> **moster said:**
> Because Utorrent is fastest torrent downloader on planet. That is no secret to heavy torrent addicts. In linux world, only vuze (former azuerus) can compete with utorrent. Problem is that Utorrent is athlete and Vuze fat java bast*rd.

Utorrent is completely compatible with wine, developers say it, and if you do not want, Vuze is your last option if you want top speed.


This is a very common misconception. utorrent is recommended mostly because it is light on resources, that does not mean it downloads faster. utorrent follows the bittorrent protocol, just like any other torrent client. There is no speed advantage in using utorrent over a native Linux client. Read up on the protocol.

I get the same speeds no matter what client I have ever used, Linux or Windows. I have used utorrent, Azureus (and Vuze), Bittorrent (new and old), Halite, ktorrent, Transmission, and rtorrent. Speeds are dependent on number of peers in the swarm and who you are connecting to, not on your client. Any properly setup client is going to get roughly the same speed in the same swarm, but of course you may connect to different peers if you download the file twice to test, so it is not an exact science.

There is absolutely no benefit in using utorrent in WINE over using a native Linux app uless utorrent is just your personal preference.

I know WINE is not an emulator, but that doesn't make utorrent a Linux native torrent client.

---

### Post by Slim Odds on 2009-07-01
> **hibliss said:**
> I know WINE is not an emulator, but that doesn't make utorrent a Linux native torrent client.

Agreed, but my point was that it doesn't entail any additional overhead or penalty either.

P.S. Last off topic post in this thread for me.... I promise.

---

### Post by pytheas22 on 2009-07-01
> 
I don't really understand why people do this over using a native Linux client. You will always get better performance from a native application designed to run on your platform.

As others have pointed out, you won't necessarily get better performance from a native application.  But that aside, the reason I suggested you try running utorrent in wine is because both Deluge and Transmission give you problems, while you say utorrent works fine for you in Windows.  It may also work better on Ubuntu--perhaps there is something about the way utorrent behaves that's different from Deluge and Transmission and that allows it to work properly on your network.  It's at least worth a try if you want to narrow down the possible sources of your problem, I think.

---

### Post by lavinog on 2009-07-01
Can utorrent handle encrypted connections?

---

### Post by bapoumba on 2009-07-02
Removed 6 off topic posts.

---

### Post by moster on 2009-07-06
If you did not touch advanced utorrent preferences then your limit is 8 connections in same time. Only 8 because windows have limit of 10 if you not have TCP/IP patch. Do not understand wrong this, you can be downloading as 5 torrent at same time but only 8 IP adresses can be look upon at same time.

Now, linux do not have probably any limits. How to find out how many connections are really at use? Any idea anyone?

edit:
I think I got it. Go here.
[http://ubuntuforums.org/showthread.php?t=1174741&page=4]("http://ubuntuforums.org/showthread.php?t=1174741&page=4")

---

### Post by stinger30au on 2009-07-06
> **moster said:**
> Because Utorrent is fastest torrent downloader on planet.

even if there is zero seeds?

many seeds that have high upload speeds are what make downloads run fast

---

### Post by stinger30au on 2009-07-06
> **lavinog said:**
> Can utorrent handle encrypted connections?

just look thru the utorrent options, you will be amazed!

---

### Post by moster on 2009-07-06
> **stinger30au said:**
> even if there is zero seeds?

many seeds that have high upload speeds are what make downloads run fast

No. If you want full speed on those you have to use Transmission. :rolleyes:

edit:
BitTorrent Inc. bought Utorrent. Why? Wilde guess because it is worth something. Go to wikipedia, educate yourself little. It is not just SEEDS.

---

### Post by hibliss on 2009-07-06
> **moster said:**
> No. If you want full speed on those you have to use Transmission. :rolleyes:

edit:
BitTorrent Inc. bought Utorrent. Why? Wilde guess because it is worth something. Go to wikipedia, educate yourself little. It is not just SEEDS.

Please stop posting again and again with no new information and worthless claims of downloading experience. A client that follows the protocol is a client that follows the protocol.

---

### Post by meeples on 2009-07-06
i have this problem in win xp pro.

so its nut just linux, but i just limited my upload to 15kb/s and problem solved, i assume this is because of virgin's TERRIBLE upload speeds.

i swear its like dial up

---

### Post by lavinog on 2009-07-06
> **meeples said:**
> i have this problem in win xp pro.

so its nut just linux, but i just limited my upload to 15kb/s and problem solved, i assume this is because of virgin's TERRIBLE upload speeds.

i swear its like dial up

Network hardware and connections sound to be the cause in your case, but the OP is saying that his problem is not common to windows.

---

### Post by Jormanks on 2009-07-06
I have a problem that, maybe, has nothing to do with all this. Well, to be fair, it's maybe the opposite: can't download anything but the .iso torrents from ubuntu, and this has happened since saturday, I guess.
I wonder why all my torrents can't do anything (no downloads, no uploads for the files I've already finished) from one day to another.
A friend has this very same problem, he thinks it's related to an update this weekend. 
sorry to bother, and to bring this giant piece of "off-topic" to this thread.

---

### Post by lavinog on 2009-07-07
> **Jormanks said:**
> I have a problem that, maybe, has nothing to do with all this. Well, to be fair, it's maybe the opposite: can't download anything but the .iso torrents from ubuntu, and this has happened since saturday, I guess.
I wonder why all my torrents can't do anything (no downloads, no uploads for the files I've already finished) from one day to another.
A friend has this very same problem, he thinks it's related to an update this weekend. 
sorry to bother, and to bring this giant piece of "off-topic" to this thread.

Please start a new thread if you know it is off-topic.

Does your friend use the same internet service?

---

### Post by moster on 2009-07-07
Everybody who has problem with browsing while torrenting should at least try this.

```
gksudo gedit /etc/sysctl.conf
```

then enter this on end

```

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760
```

restart after

This will change TCP/IP packet sizes. I forgot where I found it. Ok.. and reply here if it help you.

---

### Post by lavinog on 2009-07-07
> **moster]
This will change TCP/IP packet sizes. I forgot where I found it. Ok.. and reply here if it help you.
[/quote]
The link I posted in post #11 says the same thing:[http://ubuntuforums.org/showpost.php?p=7495241&postcount=33](http://ubuntuforums.org/showpost.php?p=7495241&postcount=33)

[QUOTE=ICDeath said:**
> Hardly it's the reason. I tried opening dozens of web-sites totally diferent in content and structure. And the case you provided has nothing to do with torrents running or not ;)

So, does it work?

---

