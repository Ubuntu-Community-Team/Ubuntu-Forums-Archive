---
title: "LottaNZB / Sabnzbd slowing down to a crawl"
date: 2011-05-19
forum: General Help
---

### Post by Feelkarma on 2011-05-19
Hi all,
Again, I am in need of help - hopefully one day I'll be able to provide some but still a Linux newbie I guess :)

One of my problems is with Sabnzbd, have been looking for a solution for quite a while: when I start a download, it will do fine until it suddenly starts to slow down up to the point when the download speed falls to 0.

I have Ubuntu 11.04 (had the same issue under 10.10) with optical fiber internet connection (important as I get ridiculously high download speeds). I use Giganews Diamond. 

I was using LottaNZB which worked fine until they decided to move from HellaNZB to SabNZBd for reasons that seem a bit puzzling to me (SabNZBd has a fine interface, why would anyone need the LottaNZB interface to use it?).

**What I have tried so far:** uninstalling - reinstalling SabNZBd and LottaNZB, emptying the .Sabnzbd cache folder repeatedly (when a download starts, the cache folders starts filling up with up to 400 files). If I disconnect and then refresh, it will start again at full speed (about 4.5 Mb/s) but will rapidly slow down. The strange thing is that it doesn't always do that... 

As mentioned, I didn't get this problem with HellaNZB or even with Grabit (used with WINE but it's even more buggy than under Windows). Also, I have increased the refresh speed, as I read somewhere that it may be a solution, but no change. 

So my questions are:
1. Does anyone know how to fix this?
2. If not, is there any alternative to SabNZBd now that LottaNZB has dropped HellaNZB (which worked like a charm for me)? 
Otherwise I will look at the possibility to rolling back to a previous version of LottaNZB although I haven't found any simple way to do that yet...

Many thanks in advance!

[COLOR="DarkSlateGray"]Config:
Dual boot Windows XP / Ubuntu
M/B: Asus M3N H HDMI with Phenom CPU
2gb Kingston PC8500 Memory
Pioneer DVD writer
Samsung 500 gb HD[/COLOR]

---

### Post by rodneymckay on 2011-05-19
Hi, Are you sure, that the reinstall was done correctly? Here's a nice little guide on how to set up Sabnzbd+...

[http://www.ainer.org/sabnzbd-install-setup-and-configuration-guide-for-ubuntu-10-04-lucid-lynx](http://www.ainer.org/sabnzbd-install-setup-and-configuration-guide-for-ubuntu-10-04-lucid-lynx)

Rgds.

---

### Post by Feelkarma on 2011-05-19
Hi Rodneymckay,
No I haven't but thanks, this looks very extensive. I'll uninstall and give it a go and post the results!
Kind regards

---

### Post by doas777 on 2011-05-19
my first thought is that this is not an issue on your sab server, but with your ISP. what does sab show in its connection log? anything?
ttraffic management would also explain why it only happens some of the time, and why it starts fast, but then gets throttled down to nothing.
have you noticed this happening more at specific times of day? does it ever happen if you queue up a nzb at 3AM, or only during the evening/weekend afternoons?

---

### Post by soulcat on 2011-05-19
hi

try changing your port 563 this is the default ssl, change to 443 or any other, my isp throttle port 563 to snails pace [traffic management] so i changed to 443 no problems


regards

---

### Post by Feelkarma on 2011-05-19
Thanks for your answers,
@doas777: I don't think so as I didn't have the problem with LottaNZB until the switch to Sab, neither do I have it with Grabit or Mimo.
@soulcat: I was using 563 with all of the above (HellaNZB, Mimo, Grabit) with no problem but I'll try.
Thanks

---

### Post by Feelkarma on 2011-05-28
Hi all,
Finally got around to trying different options out, none worked. I even installed Mint XFCE on another partition (not for that purpose!) and still the same.
The strange thing is that the traffic decreases and then increases again. I have noticed that when it decreases, the number of connections decreases. When the number of connections increases again up to the max (20) then the traffic goes up. So for some reason the number of connections is decreasing/increasing in Linux SABnzbd. I have tried using SABNzbd with windows and it works fine, so that excludes the modem and ISP.
This is driving me crazy (that and Goldman Sachs' stock price ;)).
Anyway, if anyone has any idea I'm buying.
Thanks!

---

### Post by Feelkarma on 2011-06-08
A last attempt to find a solution: here is the last entries of the SABnzbd logging +debug option just before the download stops :

```

2011-06-08 22:28:46,504::DEBUG::[bpsmeter:60] bps: 1775732.99003
2011-06-08 22:28:51,510::DEBUG::[bpsmeter:60] bps: 712875.683142
2011-06-08 22:28:56,517::DEBUG::[bpsmeter:60] bps: 286186.841916
2011-06-08 22:29:01,523::DEBUG::[bpsmeter:60] bps: 114895.541117
2011-06-08 22:29:06,529::DEBUG::[bpsmeter:60] bps: 46124.2817198
2011-06-08 22:29:11,534::DEBUG::[bpsmeter:60] bps: 18521.6660539
2011-06-08 22:29:16,538::DEBUG::[bpsmeter:60] bps: 7438.88101147
2011-06-08 22:29:21,541::DEBUG::[bpsmeter:60] bps: 2987.55612535
2011-06-08 22:29:26,546::DEBUG::[bpsmeter:60] bps: 1199.6891543
2011-06-08 22:29:31,553::DEBUG::[bpsmeter:60] bps: 481.610064186
2011-06-08 22:29:36,559::DEBUG::[bpsmeter:60] bps: 193.349857709
2011-06-08 22:29:41,565::DEBUG::[bpsmeter:60] bps: 77.6173708868
2011-06-08 22:29:46,571::DEBUG::[bpsmeter:60] bps: 31.1617616591
```
Any idea what this means?

Thanks

---

### Post by Raubsau on 2011-08-07
Please try to switch to another server (EU<->US/US<->EU) if your usenet provider has several locations.

---

