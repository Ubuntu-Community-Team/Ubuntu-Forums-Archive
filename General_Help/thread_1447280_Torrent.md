---
title: "Torrent"
date: 2010-04-05
forum: General Help
---

### Post by limestone on 2010-04-05
Hi.. I got a problem using torrent.. Before I used to have 24Mbit/s ADSL and everything worked just fine i downloaded with 2.4Mb/s, but then we changed to 8Mbit/s ADSL (still same company) But now the torrent will reach only 50-100kb/s and no one can use the web when downloading torrent, the web will be sooooo slow... Still the updates etc reches 820kb/s... whats the problem? I gott the same equipment as before and i'm not new to torrent...

---

### Post by Mighty_Joe on 2010-04-05
If you are not new to torrents, you should be aware that they can create a ton of traffic.  Since ADSL does not upload and download at the same speed, it is very easy to overwhelm a connection.  
Have a look at [this article]("http://userpages.umbc.edu/~hamilton/btclientconfig.html") for the basics on configuring your connection and consult your client's documentation [or this tool]("http://infinite-source.de/az/az-calc.html") for the recommended settings for your connection speed.

---

### Post by 98cwitr on 2010-04-05
what torrent app are you using? Check to make sure the port is open, make sure your router support UPnP and/or port forwarding. Are you behind a firewall?

---

### Post by lovinglinux on 2010-04-05
> **lovinglinux said:**
> [COLOR="DarkRed"]**Maximum Upload Speed**[/COLOR] should be about 80% of the upload speed limit of your bandwidth, otherwise it will clog you network and reduce your download speed.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"]Re: BitTorrent optimization and troubleshooting guide[/color]]("http://ubuntuforums.org/showpost.php?p=7909527")

[*]**Tags:** [[color="DarkSlateGray"]torrent speed upload limit clog network[/color]]("http://www.google.com/search?q=torrent+speed+upload+limit+clog+network+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by limestone on 2010-04-06
> **98cwitr said:**
> what torrent app are you using? Check to make sure the port is open, make sure your router support UPnP and/or port forwarding. Are you behind a firewall?

I am using Transmission and the port is open.. I use the same hardware as before so there should be no changes in the router. Also, it doesn't matter if it me that downloads, its the same for anyone in my family, and thats after switching to 8Mbit/s. None of my friends with 8 & 2 Mbit has this problem..

---

### Post by cascade9 on 2010-04-06
> **pont.andersson said:**
> I am using Transmission and the port is open.. I use the same hardware as before so there should be no changes in the router. Also, it doesn't matter if it me that downloads, its the same for anyone in my family, and thats after switching to 8Mbit/s. None of my friends with 8 & 2 Mbit has this problem..

If its just ubuntu, then maybe you have a software problem of some sort, but if your family members are using windows at all and have the same issue.....then I would guess that your ISP is shaping torrents.

---

### Post by Grenage on 2010-04-06
Knock your maximum threads/connections per-torrent.  I cap mine at 40 (more than enough for me to get max speed).

Cheap home routers suck at handling a lot of connections.

---

### Post by limestone on 2010-04-06
> **cascade9 said:**
> If its just ubuntu, then maybe you have a software problem of some sort, but if your family members are using windows at all and have the same issue.....then I would guess that your ISP is shaping torrents.

Well, my family uses Windows and got the same problem, and my ISP is not shaping torrents, it's the same ISP as before and some of my friends uses the same...

---

### Post by lovinglinux on 2010-04-06
> **pont.andersson said:**
> Well, my family uses Windows and got the same problem, and my ISP is not shaping torrents, it's the same ISP as before and some of my friends uses the same...

Have you tried the solution posted on my previous post?

---

### Post by limestone on 2010-04-06
> **lovinglinux said:**
> Have you tried the solution posted on my previous post?

Ye, I had a look at that but cant see nothing thats wrong, I should also say that when we lowed the connection from 24 to 8.. the speed first went down to about 1-2Mbit so we called and complained and then the speed went up to 8 (with firefox etc) but now they still bill us for 24... So it could be the ISP that makes this to us to make us bring back the 24Mbit...

---

### Post by lovinglinux on 2010-04-06
> **pont.andersson said:**
> Ye, I had a look at that but cant see nothing thats wrong, I should also say that when we lowed the connection from 24 to 8.. the speed first went down to about 1-2Mbit so we called and complained and then the speed went up to 8 (with firefox etc) but now they still bill us for 24... So it could be the ISP that makes this to us to make us bring back the 24Mbit...

I doubt it. What is your upload speed limit provided by your ISP and what is the upload limit configured in the torrent client?

---

### Post by limestone on 2010-04-09
> **lovinglinux said:**
> I doubt it. What is your upload speed limit provided by your ISP and what is the upload limit configured in the torrent client?

ISP upload limit about 1Mbit/s and i have not set any limit in my torrent program...
I have friends with the same settings and the same ISP company with same speed, so i doubt that the problem is on my side... Also same result at all computers in my house.

---

### Post by lovinglinux on 2010-04-09
> **pont.andersson said:**
> ISP upload limit about 1Mbit/s and i have not set any limit in my torrent program...
I have friends with the same settings and the same ISP company with same speed, so i doubt that the problem is on my side... Also same result at all computers in my house.

That's the problem. As I said, you should setup the torrent upload limit to 80% of your bandwidth upload limit. That will fix the problem.

---

### Post by limestone on 2010-04-10
> **lovinglinux said:**
> That's the problem. As I said, you should setup the torrent upload limit to 80% of your bandwidth upload limit. That will fix the problem.

No it won't... I have tried that to but without results... I've tried everything i can come up with but nothing works....

---

### Post by limestone on 2010-04-12
> **pont.andersson said:**
> Hi.. I got a problem using torrent.. Before I used to have 24Mbit/s ADSL and everything worked just fine i downloaded with 2.4Mb/s, but then we changed to 8Mbit/s ADSL (still same company) But now the torrent will reach only 50-100kb/s and no one can use the web when downloading torrent, the web will be sooooo slow... Still the updates etc reches 820kb/s... whats the problem? I gott the same equipment as before and i'm not new to torrent...

I called my ISP and yeld at them and now... Everything works just fine. =)

---

### Post by 98cwitr on 2010-04-12
> **pont.andersson said:**
> I called my ISP and yeld at them and now... Everything works just fine. =)

what did you say exactly? I'm kinda nervous to tell them that my torrent app is slow :P

---

### Post by Monotoko on 2010-04-12
> **pont.andersson said:**
> I called my ISP and yeld at them and now... Everything works just fine. =)

Yelling appears to solve everything these days lol XD

---

### Post by limestone on 2010-04-12
> **98cwitr said:**
> what did you say exactly? I'm kinda nervous to tell them that my torrent app is slow :P

Just told them that my  internet was not working properly because when I was using torrents I  could not use the browser, and they whined that it was my fault, as  usual, because "they never do wrong", we did not come up with something  special and few hours later, everything works normally. ^ ^ The thing is that it's usaly

trainees in the support and that makes it soooo boring to call and you'll have to wait like forever.. But if you shore its not your fault, just go for it and place them, but trie to be gently because you don't want them mad on you:P

---

### Post by limestone on 2010-04-12
> **98cwitr said:**
> what did you say exactly? I'm kinda nervous to tell them that my torrent app is slow :P

Just told them that my  internet was not working properly because when I was using torrents I  could not use the browser, and they whined that it was my fault, as  usual, because "they never do wrong", we did not come up with something  special and few hours later, everything works normally. ^ ^ The thing is that it's usaly

trainees in the support and that makes it soooo boring to call and you'll have to wait like forever.. But if you shore its not your fault, just go for it and place them, but try to be gently because you don't want them mad on you:P

---

