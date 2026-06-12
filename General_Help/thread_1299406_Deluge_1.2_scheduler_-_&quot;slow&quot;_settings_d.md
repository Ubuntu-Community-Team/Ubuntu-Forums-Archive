---
title: "Deluge 1.2 scheduler - &quot;slow&quot; settings don't work"
date: 2009-10-23
forum: General Help
---

### Post by infinitejones on 2009-10-23
I'm using deluge 1.2.0-rc1-dev on Ubuntu Karmic beta. Everything's updated fully on Karmic.

My ISP limits my download bandwidth per billing period, and splits it into peak and off-peak - peak is 12pm to 2am daily, and off-peak is all other times. Upload bandwidth is unlimited, so I would like to use the Schedule plugin to allow uploading at all times but downloading only between 2am and 12pm.

In the Scheduler plugin settings, I've set all boxes from 2:00 to 11:59 every day to green, and all others to yellow. Then in the yellow "slow settings" area, I've set download limit to 0, upload limit to -1 and active torrents to -1. (I'm assuming -1 means unlimited.)

It makes no difference - Deluge continues to download and upload all torrents as quickly as possible.

If I set the yellow boxes in the grid to red, it stops all downloads, but I don't want to do that - I want to continue uploading even if deluge is not downloading.

Am I missing something obvious here? ;)

---

### Post by Vaphell on 2009-10-23
i tried that plugin, neat stuff
value of 0 is indeed bugged - it doesn't stop downloading, but 1 works just fine.

besides don't set upload = -1, it will clog your internet pipe and even simple webbrowsing would be extremely painful (http requests have to compete with torrents to get off your computer to ask server for the page, so does everything else), it's better to set it to let's say 70-80% of your upload capacity.

---

### Post by infinitejones on 2009-10-23
> **Vaphell said:**
> value of 0 is indeed bugged - it doesn't stop downloading, but 1 works just fine.

Hmmm... so maybe we should be reporting it as a bug somewhere then? Seems a fairly elementary thing to be not working properly... not criticising but they seem to have slightly weird development priorities. The scheduler plugin hasn't even existed since v1.2 and now it doesn't do properly one of the most useful things that it should do...

Anyway... the -1 thing isn't an issue for me, because it's not like I'm handling hundreds of torrents at a time!

---

### Post by Vaphell on 2009-10-24
i see you posted on deluge-torrent.org :-)

i was not talking about number of torrents, but about upload bandwidth. -1 will saturate your upload, timeouts and lags will start to show. Everything you can do with your internet requires sending out request. If that request has to compete with torrent connections you get huge delays/almost non-working internet. Having some spare bandwidth (10-20%) is enough to offer non-torrent stuff some space to work.
Think of it as a road congested to the point where even a police car with blinkenlights can't get through :-)

---

### Post by infinitejones on 2009-10-24
Yep, not assuming everyone who uses Deluge uses Ubuntu, and vice versa!

Anyway... the upload thing is fine, honestly! Setting it to -1 doesn't cause me any problems.

I'm more interested in solving the question of getting it to allow uploads but not downloads.

---

