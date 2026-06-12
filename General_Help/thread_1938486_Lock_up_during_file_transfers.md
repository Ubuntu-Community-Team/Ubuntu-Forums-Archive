---
title: "Lock up during file transfers"
date: 2012-03-09
forum: General Help
---

### Post by drascus on 2012-03-09
Hi All, 

I don't really know where to begin in diagnosing this issue. My system will sometimes lock up totally during file transfers or downloads. At least it seems thats when it most often occurs. I can't move my mouse or escape out of the desktop and the only thing that fixes it is to hold the power button and restart. 

Any ideas?

---

### Post by winh8r on 2012-03-09
You should be able to restart by using the following method:

Press and hold down the ALT key

Press and release the PrintScreen (PrtScr) key

type the following letters

R E I S U B

this should safely shutdown and restart the machine and avoid potential damage to the filesystem by a forced hard shutdown.

Do the lock ups occur when downloading/transferring larger files only?

---

### Post by MSPdwalt on 2012-03-09
> **winh8r said:**
> You should be able to restart by using the following method:

Press and hold down the ALT key

Press and release the PrintScreen (PrtScr) key

type the following letters

R E I S U B

this should safely shutdown and restart the machine and avoid potential damage to the filesystem by a forced hard shutdown.

Do the lock ups occur when downloading/transferring larger files only?

Dude...that is awesome..

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by drascus on 2012-03-09
win8hr: Yes it appears to be during large file transfers and downloads. I don't know how you figurd those commands out but I will give them a try! Is there anything that I should be looking at that will help me pin down the cause?

---

### Post by winh8r on 2012-03-09
Firstly, that shutdown/safe reboot thing was taught to me by a friend, who is sadly no longer with us, when he caught me doing the power button shutdown many years ago. I had never used it for ages, then I saw someone mention it on here and I have started suggesting that people use it to avoid damaging their filesystems.

Now, the freezing issue, I cannot say for sure what is causing it in your case but i can tell you when I have seen it happening:

1.Large downloads over a wireless connection, solved by using an ethernet cable when downloading large files.

2.Downloading torrents, particularly with Azureus(which I think is now called Vuze) there is apparently some problem with the way torrent clients use Java, that causes "confusion" leading to lockups.

3.It may be a sign that the hard drive may be failing, the freezes can occur when there are Input/Output errors due to a disk beginning to fail, cause the need for repeated attempts to successfully write data to the disc, and therefore slow everything down to a crawl
, as more attempts are needed so more resources are used and eventually the system just runs out of steam so to speak.

The failing hard drive is not for definite though unless you are experiencing other symptoms, like noise, slow response times etc.

Another possible cause is that you might be trying to demand too much from the machine all at once, a heavy download , and then trying to open emails and surf the internet can all add up to have the machine running at capacity.

I hope some of this might at least point you in the right direction.

---

