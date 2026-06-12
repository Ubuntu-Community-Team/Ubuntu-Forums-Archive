---
title: "no access ubuntu.com"
date: 2011-04-13
forum: General Help
---

### Post by pazzl on 2011-04-13
hi guys!

help me solve my problem
I was interested in ubuntu,
but was unable to enter the site from work,
provider said that from his side everything is OK,
problems should not be,
may be banned my ip address
I'm first time here
it's not my fault if it is,
tell me where to go and who can help
thanks in advance,
google translation from Russian

my ip: 194.143.150.226

---

### Post by mikewhatever on 2011-04-13
Try this -> [http://forum.ubuntu.ru/](http://forum.ubuntu.ru/). Hope it works.

---

### Post by coffeecat on 2011-04-13
Is it the main Ubuntu/Canonical site you are having problems with?

[http://www.ubuntu.com/](http://www.ubuntu.com/)

What error message do you get when you try to access it from work?

---

### Post by pazzl on 2011-04-13
[http://ubuntu.ru/](http://ubuntu.ru/) opens ok
but it is built on links to ubuntu.com,
I need the support, of course,
ubuntu.com and all dl links not opens (page unavailable) and not ping...

---

### Post by mikewhatever on 2011-04-13
Here are some download links for Ubuntu from the Russian mirror on Yandex.
[http://mirror.yandex.ru/ubuntu-cdimage/releases/](http://mirror.yandex.ru/ubuntu-cdimage/releases/)

---

### Post by earthpigg on 2011-04-13
That is very odd. Unless you and [Alexander Lukashenko]("http://en.wikipedia.org/wiki/United_States_embargoes#Targeted_parties") share an ISP or [something]("http://blogs.euobserver.com/rakhlei/tag/eu-sanctions-belarus/") and the range of IP's has been embargoed... I know [folks in Cuba cannot visit sourceforge]("http://sourceforge.net/blog/clarifying-sourceforgenets-denial-of-site-access-for-certain-persons-in-accordance-with-us-law/"), for example, because of similar silly nonsense (Some foolish politicians think open source software is a 'munition' or 'economic capital' and the like - and force some open source centered websites to act accordingly. We live in an insane world.). 

But you are in Russia, right? And your ISP isn't the national ISP of Belarus or the back-end tech support for that national ISP?

(This probably just me creating an insane conspiracy theory.)

---

### Post by earthpigg on 2011-04-13
is the nearest major city to you across the Belarusian border?

can you ping ubuntu.com?

windows command prompt: ping ubuntu.com
linux command prompt: ping -c 3 ubuntu.com


what if you skip the DNS layer and go directly to this web address:

[http://91.189.94.156](http://91.189.94.156)

---

### Post by earthpigg on 2011-04-13
here is a writeup wherein an Sun employee discusses the mistaken identity that the first poster may be suffering from according to my weird conjecture:

[http://blogs.sun.com/alfredc/entry/embargoed_countries_software_downloads](http://blogs.sun.com/alfredc/entry/embargoed_countries_software_downloads)

> But because the Internet is constantly growing and evolving, false positive matches do occur, denying legitimate end users access.

---

### Post by Enigmapond on 2011-04-13
> **earthpigg said:**
> 
(This probably just me creating an insane conspiracy theory.)

But a good one. I lived in Minsk for a year or so. He's insane and totally against free ANYTHING and there are many sites that are blocked by Beltelecom.

---

### Post by earthpigg on 2011-04-13
> **Enigmapond said:**
> But a good one. I lived in Minsk for a year or so. He's insane and totally against free ANYTHING and there are many sites that are blocked by Beltelecom.

Ya. I'm not sure, but if many of pazzl's http requests go through Belarus, could he be affected by their having blocked a website? that is why i asked the question about the nearest major urban center being across the border.

I can think of a dozen political reasons why certain dictators would want to block Ubuntu.com, none of which we can discuss on the forum.

I recall that a few years ago, Pakistan's gov't blocked some website thus making that website temporarily unavailable to *the entire world*... so, it isn't impossible that Belarus blocking something could experience similar cross-border contamination.

---

### Post by earthpigg on 2011-04-13
hrm, nope. he seems to be in the Moscow area. [http://ip2geolocation.com/?ip=194.143.150.226&lang=en](http://ip2geolocation.com/?ip=194.143.150.226&lang=en)

i'd be curios to see the /etc/hosts.deny in play, here.

pazzl - you can visit ubuntu.com from other places, right? just not at work?

---

### Post by Enigmapond on 2011-04-13
It's not far really. 400+ miles to Moscow from Minsk which is in the middle of the country. Like from New York City to Concord, NH area..so still anything is possible.

---

### Post by pazzl on 2011-04-14
i live near moscow,
but i see ukrainian flag in soulseek (p2p music fileshare soft)
also i have czech flag when at home :)

show today 2 tracert logs, its funny

---

### Post by pazzl on 2011-04-14
&#1086;&#1082;, it works today!
I think this is a shaman passes my provider
its a very long road :)

  1     4 ms     6 ms     4 ms  ws-192-168-1-1.st-net.ru [192.168.1.1]
  2     9 ms    12 ms    10 ms  ws-192-168-7-1.st-net.ru [192.168.7.1]
  3    23 ms    21 ms    15 ms  192.168.253.10
  4     1 ms     1 ms     2 ms  ws-172-20-0-2.st-net.ru [172.20.0.2]
  5    43 ms    31 ms    22 ms  192.168.251.21
  6    20 ms    16 ms    11 ms  94.25.4.141
  7    60 ms    61 ms    60 ms  95.167.92.58
  8     *       70 ms    75 ms  **64.211.193.169**
  9    52 ms    51 ms    68 ms  ae8.scr4.FRA4.gblx.net [67.16.145.241]
 10   279 ms   214 ms   245 ms  te6-2-10G.ar4.FRA3.gblx.net [67.17.70.189]
 11    76 ms    75 ms     *     ge-6-11.car2.Frankfurt1.Level3.net [195.122.136.
245]
 12    67 ms     *        *     vlan69.csw1.Frankfurt1.Level3.net [4.68.23.62]
 13     *       63 ms    62 ms  ae-62-62.ebr2.Frankfurt1.Level3.net [4.69.140.17
]
 14    73 ms    74 ms    71 ms  ae-21-21.ebr2.London1.Level3.net [4.69.148.185]

 15    81 ms     *       67 ms  4.69.143.93
 16     *       93 ms    96 ms  ae-3-3.ebr2.London2.Level3.net [4.69.141.190]
 17     *        *        *     &#1055;&#1088;&#1077;&#1074;&#1099;&#1096;&#1077;&#1085; &#1080;&#1085;&#1090;&#1077;&#1088;&#1074;&#1072;&#1083; &#1086;&#1078;&#1080;&#1076;&#1072;&#1085;&#1080;&#1103; &#1076;&#1083;&#1103; &#1079;&#1072;&#1087;&#1088;&#1086;&#1089;&#1072;.
 18     *        *       62 ms  gi1-0-1.oxygen.canonical.com [195.50.121.2]
 19    60 ms    64 ms     *     eth0.peumo.canonical.com [91.189.88.10]
 20    87 ms    69 ms     *     vostok.canonical.com [91.189.94.156]
----------------------
for comparison my home way:

  1     3 ms     2 ms     2 ms  178.215.89.1
  2     2 ms     4 ms     3 ms  c7606.speedyline.ru [213.108.16.1]
  3     3 ms     4 ms     3 ms  ae6-220.RT.M9.MSK.RU.retn.net [87.245.255.65]
  4    52 ms   116 ms    52 ms  ae1-9.RT.TC2.LON.UK.retn.net [87.245.233.98]
  5    71 ms    86 ms    97 ms  ge2-22-0-cr0.tch.uk.as6908.net [87.245.245.10]
  6    53 ms    53 ms    53 ms  canonical-gw.gwr.datahop.net [213.133.130.106]
  7    51 ms    52 ms    51 ms  eth0.peumo.canonical.com [91.189.88.10]
  8    52 ms    51 ms    50 ms  vostok.canonical.com [91.189.94.156]

---

### Post by pazzl on 2011-04-14
and i think **earthpigg** right,
yesterday tracert ends with Beltelekom,
today trafic goes another way,
through USA :lol:

[http://ip2geolocation.com/?ip=64.211.193.169&x=0&y=0](http://ip2geolocation.com/?ip=64.211.193.169&x=0&y=0)

---

### Post by earthpigg on 2011-04-14
I'm glad my conspiracy theory proved not so outlandish after all, and am glad that ubuntu.com is now working for you at least sometimes. :)

---

### Post by earthpigg on 2011-04-14
for anyone else that consideres this thread to be academically interesting original research relevant to open source software, here is the precedent i referred to earlier regarding Pakistan.

[http://www.arabianbusiness.com/pakistan-puts-global-block-on-youtube-188398.html](http://www.arabianbusiness.com/pakistan-puts-global-block-on-youtube-188398.html)

(No political discussions about that, please. Link is only relevant to academicians such as myself that may consider including this anecdote in a research paper, or perhaps journalists.)

---

