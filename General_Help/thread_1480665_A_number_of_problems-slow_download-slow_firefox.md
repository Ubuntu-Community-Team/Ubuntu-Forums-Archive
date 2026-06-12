---
title: "A number of problems-slow download-slow firefox"
date: 2010-05-11
forum: General Help
---

### Post by Michael64 on 2010-05-11
I have a number of problems and didn't want to make a number of posts. I just wanted to start off by saying that I just downloaded Ubuntu and have not made any changes to the orignal setup made by the CD. Also I am a beginning just getting use to using terminal for everything, so if you can try to explain it in as simple a way possible that would be nice. Thanks.
 
First, when I am trying to download anything my rate of download in very very slow. I can download nothing before it just quits on me. For instance, I was downloading compiz and it takes like 5 minutes to get 10 out of 30 files. When it gets to 20 out of 30 it just quits.
 
Second, I don't know if this problem is related, but my firefox when browsing is also very slow. I can go to google really fast, but when I try to enter a search and press enter it take forever. It will timeout before it loads. Also neither can I enter a site manually.
 
Now I haven't installed any extra drivers or anything. I have been looking this up for sometime now and came across stuff like graphics drivers and other things. Also am I suppose to download any network stuff? I just started my internet up right after download and it connected. I was thinking you need other software to make it run faster.
 
Any help I can get would be greatly appreciated. Thanks.

---

### Post by warfacegod on 2010-05-11
This should prove useful for your Firefox troubles: [http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Michael64 on 2010-05-11
Hey thanks for the post. I would look into it, but currently I can't download anything. I am getting only 674 B(Less than kilo). This seems only to have when I use downloading package files. If I download from website or something I can download very quick. I downloaded firefox in like 2 seconds getting around 850kilo bytes.

---

### Post by 2hot6ft2 on 2010-05-11
> **Michael64 said:**
> This seems only to have when I use downloading package files. If I download from website or something I can download very quick. I downloaded firefox in like 2 seconds getting around 850kilo bytes.

System > Administration > Software Sources
Where it says Download from:
Click on it and select Other
Then on Select best Server
When it finishes click on Choose server
Then Close, and Reload

Now you should get packages faster.
:popcorn:

---

### Post by lovinglinux on 2010-05-11
> **Michael64 said:**
> Second, I don't know if this problem is related, but my firefox when browsing is also very slow. I can go to google really fast, but when I try to enter a search and press enter it take forever. It will timeout before it loads. Also neither can I enter a site manually.

[Disable ipv6](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html) [5th solution on that list].

---

### Post by Michael64 on 2010-05-12
I already disabled the ip6v thing. It didn't do anything.
 
Also thank you so much 2hot6ft2. My download is one hundred thousand times faster

---

### Post by moodle on 2010-05-13
Disabling ip6v doesn't work for me either.  Firefox is still painfully slow at loading web pages.

---

### Post by lovinglinux on 2010-05-13
> **Michael64 said:**
> I already disabled the ip6v thing. It didn't do anything.
 
Also thank you so much 2hot6ft2. My download is one hundred thousand times faster

> **moodle said:**
> Disabling ip6v doesn't work for me either.  Firefox is still painfully slow at loading web pages.

Have you tried to start a clean profile or a different browser to see if the problem persists? Could be a problem with your DNS server.

Also disabling the feature to block web forgeries and attack sites might help.

---

### Post by Michael64 on 2010-05-14
When I search on google, underneath the search bar it will say like 100,000 finds in .34 seconds. Then take an addition 5 seconds to finish loading.

---

### Post by wkulecz on 2010-05-14
run this command in a terminal:

date && nslookup msdn.com 8.8.4.4 && date


The time diffecence between the date commands running gives a good idication of if its dns problem or something else.

8.8.4.4 is Google's open dns, so if its fast, the problem is probably your ISP's dns.  You can setup your system to use Google's 8.8.8.8 and 8.8.4.4 and then all should be fine.

However, on 10.04 its about 5 seconds for dns lookups, while 8.04 is essentially instantaneous.  I've so far no solution :(  The problem seems introduced in 9.10.

---

### Post by lovinglinux on 2010-05-14
You could try to increase Firefox DNS cache. Change **network.dnsCacheExpiration** in **about:config** to **7200** and change **network.dnsCacheEntries **to **1000**. If you don't know how to do that, [see this]("http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html").

You can also try [Speed DNS](https://addons.mozilla.org/en-US/firefox/addon/54648) extension for Firefox.

---

### Post by Michael64 on 2010-05-15
Hey I have one more problem. My browser seems to be a little bit faster. But, when I watch videos from youtube. They load pretty fast, get like 30 % loaded then suddenly just stop. It wasn't slowly loading, but very fast and just suddenly stops out of the blue.

---

### Post by lovinglinux on 2010-05-15
> **Michael64 said:**
> Hey I have one more problem. My browser seems to be a little bit faster. But, when I watch videos from youtube. They load pretty fast, get like 30 % loaded then suddenly just stop. It wasn't slowly loading, but very fast and just suddenly stops out of the blue.

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Michael64 on 2010-05-16
I downloaded some of those add-ons, but even when I play it from the mplayer the loading bar stops. Maybe the problem is my internet. I am connected to my internet using a WUSB54g V.4 adapter. I didn't have to download anything it just worked when I first downloaded ubuntu. Also I have a intel graphics card which I never downloaded anything for.

---

### Post by Michael64 on 2010-05-18
When ever I load videos from youtube or any media site. The video's load bar will shoot forward going out to like 30% loaded in 10 seconds and then suddenly stop. Load percentages vary every reload, but it never makes it to 100%.

I have a WUSB54G v.4 adapter. I didn't have to load any software is just started working. It detects my network perfectly fine and connects fine.

I have tried some add-ons that let you play the video in your own mplayer, but the same thing happens.

I have also tried add-ons to download the video directly to the computer and here is where I think I have the issue. When downloading the video, the download will also stop after a few seconds and I will have to pause the load and start it up again to finish.

If you read the paragraph above this one then the problem I think comes down to the adapter losing connection with my router. The wireless connection never says that it lost connection, but this is what I am quessing. So is there anything I can do?

---

### Post by lovinglinux on 2010-05-18
> **Michael64 said:**
> If you read the paragraph above this one then the problem I think comes down to the adapter losing connection with my router. The wireless connection never says that it lost connection, but this is what I am quessing. So is there anything I can do?

It makes sense. Unfortunately, I know nothing about such devices.

---

### Post by Michael64 on 2010-05-18
I was also thinking since ubuntu goes through servers to download such videos. That maybe I am losing connection with the server.
 
If you go to software soruces then go to like best servers or something like that.

---

