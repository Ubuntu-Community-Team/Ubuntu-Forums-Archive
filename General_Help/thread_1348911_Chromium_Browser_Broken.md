---
title: "Chromium Browser Broken"
date: 2009-12-07
forum: General Help
---

### Post by brydonhunter on 2009-12-07
My Chromium was working really well until the last kernel update, 2.6.31-16. After the update, Chromium no longer displays any web pages. The browser seems to connect to the website but there is nothing being displayed and there is no source.

I removed Chromium completely, and re-installed, no luck. I rebooted using kernel 2.6.31-15, no luck. I deleted the .config/chromium directory, no luck. 

Anybody have any ideas? I want my Chromium back !!

---

### Post by brydonhunter on 2009-12-08
Just an update, the web page source is downloaded but not being displayed. Neither of the internal Chromium pages is rendered either.

This is not good, I miss Chromium.

---

### Post by The Thug on 2009-12-08
I had a problem yesterdaywith Chromium displaying big black patches on my screen and have now reverted back to Firefox.

My kernel update only took place today so that wasn't to blame. 

Here's the link to the thread I posted. [http://ubuntuforums.org/showthread.php?t=1348355](http://ubuntuforums.org/showthread.php?t=1348355)

---

### Post by brydonhunter on 2009-12-08
The only other possible cause that I can think of is that there was a gdm update around the same time.

I have also created another account on the computer and the same problem. This is strange.

---

### Post by otchie1 on 2009-12-08
You are not alone.
Latest chromium is broken making a black or fuzzy mess of many web pages.

No idea what the devs were trying to fix but clearly they didn't test it very well.

---

### Post by darco on 2009-12-08
4.0.267.0 (Ubuntu build 34029) seems to be working fine now.....




darco

---

### Post by brydonhunter on 2009-12-08
latest update doesn't work for me. I don't seem to be having the same issue a lot of others are having, black squares on the screen. My problem is that it is not rendering whatsoever. Including the "internal" chromium pages.

---

### Post by fragos on 2009-12-08
4.0.267.0 has fixed the "black square" problem for me.

---

### Post by BinaryFeast on 2009-12-08
I also had the rendering problem with black and "fuzzy" areas yesterday, but the latest build (4.0.267.0) has fixed that for me.

---

### Post by Mud.Knee.Havoc on 2009-12-08
I just installed the brand spanking new Chrome Beta and it's doing the same thing.  It doesn't matter which website I try to visit, I just get a blank white browser window.

It's downloading content, however... I can save the page onto my hard drive and the content is there.

---

### Post by brydonhunter on 2009-12-08
i have removed chromium, installed google chrome beta and the same thing is happening. something tells me that some X setting has been crewed around with and causing this problem.

Any ideas?

---

### Post by otchie1 on 2009-12-10
> **brydonhunter said:**
> i have removed chromium, installed google chrome beta and the same thing is happening. something tells me that some X setting has been crewed around with and causing this problem.

Any ideas?
latest repo update cured me >>> 4.0.267.0 (Ubuntu build 34059)

But i was working just fine with Chrome before so I know it was the errant update that messed things up.

I can't think of anything in X that would ONLY mess up your Chromium browser.

Rip it all out and do it again - maybe?

---

### Post by brydonhunter on 2009-12-13
Oops, this ended up being my fault. Looking at the console while running Chromium, it displayed an error, not able to write to /dev/shm.

At the time this problem started, I had modified my fstab file to put /dev/shm as ro, for security reasons. Changing it to rw and rebooting solved my problem.

Thanks for all the suggestions from everyone, just happy to get my Chromium back :D

Scott

---

