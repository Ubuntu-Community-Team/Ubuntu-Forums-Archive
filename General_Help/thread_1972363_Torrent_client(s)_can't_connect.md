---
title: "Torrent client(s) can't connect"
date: 2012-05-03
forum: General Help
---

### Post by LisaBrane on 2012-05-03
First, apologies if this isn't the correct place to post.

Second, I'm an absolute beginner.

Third, the issue.  I have been accessing wi-fi through public hot-spots since I'm unable to afford my own connection at the moment. And, yes, I know I shouldn't be doing so, but I have been using them to download torrents.

I started with ubuntu 11.04, upgraded to 11.10, and a few days ago to 12.04.  Prior to upgrading to 12.04, I used both transmission and deluge without any difficult at any public wi-fi I came across.  Since the upgrade to 12.04, neither tracker can connect at my favorite spot - the public library where I can sit without spending any $$ for hours.  Both will still connect at other wi-fi spots and, to the best of my knowledge, work just fine.

The inability to connect began as soon as the upgrade was complete (which also was done at the library if that should matter for some reason unknown to me). I've even tried utorrent under Wine, which also works every place else but the library. 

All 3 client programs use encryption and all are randomized as to port upon opening. Ports are closed, but I've still been able to maintain a respectable 1.6 ratio.

Any idea how to tweak the client(s)/ubuntu to get my access back? It doesn't seem likely that the library suddenly decided to block coincidentally with the exact day I upgraded (or that they could block every torrent every time I started a client, at least from what I understand), so it seems that something somewhere got "switched" that's preventing me from connecting to the trackers. 

Error messages include a simple "Connection timed out" and "Tracker gave HTTP response code 0: No Response".

Any ideas?

Thanks in advance for even taking the time to read this long thing.

---

### Post by Cheesemill on 2012-05-03
I'd guess that the library noticed that someone was torrenting and blocked access.

That's exactly what I would have done if I was in charge of their IT.

---

### Post by LisaBrane on 2012-05-03
@cheesemill

First, thanks.

Well, blocking is what I thought.  Except for this.  Library policy doesn't forbid torrenting per se (just warns against file sharing copyrighted material) and since I use encryption, they wouldn't know what I was torrenting. It doesn't block access to torrent sites (unless also categorized as porn or some security risk).

And, I upgraded on Saturday.  I wasn't running torrents before I upgraded nor during. I finished the upgrade literally a couple of minutes before the library closed, so I didn't run them at all.  But Sunday when I came in, I couldn't connect.  So, to institute blocking from Friday night seems a bit odd also.

Also, someone told me - and this is where I am out of my depth - that since trackers use random ports and I use them and they all can't be blocked, it becomes nearly impossible to block every single torrent that might be running.

I thought there might be some sort of association made with my particular hardware or OS, but was also told that was unlikely.

But I'm lost.

---

### Post by LisaBrane on 2012-05-03
And two other things. 

First, after I started being unable to connect to the trackers, some torrents continued to run - downloading and uploading based upon legacy peers I would guess. Wouldn't blocking of torrent traffic also block that?  So, the old torrents would continue to run, but new ones won't.

Second, since the upgrade I seem to "lose" my wireless connection.  Even though my icon shows a connection and the wireless menu shows a connection, I can't in fact even get web pages to load. I have to manually disconnect, wait a bit, reconnect and then get permission from the library website again to use wireless.  This would happen occasionally before the upgrade - once or twice in 8 or 9 hours, but since I upgraded on Saturday it seems to be nearly an hourly occurrence. 

That's another thing that makes me think something weird happened relative to the upgrade and that it isn't a blocking thing.

---

### Post by lhail on 2012-05-17
Hi Lisa
Same thing happened to me, I can connect to every website / service ok, except Vuze or QTransmission.
I have done a clean install of both and same problems.
This has only happened since I upgraded to 12.04, and I am connecting from home, not a library or shared access point.
Something in the 12.04 upgrade has closed the ports.

---

