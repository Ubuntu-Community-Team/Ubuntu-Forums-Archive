---
title: "I'm about done with torrents all together"
date: 2010-05-04
forum: General Help
---

### Post by 98cwitr on 2010-05-04
Ping to google while torrent app is open:

> brett@brett-desktop:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.67.147) 56(84) bytes of data.
64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=1 ttl=53 time=6011 ms
64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=2 ttl=53 time=5823 ms
64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=3 ttl=53 time=5553 ms
64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=4 ttl=53 time=5763 ms
64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=5 ttl=53 time=5925 ms
64 bytes from 74.125.67.147: icmp_seq=6 ttl=53 time=5720 ms
64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=7 ttl=53 time=4643 ms
^C64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=8 ttl=53 time=4799 ms
64 bytes from 74.125.67.147: icmp_seq=9 ttl=53 time=4857 ms
64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=10 ttl=53 time=5015 ms
64 bytes from gw-in-f147.1e100.net (74.125.67.147): icmp_seq=11 ttl=53 time=5593 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 52560ms
rtt min/avg/max/mdev = 4643.657/**5427.933**/6011.240/475.928 ms, pipe 6
brett@brett-desktop:~$ 


ping to google right after closing torrent app.
> 
...
64 bytes from yx-in-f99.1e100.net (74.125.45.99): icmp_seq=69 ttl=53 time=28.7 ms
64 bytes from yx-in-f99.1e100.net (74.125.45.99): icmp_seq=70 ttl=53 time=26.4 ms
64 bytes from yx-in-f99.1e100.net (74.125.45.99): icmp_seq=71 ttl=53 time=29.5 ms
64 bytes from yx-in-f99.1e100.net (74.125.45.99): icmp_seq=72 ttl=53 time=28.4 ms
64 bytes from yx-in-f99.1e100.net (74.125.45.99): icmp_seq=73 ttl=53 time=29.1 ms
^C
--- [www.l.google.com](www.l.google.com) ping statistics ---
73 packets transmitted, 73 received, 0% packet loss, time 72098ms
rtt min/avg/max/mdev = 26.400/**30.655**/41.577/3.496 ms
brett@brett-desktop:~$ ^C


IP match from 1st run:
> 
...
64 bytes from 74.125.67.147: icmp_seq=19 ttl=53 time=22.2 ms
64 bytes from 74.125.67.147: icmp_seq=20 ttl=53 time=24.2 ms
^C
--- 74.125.67.147 ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 19027ms
rtt min/avg/max/mdev = 21.897/**23.537**/26.963/1.231 ms
brett@brett-desktop:~$ 


w...t...f is Vuze/Tranmission/etc doing to my f**king connection.

Yes, the ports are open
Yes, UPnP is enabled and working on the router
Yes, I've limited connections and upload bandwidth

---

### Post by v1ad on 2010-05-04
well torrents take up bandwidth. what did you expect?

---

### Post by 98cwitr on 2010-05-04
> **v1ad said:**
> well torrents take up bandwidth. what did you expect?
Its a ping...a 64 byte ping...

I've got 30Mbps down, downloading a file @ 10kbps and my bandwidth drops to that? Cop-out dude try again.

---

### Post by gameplace123 on 2010-05-04
I think he thinks that torrents are magic... 
p.s. they kinda are. Stop downloading so much porn

---

### Post by v1ad on 2010-05-04
its probably your isp. a lot of isp's detect torrents and reduce their bandwidth.
Comcast?

---

### Post by 98cwitr on 2010-05-04
> **gameplace123 said:**
> I think he thinks that torrents are magic... 
p.s. they kinda are. Stop downloading so much porn

it's a single file...@ 10k down. :roll: If it's going to put traffic through a certain TCP/UDP port number...wtf is it messing with ICMP?

---

### Post by DomesDKG on 2010-05-04
I've had really bad luck with vuse on Ubuntu, though transmission has worked wonders. what are you using?

---

### Post by techunit on 2010-05-04
> **gameplace123 said:**
> I think he thinks that torrents are magic... 
p.s. they kinda are. Stop downloading so much porn


:lolflag:

What do you get 30Mbps do you mean you connection speed or your plan speed...

What I mean: I have  a 7Megabytes (5 Down 2 Up) per second cable line. I get 54mbps because that is the speed of a Wireless G connection. So in a torrent I get around 500 Kilobytes per second.

Hope this helps

---

### Post by moviemaniac on 2010-05-04
I noticed this too lately when downloading a movie (CC licensed if you should ask) - the download and upload speeds with torrent were very slow (way below the limit of my line) as nearly no seeders were available yet ping times were way up and general browsing a PITA. When I closed transmission ping times and general browsing worked flawlessly again. I don't use torrents much so I don't really care but it got me scratching my head too...

---

### Post by 98cwitr on 2010-05-04
^^^good way to put it...same thing right here. :?

> **techunit said:**
> :lolflag:

What do you get 30Mbps do you mean you connection speed or your plan speed...

What I mean: I have  a 7Megabytes (5 Down 2 Up) per second cable line. I get 54mbps because that is the speed of a Wireless G connection. So in a torrent I get around 500 Kilobytes per second.

Hope this helps

omfg...im almost insulted by your post.... My WAN connection is 30Mbps down...my LAN is 100Mbps duplex, which is completely irrelevant btw. Thanks for your input.

[img]http://img.photobucket.com/albums/v673/98cwitr/bandwidth.jpg?t=1273010007[/img]

---

### Post by v1ad on 2010-05-04
[http://torrentfreak.com/comcast-throttles-bittorrent-traffic-seeding-impossible/](http://torrentfreak.com/comcast-throttles-bittorrent-traffic-seeding-impossible/)

---

### Post by jerome1232 on 2010-05-04
Also some routers start getting angry when the torrent uses up all the sessions.

But what they said torrents are design to hog bandwidth, my whole network drops to a crawl if I'm torrenting.

---

### Post by v1ad on 2010-05-04
my isp is nice. even though i have 10mbps nothing is bottlenecked. download files at 1.2 mega bytes. my family i had a lot of experience with other isp's blocking me.

30mbps = megabits per sec. (about 3.4 megabytes a sec)

---

### Post by techunit on 2010-05-04
Ok I found the test you did any my results are... I found that it was inaccurate not bad though. I did a different speed test and and it probed much more accurate.

Uptime based on your test my download speed was around 4 mbps

---

### Post by PhilGil on 2010-05-04
An interesting theory why torrenting causes high latency (slow ping times):
[http://www.formortals.com/?p=57](http://www.formortals.com/?p=57)

---

### Post by 98cwitr on 2010-05-04
router's good...jury on ISP is still out. I "heard" TWC throttles but cannot confirm or deny that claim.

---

### Post by 98cwitr on 2010-05-05
techunit, that test is located in North Carolina...it might not be as accurate for you depending on your location.

any further ideas?

---

### Post by 98cwitr on 2010-05-05
bump

---

### Post by psusi on 2010-05-05
You said you limited your upload speed?  How low?  Looks like your connection can only push about 46 KB/s so if you are trying to upload more than around 40 you're going to max it out and your latency is going to go up.

---

### Post by ankspo71 on 2010-05-05
This problem always effected my web surfing too, even with a slow torrent download rate and low number of connections. 

What I did to help this was run transmission with a higher nice value (a lower priority). I can run transmission with nice values of 3 to 5 without difficulty, and be able to use the internet at normal speeds at the same time.

More info on nice values.
[http://manpages.ubuntu.com/manpages/hardy/man2/nice.2.html](http://manpages.ubuntu.com/manpages/hardy/man2/nice.2.html)

Example Usage:
**nice -n 3 transmission**
Starts transmission with a nice value of 3

**nice -n 3 transmission -m**
Same as above but starts transmission minimized to notification-area.

Hope this helps, it's what I did in Karmic.

---

### Post by ankspo71 on 2010-05-05
> **98cwitr said:**
> router's good...jury on ISP is still out. I "heard" TWC throttles but cannot confirm or deny that claim.

Does TWC = Time Warner Cable?  I have them with Roadrunner internet, and my seeding rate averages about 45-75kb/s. My regular Internet upload rate is 768kb/s, and my download rate was said to be up to 30mb/s.

---

### Post by QIII on 2010-05-05
Enough with the insults, folks.  The OP has a problem we need to help him fix.

98cwitr, ankspo71 may be on the right track.  Hope that helps.

If it doesn't, you may be able to check to see whether it is your torrent client misbehaving in Ubuntu or throttling by your ISP by borrowing a Windows machine (I sense you may not have one?) or using another distro and attempting to torrent something with another OS.  If you do have a Windows machine or a dual boot with Windows or another distro, could you check that out?  That might let the jury make a decision on your ISP.

If you get good results in Windows or another distro, then we need to dig further in Ubuntu.

(PS:  Sometimes diagnosis is best served by methodically finding out what is NOT the problem rather than chasing after many things that COULD be the problem.)

---

### Post by slynke on 2010-05-05
Are you using DHT with your Vuze or Transmission? If yes try disabling DHT and try the ping test again. DHT has a tendancy to try to use the maximum available ports set aside by your router for active IP connections which will in turn basically kill your connection regardless of how fast your up and down speeds are.

---

### Post by peepingtom on 2010-05-05
Have you tried reducing the number of connections your bittorent client makes, and possibly the half-open connections too?

edit: yup

Try connecting your cable modem directly to your computer to see if the issue is with your router.

Does this happen when using Windows?

---

### Post by Vaphell on 2010-05-05
my question is about upload speed limit - at what value it is now? 368kbps is low (46kB/s) given the very high download speed measured in tens of megabits per second. My computer lags even at 50% of total upload.
My guess is that torrents crowd out everything else from upload bandwidth and without upload there is no download - your computer has to ask for content first to get it and that ain't easy when request packets time out because there is no room for them in the outbound traffic.

check if there are known issues with your router, many routers are not powerful enough to support heavy torrent traffic, to create and destroy connections all the time due to low memory and cpu power.

---

### Post by 98cwitr on 2010-05-06
limiting the upload to are 30k, and turned off encrytion and cleared up a good bit. I guess it's good to set it to 10% of your upload max...also changed the Max upload per torrent from 10 to 5. Just ran a speedtest with Vuze open and got 24M down. No, dont use DHT.

Thanks for the support, guys (esp. QIII)

peepingtom, I dont have a windows machine to even test on...just speaking from when I did :D

---

### Post by psusi on 2010-05-07
10% is a bit extreme, but yes, if you try to use more than 80-90% then packets are going to have to wait in the queue so your latency will go up.

---

### Post by cascade9 on 2010-05-07
> **98cwitr said:**
> limiting the upload to are 30k, and turned off encrytion and cleared up a good bit. I guess it's good to set it to 10% of your upload max...also changed the Max upload per torrent from 10 to 5. Just ran a speedtest with Vuze open and got 24M down. No, dont use DHT.

I'm might well be wrong...but isn't it normal for ISPs, etc to list speeds in bits, not bytes? 

368kbit = 46kbyte. So limiting to 30k would be about 65% of your bandwidth. 

Like Vaphell, I've found that if you are running much more than 50% of your total upload bandwidth using torrents (or any other P2P) it really impacts on download, ping, etc.  

I've also found that Vuse is pretty awful...that might just be me ;)

---

### Post by sylvester_0 on 2010-05-07
Your connection's upload speed is really disproportionate to your download speed. The lowest upload speed I've seen with cable is 512k while the norm is 768k. With 30 down I'd expect to get 1.5/2 up. My connection is 50down/5up but we're spoiled here :)

Limiting your upload speed is the way to go. I'd go with about 10K upload max as there's lots of other upload traffic generated when using torrents (ACKs and traffic used negotiating with other peers etc). If you're using a hacked router firmware like tomato on a WRT54g take a look at the bandwidth graph. Your 10k/s upload limit will in reality use more than 10k/s because of overhead.

EDIT: I wouldn't disable encryption as it shouldn't be affecting your situation and it may end up in you not connecting to many possible peers. Some people (myself included) only use encryption.

---

### Post by 98cwitr on 2010-05-07
> **cascade9 said:**
> I'm might well be wrong...but isn't it normal for ISPs, etc to list speeds in bits, not bytes? 

368kbit = 46kbyte. So limiting to 30k would be about 65% of your bandwidth. 

Like Vaphell, I've found that if you are running much more than 50% of your total upload bandwidth using torrents (or any other P2P) it really impacts on download, ping, etc.  

I've also found that Vuse is pretty awful...that might just be me ;)

Wait...Vuze uses byte measurements and not bits (according to their wiki it looks to be this case)? Damn...no wonder. That's pretty dumb. I know the difference, but I thought it was a standard almost to list any network bandwidth in an application or otherwise in bits ONLY!

---

### Post by cascade9 on 2010-05-08
> **98cwitr said:**
> Wait...Vuze uses byte measurements and not bits (according to their wiki it looks to be this case)? Damn...no wonder. That's pretty dumb. I know the difference, but I thought it was a standard almost to list any network bandwidth in an application or otherwise in bits ONLY!

I havent seen any torrent client that does measure in bits. 

I agree, its dumb in some ways, but that is what happens when ISP want to sell the biggest number possible, and bits are the 'industry standard' and software almost always uses bytes.

I'd rather see the ISPs move to a standard byte measurement, rather than some parts of the industry sodding around with KiB (kibibyte, 1000 bytes) and kB (kilobyte, 1024 bytes). That is even more stupid than bits from ISPs and bytes from software (and its going to make a whole new stupid things happen sooner or later) I know, I'm not going to get my wish. :(

---

### Post by psusi on 2010-05-09
Avoiding the idiocy of kilobytes vs kilobytes ( I refuse to use the other word as it is retarded ) that the hard drive industry marketing departments created is one of the GOOD things about the telecom industry always measuring in bits.  There is no ambiguity.

---

### Post by -humanaut- on 2010-05-09
Deluge solves all torrent problems. for me atleast.

---

