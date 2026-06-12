---
title: "Saving streaming flash video from website"
date: 2011-02-07
forum: General Help
---

### Post by NertSkull on 2011-02-07
Is there a way to save a flash video from a website to my computer?  My wife is asking me if I can save a video from her work onto a flash drive so she can take it in to a meeting tomorrow and play it from the flash drive.

I've heard of firefox plugins for saving youtube files.  But I don't want it from youtube or similar sites.  This would be off of her work's (its a college) webiste so she can play the video where they don't have internet access.

Is this possible?  I tried finding saved caches from firefox or chrome with the video still open, but I had no luck.  

But then again, I don't know what I'm doing.

Thanks

---

### Post by BUSHYBOB on 2011-02-07
Look in /tmp

---

### Post by sydbat on 2011-02-07
[downloadhelper]("https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/") for Firefox.

---

### Post by NertSkull on 2011-02-07
Thanks, but neither of those seemed to work.  I can't find anything in tmp that was even big enough to be a movie file.

And download helper doesn't work on the site.

I tried doing the things in this thread

[http://ubuntuforums.org/showthread.php?t=40193](http://ubuntuforums.org/showthread.php?t=40193)

But I can't find a direct link to the video itself.  I've looked through the source code on the page itself 5 times and there is no link that I can tell points to the movie.  Just lots of Java script calls that link to the name of the movie, but not the full path.

So I think I'm just going to tell her it can't be done.  Shouldn't be a huge deal.

Thanks though

---

### Post by Doctor.Suse on 2011-02-07
1. install firefox
2. install grease monkey
3. go to userscripts website and find appropriate script
4. download video clip

5. or perhaps pm me the link to the video and i will get it for you

---

### Post by henrodon on 2011-02-18
> **BUSHYBOB said:**
> Look in /tmp

Until the latest update to Chrome, that worked. Now it doesn't. Can anyone tell me where Chrome now saves these files, or does it not save them at all now???

---

### Post by Grenage on 2011-02-18
The new adobe flash player stores its temporary data in the same place as the browser. *cheer*

I don't know where chrome stores it's temp files (/home/user/.chrome/ maybe?), but I'd look there.

---

### Post by t0p on 2011-02-18
Check out the link in my sig.  You'll find a whole load of ways to save streaming video in Ubuntu/Linux.

---

### Post by Hoopz on 2011-02-18
> **henrodon said:**
> Until the latest update to Chrome, that worked. Now it doesn't. Can anyone tell me where Chrome now saves these files, or does it not save them at all now???

/home/username/.cache/google-chrome/Default/Cache

---

### Post by henrodon on 2011-02-18
> **Hoopz said:**
> /home/username/.cache/google-chrome/Default/Cache

Great!  Thank you very much. (No thanks to Google for changing it from the way it was before.)

---

### Post by Vaphell on 2011-02-18
it's flash, it does the same with firefox - and it's a good thing that it obeys browser rules and stores temporary files together with the rest of stuff in browser cache.

---

### Post by chetancrasta on 2011-02-25
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by mike941 on 2011-02-26
Can someone plz post a link to Firefox's tmp file. I'm looking for it but so far i havn't even found firefox.

---

### Post by TeoBigusGeekus on 2011-02-26
Read my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

---

### Post by mike941 on 2011-02-26
Ok that didn't help can someone plz just post the exact filepath to firefox cache on ubuntu 10.04 64 bit please.

---

### Post by Vaphell on 2011-02-26
~/.mozilla/firefox/random.garbage/Cache

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/2011...ash-files.html](http://davesource.com/Solutions/2011...ash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

### Post by andrew.46 on 2011-04-10
> **NertSkull said:**
> But I can't find a direct link to the video itself.  I've looked through the source code on the page itself 5 times and there is no link that I can tell points to the movie.  Just lots of Java script calls that link to the name of the movie, but not the full path.

Can you give the address of this page?

---

