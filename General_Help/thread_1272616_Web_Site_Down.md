---
title: "Web Site Down?"
date: 2009-09-22
forum: General Help
---

### Post by dave r on 2009-09-22
For the last couple of days I have been trying to access the Ubuntu software website, [www.getdeb.net](www.getdeb.net)., without success, it spends ages trying to load then gives me a network timed out error message. can any tell me if they have a problem at the moment.

---

### Post by Mighty_Joe on 2009-09-22
[http://downforeveryoneorjustme.com/]("http://downforeveryoneorjustme.com/")

---

### Post by dave r on 2009-09-22
> **Mighty_Joe said:**
> [http://downforeveryoneorjustme.com/]("http://downforeveryoneorjustme.com/")

Thanks Mighty_Joe, I haven't come accross that one before, it looks its me not the website so it looks like I have a problem to solve.

---

### Post by nikhilbhardwaj on 2009-09-22
thanks 
i didn't know about that either
pretty cool

---

### Post by xeriouxi on 2009-09-22
I haven't been able to access GetDeb (or PlayDeb, which I assume runs on the same server?) for a good few days, either... :(

---

### Post by Genefreak on 2009-09-23
That website [http://downforeveryoneorjustme.com/](http://downforeveryoneorjustme.com/) doesn't appear to work, Several people have tried getdeb and it's not working, but that site says that it's me! I pinged getdeb with no response from 3 different computers on 2 sites with no avail.

Probably need to get back to the suppositories - er I mean repositories.

Thanks.

Steve.

---

### Post by barrieluv on 2009-09-23
Same problem here.  downforeveryoneorjustme.com claims it's just me, but getdeb's been down for about week now.  
I did, however, manage to get what I wanted (Tintii) from [here](http://getdeb.masio.com.mx/jaunty/).
Change jaunty to hardy or intrepid depending on your requirements.

---

### Post by Genefreak on 2009-09-23
That's fantastic. Thanks. Got what I wanted too. Checking out the Flock Browser. Wonder what's up with Getdeb though.

---

### Post by P4man on 2009-09-23
Well, the right answer is "it is just you (and some others)" :)  but its not getdeb.net, as it works fine for me (and a lot of others). The site is up, thats for sure.

perhaps you can try a tracert or see if you can access it through IP:
[http://94.126.144.44](http://94.126.144.44) (edit scratch that, that just gives "it works!" for me too)

in any case, its probably a DNS or routing problem with your provider(s) ? If accessing through IP works, perhaps change DNS servers to opendns:
[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by barrieluv on 2009-09-23
Got there through [http://www.proxybrowsing.com/](http://www.proxybrowsing.com/)

---

### Post by 3rdalbum on 2009-09-23
I was able to get to [www.getdeb.net](www.getdeb.net)...

---

### Post by barrieluv on 2009-09-23
Silly thing is, I've just logged on via my brother's network and it's fine.  So maybe the site's being blocked by my provider, O2.  I had no luck with the IP address given earlier.

---

### Post by xeriouxi on 2009-09-23
> **barrieluv said:**
> Silly thing is, I've just logged on via my brother's network and it's fine.  So maybe the site's being blocked by my provider, O2.  I had no luck with the IP address given earlier.

My provider is also O2. I tried the site  in work today (which uses BT) and it worked just fine... :(

Oh... and I'm using OpenDNS, too...

---

### Post by t0p on 2009-09-23
> **Genefreak said:**
> That website [http://downforeveryoneorjustme.com/](http://downforeveryoneorjustme.com/) doesn't appear to work, Several people have tried getdeb and it's not working, but that site says that it's me! I pinged getdeb with no response from 3 different computers on 2 sites with no avail.


Don't libel [downforeveryoneorjustme.com]("http://downforeveryoneorjustme.com")!  It's working just fine - [www.getdeb.net](www.getdeb.net) *is* up, it *is* just you (and several others).

Those people who can't reach [www.getdeb.net](www.getdeb.net) should all post some info here about themselves - geographic location, internet service provider, maybe some other stuff - so then you may be able to deduce what's causing the problem.  Also, run 

```
traceroute getdeb.net
```

and you'll get an idea of where the "blockage" is.  If everyone experiencing this problem runs the traceroute, you'll see if it's the same problem affecting you all.

[downforeveryoneorjustme.com]("http://downforeveryoneorjustme.com") is an extremely useful internetworking tool.  Just as long as [downforeveryoneorjustme.com]("http://downforeveryoneorjustme.com") isn't down!  But of course you can always check if it's up by making a request at [downforeveryoneorjustme.com]("http://downforeveryoneorjustme.com")!  :p__

---

### Post by barrieluv on 2009-09-23
Okay, I'm in the UK, service provider O2.  I cannot connect via my friend's O2 connection either but I can via my brother's BT connection.
Output of traceroute:
```
barrieluv@Mint ~ $ traceroute getdeb.net
traceroute to getdeb.net (94.126.144.44), 30 hops max, 60 byte packets
 1  O2WirelessBox.lan (192.168.1.254)  15.297 ms  12.605 ms  10.848 ms
 2  78-86-32-1.zone2.bethere.co.uk (78.86.32.1)  33.068 ms  33.264 ms  35.068 ms
 3  * * *
 4  10.1.2.157 (10.1.2.157)  51.854 ms  54.786 ms  54.962 ms
 5  197.ge-1-3-2.mpr1.lhr2.uk.above.net (213.161.78.221)  55.114 ms  57.385 ms  57.575 ms
 6  217.243.218.145 (217.243.218.145)  163.613 ms  154.866 ms  154.820 ms
 7  lis-e1-i.LIS.PT.NET.DTAG.DE (62.156.131.129)  82.093 ms  81.068 ms  83.205 ms
 8  217.243.216.90 (217.243.216.90)  61.998 ms  64.303 ms  69.202 ms
 9  ge000-1000M.er2.Lisbon.as25137.net (81.92.201.61)  101.951 ms  102.122 ms  104.015 ms
10  83.240.236.174 (83.240.236.174)  86.923 ms  70.247 ms  66.113 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
barrieluv@Mint ~ $
```

I anyone can make any sense of this, I'd be grateful for a brief explanation. :)

---

### Post by xeriouxi on 2009-09-25
I've just emailed O2 about this issue. I'll let everyone know when I get a response! :D

---

### Post by dave r on 2009-09-25
Yes I am with o2 as well, I am located in Coventry England. I have found that getdeb is accessable now, after 6 days. I also have E-Mailed o2 about this and am waiting for a reply. I suspect that o2 will turn out to be the villain in this. Thanks for all the replies lads looks like this one is sorted, apart for o2's input, if we get any.

---

### Post by dave r on 2009-09-25
Output of Traceroute
traceroute to getdeb.net (94.126.144.44), 30 hops max, 60 byte packets
 1  dsldevice.lan (192.168.1.254)  15.776 ms  15.311 ms  14.884 ms
 2  * * *
 3  * * *
 4  * * *
 5  london1-cr1-f50.cprm.net (195.66.224.91)  106.619 ms  107.801 ms  108.484 ms
 6  lis1-cr1-gi-3-0-0.cprm.net (195.8.0.209)  63.466 ms  49.501 ms  49.890 ms
 7  lis1-br1-gi-3-0-0.cprm.net (195.8.0.210)  51.361 ms  53.590 ms  53.981 ms
 8  ptprime5.cprm.net (195.8.10.110)  49.839 ms  47.940 ms  48.288 ms
 9  BC-PCS1-0-1-5200033.ptprime.net (62.48.132.94)  48.955 ms  49.615 ms  47.127 ms
10  62.48.133.121 (62.48.133.121)  58.445 ms  59.051 ms  59.721 ms
11  83.240.236.174 (83.240.236.174)  55.327 ms  55.258 ms  55.495 ms
12  94.126.144.44 (94.126.144.44)  58.534 ms  58.587 ms  59.405 ms
 
I haven't a clue what it all means either.

---

### Post by pcjunkie on 2009-09-25
Working here. Must be an ISP issue.
And since when was England "filtering" websites? (takes off tin foil hat - puts on sunglasses)

---

### Post by xeriouxi on 2009-09-25
Just to let you know that I've just tried the site and it seems to be working fine now! :D

---

### Post by dave r on 2009-09-25
> **pcjunkie said:**
> Working here. Must be an ISP issue.
**And since when was England "filtering" websites**? (takes off tin foil hat - puts on sunglasses)

That's a good question! I am hoping it will turn out to be a fault or an upgrade that didn't work as it should. I know some filtering goes on, I don't see as much junk as I used to, but I am hoping its not getting to the stage that legitimate web sites start getting blocked

---

### Post by dave r on 2009-09-26
This is the reply I got from o2

Hi Dave


Thanks for emailing us about your connection.

Sorry to hear about the problems you've been having.

It could be that the website in question has black-listed the IP address we've assigned to you.

If you know how, you could try accessing the site via an anonymous proxy. This means the page is effectively displayed via a third party, so your IP address wouldn't be used. If the page does come up via the proxy, this would suggest that your IP has been blocked.

If you need any help trying this, you could contact us via Live Chat. Just open the Broadband Assistant and go to Help then Chat Online.

If the IP seems to have been black-listed, we'd recommend contacting the site directly with your IP address. They'll be able to remove your IP from the black-list.


It seems that they are blaming GetDeb.

---

### Post by FunkyRes on 2009-09-26
> **Genefreak said:**
> That website [http://downforeveryoneorjustme.com/](http://downforeveryoneorjustme.com/) doesn't appear to work, Several people have tried getdeb and it's not working, but that site says that it's me!

That can happen if the problem is a DNS change that hasn't yet been reflected in your ISP's nameserver.

Some ISP's cache names longer than they should, you can solve that by installing a caching nameserver on your local host.

Not tried it myself on Ubuntu (only rhel/fedora) but these ubuntu specific instructions look right:

[http://www.zaphu.com/2007/09/10/ubuntu-dns-server-guide-bind-caching-name-server-setup/](http://www.zaphu.com/2007/09/10/ubuntu-dns-server-guide-bind-caching-name-server-setup/)

If you have a lan, you only need to set it up on one box, then all your boxes can use that one box as their nameserver instead of your ISP nameserver (just make sure that one box has static IP on your local network).

---

### Post by Shazaam on 2009-09-26
No need to install traceroute. Use mtr-tiny (installed by default) instead...
```
mtr getdeb.net
```
man mtr for options. You will have to ctrl+c to stop it running.

---

### Post by barrieluv on 2009-09-27
Working for me now, too. :)
I must find out what the output of traceroute means, though... this may take some time...

---

### Post by t0p on 2009-09-27
> **barrieluv said:**
> Working for me now, too. :)
I must find out what the output of traceroute means, though... this may take some time...

```
man traceroute
```

---

### Post by xeriouxi on 2009-09-29
Well that's cruddy... it's not working again! Is it working for everyone else who had the problem with it before? :(

---

### Post by dave r on 2009-10-01
:confused: Yep its down again for me

Trace Route


Hop	Hostname	IP	Time 1	Time 2
1	davesmagicbox2.lan	192.168.1.64	0.178ms	
1	dsldevice.lan	192.168.1.254	16.867ms	
1	dsldevice.lan	192.168.1.254	98.092ms	
2	no	reply	*	
3	no	reply	*	
4	no	reply	*	
5	79.141.38.121.available.above.net	79.141.38.121	31.488ms	
6	linx1.teleglobe.net	195.66.224.51	42.152ms	
7	195.219.185.1	195.219.185.1	59.947ms	
8	if-0-0-0.core2.WV6-Madrid.as6453.net	195.219.195.30	123.983ms	
9	if-6-0-0.core1.PV9-Lisbon.as6453.net	195.219.112.2	63.601ms	
10	ge000-1000M.er2.Lisbon.as25137.net	81.92.201.61	80.809ms	
11	ge000-1000M.er2.Lisbon.as25137.net	81.92.201.61	78.517ms	
12	83.240.236.174	83.240.236.174	72.332ms	
13	no	reply	*	
14	no	reply	*	
15	no	reply	*	
16	no	reply	*	
17	no	reply	*	
18	no	reply	*	
19	no	reply	*	
20	no	reply	*	
21	no	reply	*	
22	no	reply	*	
23	no	reply	*	
24	no	reply	*	
25	no	reply	*	
26	no	reply	*	
27	no	reply	*	
28	no	reply	*	
29	no	reply	*	
30	no	reply	*	
31	no	reply	*

---

### Post by UltraAnders on 2009-10-15
Sorry to resurrect and oldish thread, did this ever get this resolved? I've been having problems getting on getdeb.net for a few of weeks now, admittedly I've not been trying daily. My broadband is with Be, who are part of ... o2.

---

### Post by UltraAnders on 2009-10-22
... anybody? It's a really useful resource to be without :( Traceroute in case it helps anyone:
```
traceroute to www.getdeb.net (94.126.144.44), 30 hops max, 60 byte packets
 1  BeBox.config (192.168.1.254)  51.206 ms  50.169 ms  48.905 ms
 2  * * *
 3  10.1.3.50 (10.1.3.50)  31.221 ms  32.191 ms  33.545 ms
 4  197.ge-1-3-2.mpr1.lhr2.uk.above.net (213.161.78.221)  34.903 ms  35.886 ms  35.871 ms
 5  linx1.teleglobe.net (195.66.224.51)  36.854 ms  36.839 ms  38.447 ms
 6  if-1-0-0-52.core4.LDN-London.as6453.net (80.231.76.1)  38.433 ms  31.918 ms  32.222 ms
 7  if-2-0-0-1626.core2.wv6-madrid.as6453.net (80.231.76.30)  58.233 ms  58.088 ms  57.835 ms
 8  if-6-0-0.core1.PV9-Lisbon.as6453.net (195.219.112.2)  63.185 ms  63.332 ms  64.187 ms
 9  ix-3-1.core1.PV9-Lisbon.as6453.net (195.219.187.50)  64.585 ms  65.565 ms  59.577 ms
10  xe11-10GE.xmr2.Lisbon.as25137.net (81.92.201.11)  72.474 ms  72.556 ms  72.314 ms
11  83.240.236.174 (83.240.236.174)  66.044 ms  64.548 ms  64.968 ms
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

---

### Post by xeriouxi on 2009-10-25
I've recently moved out from my parents house (which has O2 Broadband) and we had Sky Broadband here for a while and we've recently switched to Be Broadband... and, just like with O2, the site isn't accessible. This is getting quite annoying! =(

---

### Post by DeMus on 2009-10-25
> **dave r said:**
> For the last couple of days I have been trying to access the Ubuntu software website, [www.getdeb.net](www.getdeb.net)., without success, it spends ages trying to load then gives me a network timed out error message. can any tell me if they have a problem at the moment.

Works fine from my place. Sorry.

---

### Post by renkinjutsu on 2009-10-25
> **DeMus said:**
> Works fine from my place. Sorry.

Problem was reported a month ago :confused:

---

### Post by JedMeister on 2009-10-27
I have sent an email (with my traceroute & a link to this topic) to both the owner of the site and the owner of the server where the requests are getting lost. The owner of playdeb.net & godeb.net has already responded:
> we had some  reports of lack of network connectivity to our site, I am sending your info to our network admin.

ThanksHere's hoping for a speedy fix! In the meantime [www.proxybrowsing.com](www.proxybrowsing.com) works a treat!

---

### Post by Uncle Spellbinder on 2009-10-27
Having visited getdeb.com for several times a week for a very long time (over a year), I've not had any troubles at all. The site always loads immediately.

---

### Post by EnlistedSquire on 2009-11-13
+1 for not being able to access getdeb.net here too. I'm also on an O2 connection.

The site did go down for a while earlier this week (I think because it was featured on lifehacker :) ) but now I can get to it fine from work and through a web proxy, just not directly from home.

I had a similar problem earlier this year accessing O2's own site. I found one other guy on the web with the same problem. Emailing O2 got nowhere ("please phone our tech support to go through some troubleshooting steps" - when I knew it wasn't my connection), and one day it just started working again.

---

### Post by scouser73 on 2009-11-13
Try [[COLOR="Red"]**Down For Everyone Or Just Me?**[/COLOR]]("http://downforeveryoneorjustme.com/") to check if a website is down.

I've just checked GetDeb and it's up and running.

---

### Post by EnlistedSquire on 2009-11-13
@Scouser73, if you read my post you will see I already know the site is working.

---

### Post by philliptweedie on 2009-11-14
I'm a Be/02 customer in the UK. I raised a support ticket about the website and got this response :

"Thank you for your patience. We have investigated the issue further and it seems your IP range has been blocked by the server you are having issues with. Please check with them to unlock this range."

So if someone could get in touch with the guys running the site and let them know maybe we can get this fixed.

Cheers

---

### Post by potatan on 2009-11-14
I'm with Be in the UK too, and I can't get to it.  Maybe Getdeb has blocked the entire O2/Be Ip address range?  If so I'd have thought it was up to O2/Be to get themselves unblocked rather than relying on individuals?

---

### Post by EnlistedSquire on 2009-11-14
I just sent this via their "contact us" form:

> Hi,
Myself and several others who use the ISPs O2/Be (same comapany, different brands) in the UK are having trouble connecting to getdeb (see here for example - [http://ubuntuforums.org/showthread.php?t=1272616](http://ubuntuforums.org/showthread.php?t=1272616)). It has been suggested by our ISP that you are blocking their IP range. Can you confirm if this is the case, explain why if is the case, and let me know what we can do to resolve this? Thanks.

When I clicked submit I got a "page you requested could not be found" message and was redirected to their homepage so I don't know if it worked or not. I was using a proxy to access the site so that might have been the reason for it. I'll try again at work later. Maybe some other people could try to - power in numbers and all that.

---

### Post by Vadi on 2009-11-14
> **EnlistedSquire said:**
> I just sent this via their "contact us" form:



When I clicked submit I got a "page you requested could not be found" message and was redirected to their homepage so I don't know if it worked or not. I was using a proxy to access the site so that might have been the reason for it. I'll try again at work later. Maybe some other people could try to - power in numbers and all that.


We did receive the email and are looking into it.

---

### Post by EnlistedSquire on 2009-11-14
Superb, thanks Vadi. :D

---

### Post by EnlistedSquire on 2009-11-14
Reply from João:

> we are not blocking any IP range at the server level, I have forwarded the problem to our network admin. 

---

### Post by EnlistedSquire on 2009-11-16
The site's still not accessible. They've definitely got some routing issues. From just-ping.com:

> Location 	Result 	min. rrt 	avg. rrt 	max. rrt 	IP
 Amsterdam3, Netherlands: 	Okay 	53.8 	60.2 	101.4 	94.126.144.44
 Amsterdam2, Netherlands: 	Okay 	56.4 	58.9 	70.1 	94.126.144.44
 Florida, U.S.A.: 	Okay 	146.3 	147.9 	152.5 	94.126.144.44
 Hong Kong, China: 	Okay 	275.1 	281.0 	317.0 	94.126.144.44
 Sydney, Australia: 	Okay 	385.1 	389.5 	395.6 	94.126.144.44
 New York, U.S.A.: 	Okay 	173.8 	177.1 	183.2 	94.126.144.44
 Stockholm, Sweden: 	Okay 	78.2 	80.0 	81.1 	94.126.144.44
 Santa Clara, U.S.A.: 	Okay 	246.4 	251.2 	256.2 	94.126.144.44
 Vancouver, Canada: 	Okay 	205.2 	206.9 	208.7 	94.126.144.44
 ***Krakow, Poland: 	Packets lost (90%) 	122.9 	122.9 	122.9 	94.126.144.44***
 ***London, United Kingdom: 	Packets lost (100%) 				94.126.144.44***
 Madrid, Spain: 	Okay 	95.2 	98.4 	101.4 	94.126.144.44
 Padova, Italy: 	Okay 	90.2 	92.4 	95.1 	94.126.144.44
 Singapore, Singapore: 	Okay 	407.9 	410.1 	412.1 	94.126.144.44
 Austin, U.S.A.: 	Okay 	163.6 	163.9 	164.6 	94.126.144.44
 ***Cologne, Germany: 	Packets lost (90%) 	97.4 	97.4 	97.4 	94.126.144.44***
 Munchen, Germany: 	Okay 	66.7 	67.8 	69.1 	94.126.144.44
 Amsterdam, Netherlands: 	Okay 	52.6 	53.2 	54.4 	94.126.144.44
 Paris, France: 	Okay 	62.0 	63.1 	64.8 	94.126.144.44
 [I][B]Shanghai, China: 	Packets lost (20%) 	398.0 	413.8 	426.0 	94.126.144.44
 Melbourne, Australia: 	Packets lost (10%) 	395.6 	396.3 	397.8 	94.126.144.44
 Copenhagen, Denmark: 	Packets lost (90%) 	113.4 	113.4 	113.4 	94.126.144.44[/B][/I]
 Rio de Janeiro, Brazil: 	Okay 	253.9 	263.8 	297.9 	94.126.144.44
 Lille, France: 	Okay 	58.5 	59.4 	62.6 	94.126.144.44
 San Francisco, U.S.A.: 	Okay 	182.1 	182.9 	183.4 	94.126.144.44
 Chicago, U.S.A.: 	Okay 	139.3 	142.0 	144.0 	94.126.144.44
 ***Zurich, Switzerland: 	Packets lost (100%) 				94.126.144.44***
 Johannesburg, South Africa: 	Packets lost (100%) 				94.126.144.44
 Mumbai, India: 	Okay 	370.6 	386.4 	516.0 	94.126.144.44
 Nagano, Japan: 	Okay 	319.6 	324.9 	328.5 	94.126.144.44
 ***Haifa, Israel: 	Packets lost (100%) 				94.126.144.44***
 ***Auckland, New Zealand: 	Packets lost (20%) 	348.2 	353.0 	358.8 	94.126.144.44***
 Groningen, Netherlands: 	Okay 	56.0 	57.0 	61.2 	94.126.144.44
 A***ntwerp, Belgium: 	Packets lost (10%) 	57.7 	66.4 	125.2 	94.126.144.44***
 Dublin, Ireland: 	Okay 	58.0 	58.9 	60.7 	94.126.144.44
 Moscow, Russia: 	Okay 	116.1 	121.0 	125.3 	94.126.144.44
 ***Oslo, Norway: 	Packets lost (80%) 	115.6 	115.7 	115.8 	94.126.144.44***
 Odessa, Ukraine: 	Okay 	96.2 	96.5 	96.8 	94.126.144.44

---

### Post by EnlistedSquire on 2009-11-18
Seems to be accessible now - yay!

---

### Post by potatan on 2009-11-21
playdeb.net and getdeb.net both seem to be working fine for me now too (on Be's network)

Thought I'd post in case anyone else was looking.

---

