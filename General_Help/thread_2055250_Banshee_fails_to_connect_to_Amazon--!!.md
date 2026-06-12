---
title: "Banshee fails to connect to Amazon--??!!??"
date: 2012-09-08
forum: General Help
---

### Post by Subito Piano on 2012-09-08
The title says it all.  I try to download an album from Amazon.com thru Banshee and it just keeps trying to connect.  This was never a problem before, even after upgrading to 12.04, although i only downloaded individual songs on precise.   Good thing i've only spent 99 cents so far...

Insights appreciated.

---

### Post by pete04 on 2012-09-21
Hey Subito, 

Same thing happened to me. I was able to easily download individual mp3s from the browser, so no loss. Hopefully you figured this out, too by now.

 But Banshee completely failed to connect to both download the album or to download individual tracks from the player window. 

Would love to hear if anyone found a solution.

---

### Post by Subito Piano on 2012-09-21
I installed Pymazon -- works great.  Still annoyed (and i DON'T blame Banshee!!)

---

### Post by relph on 2012-12-08
I, too, am having no luck with Banshee and my Amazon AMZ files.

I tried running "banshee --debug" and I see messages such as the following:


[FONT="Courier New"][SIZE="2"][1 Debug 11:22:19.645] Starting - Amazon MP3 Purchases
[1 Info  11:22:19.827] Starting to download "Joy to the World" by David Arkenstone
[1 Info  11:22:19.829] Starting to download "God Rest Ye Merry Gentlemen" by Beegie Adair
[1 Info  11:22:19.831] Downloading Amazon MP3 purchase - /home/relph/Downloads/Amazon-MP3-1354983355.amz

...

[17 Info  11:22:27.210] Amazon downloader: waiting for last file to be imported
[17 Info  11:22:27.213] Amazon downloader: last file imported; finishing
[17 Debug 11:22:27.213] Finished - Amazon MP3 Purchases
[/SIZE][/FONT]

But it never actually downloads any of the tracks.  Bogus.

---

### Post by Subito Piano on 2012-12-08
Yeah, fuggetabout pymazon as well.  The only way is to use their stoopid cloud player and download one at a time.  You don't have to wait for the first one to finish downloading before starting the next song downloading, thankfully -- but it's a pain and ubuntu-one (7digital.com) just can't match amazon's prices.  Anybody know a LInux-friendly place with good prices?

---

