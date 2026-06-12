---
title: "Download speeds unrealistic"
date: 2011-02-21
forum: General Help
---

### Post by Spyderkid on 2011-02-21
I install Axel from the Software Centre (a download accelorator) and it unrealisticly fast seeing as I only have a 7 megabit download speed I ended up downloading Mandriva to run in virtual box in 5 seconds!
It only seemed however to be 300mb not the 600mb which it said on the site and virtual-box said that It couldn't use it as a boot file however it can with ubuntu?

whats going on?

---

### Post by Spyderkid on 2011-02-21
Also if you know could you explain how it works

---

### Post by emarkay on 2011-02-21
Google is your friend.
[http://axel.alioth.debian.org/](http://axel.alioth.debian.org/)

It's not increasing your DL speed, just opening multiple locations for the file.

Try the file without this "accellerator" and see if you get it correctly.

---

### Post by Spyderkid on 2011-02-22
It turns out I think that I didn't leave it long enough I effectively cancelled it half way through.

The only thing is it opens up a blank terminal which you cant do anything in and it never tells you when your done. So i closed it which cancelled the process.

The onyl way which I could find out if it was done was go to the files properties and check to see when the file size stops growing so I deleted it. It was too much bother.

---

### Post by Spyderkid on 2011-02-22
even though it did seem to increase the speed it seemed to come up with 300mb almost instantaniously and then averaged about 5mb/3secs

---

### Post by Grenage on 2011-02-22
> **Spyderkid said:**
> even though it did seem to increase the speed it seemed to come up with 300mb almost instantaniously and then averaged about 5mb/3secs

The 300MB was probably still cached.

---

### Post by Spyderkid on 2011-02-22
I should know this but what do you mean by still chached

---

### Post by Grenage on 2011-02-22
> **Spyderkid said:**
> I should know this but what do you mean by still chached

There's no particular reason you should have known.

When the files are downloaded, the data is stored temporarily, until (or long after) the file is written to its destination.  This could be either in RAM, or the browser's temp directory - it depends on the system and its configuration.

Assuming that the computer hasn't restarted, or the cache cleared, that data will still be there, so it doesn't need to be downloaded again.

---

### Post by Spyderkid on 2011-02-22
yeah I did try to do that.

---

### Post by swamyuefa on 2012-05-23
> **Spyderkid said:**
> I install Axel from the Software Centre (a download accelorator) and it unrealisticly fast seeing as I only have a 7 megabit download speed I ended up downloading Mandriva to run in virtual box in 5 seconds!
It only seemed however to be 300mb not the 600mb which it said on the site and virtual-box said that It couldn't use it as a boot file however it can with ubuntu?

whats going on?

Hi Spyderkid,
i have installed axel via software centre, but how to use it. :confused:  pls clearify, i am newbie to ubuntu.

---

