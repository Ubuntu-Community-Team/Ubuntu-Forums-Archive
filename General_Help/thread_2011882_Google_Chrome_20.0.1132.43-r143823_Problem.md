---
title: "Google Chrome 20.0.1132.43-r143823 Problem"
date: 2012-06-28
forum: General Help
---

### Post by josekym on 2012-06-28
I am using 10.04 LTS x86 and today I ran some updates on it which included Google Chrome (v20.0.1132.43-r143823) from the repos.  After applying updates and restarting, Google Chrome no longer loads when I call it up, but instead spawns 2 processes and becomes a "zombie" per System Monitor.

Downgrading to Google Chrome v91.0.1084.56 fixes the problem.

Any one else experiencing the same problem with the latest Google Chrome?

---

### Post by vasa1 on 2012-06-28
20.0.1132.43 (Official Build 143823) is working for me on 12.04. Don't know what to say ???
If you try again and still have problems, you could temporarily rename your profile folder in case something there is corrupted:
With no processes of Chrome running, rename "/home/your_name/.config/google-chrome" to something else.
When Chrome installs it will create a new folder but without any of the old information. If it works successfully, you will then have to figure out what exactly was the problem or just go with the new profile.

See: [http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059](http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059)

---

### Post by josekym on 2012-06-28
Thanks for replying, vasa1.

I tried completely removing Chrome (including the google-chrome folder), but with the same negative results.  Maybe I'll have better luck with the next update.

Too bad my machine can't handle 12.04, as it is very old in specs (AXP 2400+, 1GB DDR-400, 80GB HDD).  That's why I'm stuck with 10.04 LTS... Heheh.

---

### Post by vasa1 on 2012-06-28
FWIW, [https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)

---

### Post by grindcrust on 2012-06-28
> **josekym said:**
> I am using 10.04 LTS x86 and today I ran some updates on it which included Google Chrome (v20.0.1132.43-r143823) from the repos.  After applying updates and restarting, Google Chrome no longer loads when I call it up, but instead spawns 2 processes and becomes a "zombie" per System Monitor.

Downgrading to Google Chrome v91.0.1084.56 fixes the problem.

Any one else experiencing the same problem with the latest Google Chrome?


after upgrading to v20 crashed, does not appear , 
I tried looking for the version 19 , just found the v17 , installed , is working well , the v19 also worked well  

I use Ubuntu 12.04,   i 've tried the beta, but none works except version 19 or less

---

### Post by Egaeus on 2012-06-28
Vasa1 got it.  I have little to add, except to confirm that nothing I've tried works on Kubuntu 10.04 32-bit. I purged Chrome and reinstalled from the website, as well as trying the beta/testing version. I guess we'll just have to wait until the next update (hopefully today).  This is very uncharacteristic of Google in my experience, but we're all human, it seems.

---

### Post by vasa1 on 2012-06-28
Well, I don't know when they'll come up with a solution because they'll need to pin down the problem first. The sad thing is that Google, as of now, hasn't got enough information so far.

---

### Post by Egaeus on 2012-06-28
> **vasa1 said:**
> Well, I don't know when they'll come up with a solution because they'll need to pin down the problem first. The sad thing is that Google, as of now, hasn't got enough information so far.

UPDATE

I fixed the problem, for certain values of "fix."  Someone mentioned [on the chrome blog]("http://googlechromereleases.blogspot.com/2012/06/stable-channel-update_26.html") that for x64, the Flash player slowed it down.  I tried, and sure enough, that's the problem with x32 as well, though with a crash instead.

Go to /opt/google/chrome/PepperFlash and type 

```
sudo mv libpepflashplayer.so libpepflashplayer.so.bak
```

This will disable flash player, but Chrome will work.  How to fix both?  No idea.

---

### Post by craig10x on 2012-06-28
actually, all you have to do is type   about:  plugins  in your browser bar and it will bring up the plug ins on your google chrome...then click "details" and it will show the 2 flash plug ins your native adobe flash that ubuntu installed as well as the "pepper flash plug in" that is included in Chrome)...

Just disable pepper flash and see if that helps...i did that and it cleared up my weird flash problems on radio streams and you tube videos...

You will then be running on your "native" flash plug in.....

I'm going to keep it that way until they fix the bugs in the "pepper flash"...
it was introduced on this new version, which i suspect is causing a lot of these problems...

---

### Post by marl30 on 2012-06-28
> **craig10x said:**
> actually, all you have to do is type   about:  plugins  in your browser bar and it will bring up the plug ins on your google chrome...then click "details" and it will show the 2 flash plug ins your native adobe flash that ubuntu installed as well as the "pepper flash plug in" that is included in Chrome)...

Just disable pepper flash and see if that helps...i did that and it cleared up my weird flash problems on radio streams and you tube videos...

You will then be running on your "native" flash plug in.....

I'm going to keep it that way until they fix the bugs in the "pepper flash"...
it was introduced on this new version, which i suspect is causing a lot of these problems...

It's actually: chrome://plugins/ to get to the plugins. Then detail at the right of the flash plugin line. Disable flash 11.3 and then enable 11.2. Works for me too.

---

### Post by Egaeus on 2012-06-28
> **craig10x said:**
> actually, all you have to do is type   about:  plugins  in your browser bar...

Not when your browser won't start.

---

### Post by craig10x on 2012-06-28
right marl30...though if you type what i said it shows what you said in the url bar (lol)...

that would do it...i did temporarily re-enable pepper and it SEEMS to be behaving now...but if it starts in again, then i will just leave it of and wait for the fixes to arrive...

egaeus: good point!  but for those of us that are able to start it but just have the flash problem, it's an easy way to reach it...

---

### Post by vasa1 on 2012-06-28
> **Egaeus said:**
> ... we'll just have to wait until the next update (**hopefully today**). ...

Downloading the update (20.0.1132.47-r144678)! Hope it goes well for everybody :)

Edit: it maybe an update unrelated to the problem :(

 ... fixing something for the Mac Air something.

One more edit: I'm going to disable the google ppa and enable it only if their release blog mentions something worthwhile. That way, I won't be offered updates that are of no relevance to me.

---

### Post by vasa1 on 2012-06-29
Someone at Google feels that older CPUs won't play well with the "Pepper" Flash and suggest starting Chrome 230 with "--disable-bundled-ppapi-flash".
Comment #17 here: [http://code.google.com/p/chromium/issues/detail?id=134940](http://code.google.com/p/chromium/issues/detail?id=134940)

---

### Post by craig10x on 2012-06-29
It's not even "playing well" with some newer cpus...i have a 4 month old Toshiba Laptop with i3 core intel processor and i am unable to use pepper at all...

The update they sent last night doesn't do a thing to fix it...hopefully, they will get it smoothed out and we will eventually get an update that corrects the problem...
I love chrome though i am surprised they would release this now while it is still apparently very buggy... :confused:

---

### Post by vasa1 on 2012-06-29
> **craig10x said:**
> ...
The update they sent last night doesn't do a thing to fix it...
It wasn't meant to.> This release disables some of Chrome&#8217;s GPU acceleration features on Mac hardware containing the Intel HD 4000 graphics chip (e.g. the new Macbook Airs), in order to prevent a resource leak which is causing a kernel panic on that hardware. This is a temporary change while we work on fixing the root cause of the issue.

---

### Post by craig10x on 2012-06-29
The bug report for this has been filed with the chromium developers:

[http://code.google.com/p/chromium/issues/detail?id=128870](http://code.google.com/p/chromium/issues/detail?id=128870)

---

### Post by vasa1 on 2012-06-29
> **craig10x said:**
> The bug report for this has been filed with the chromium developers:

[http://code.google.com/p/chromium/issues/detail?id=128870](http://code.google.com/p/chromium/issues/detail?id=128870)

See the status near the top left: [untriaged]("http://www.chromium.org/getting-involved/bug-triage")

If it was a Windows or Mac bug it may have got VIP treatment ;)

---

### Post by craig10x on 2012-06-29
Last night's update did seem to help my problem with the higher cpu temps i was experiencing...maybe because i have intel (even though it isn't a mac...lol)...

But yeah, i guess it might be some time before they actually work on the pepper bug for linux...so we may be using our native adobe flash plug ins for some time to come...

---

### Post by lovinglinux on 2012-06-30
I haven't tested this, but anyone experiencing issues with the PepperFlash plugin could try to set plugins to "Click to play" in the "Privacy >> Content Settings". It might solve the problem, specially if you start Chrome with open tabs that has flash content. This way you can still make use of PepperFlash and speed up the browser start up.

Let me know if this works or not.

---

### Post by haplorrhine on 2012-07-01
> **Egaeus said:**
> UPDATEGo to /opt/google/chrome/PepperFlash and type 

```
sudo mv libpepflashplayer.so libpepflashplayer.so.bak
```This will disable flash player, but Chrome will work.  How to fix both?  No idea.
What code would reverse this change?

---

### Post by lovinglinux on 2012-07-01
> **haplorrhine said:**
> What code would reverse this change?

To revert use this:

```
sudo mv libpepflashplayer.so.bak libpepflashplayer.so
```

---

### Post by haplorrhine on 2012-07-02
> **lovinglinux said:**
> To revert use this:

```
sudo mv libpepflashplayer.so.bak libpepflashplayer.so
```

It's not working for this computer unless I'm in the wrong directories.
```
haplorrhine@haplorrhine-desktop:~$ sudo mv libpepflashplayer.so.bak libpepflashplayer.so
**mv: cannot stat `libpepflashplayer.so.bak': No such file or directory**
```
I got the same message for */opt/google/chrome* and */opt/google/chrome/PepperFlash*

---

### Post by vasa1 on 2012-07-02
> **haplorrhine said:**
> It's not working for this computer unless I'm in the wrong directories.
```
haplorrhine@haplorrhine-desktop:~$ sudo mv libpepflashplayer.so.bak libpepflashplayer.so
**mv: cannot stat `libpepflashplayer.so.bak': No such file or directory**
```
I got the same message for */opt/google/chrome* and */opt/google/chrome/PepperFlash*

@haplorrhine, could you do this?
Type **about:plugins** in the address bar and hit enter.
Then, in the page that opens, look for a little + sign near the top right and click on it.
Then, take a screenshot of the region that shows information about **Flash** and post that here?

---

### Post by haplorrhine on 2012-07-02
> **vasa1 said:**
> @haplorrhine, could you do this?
Type **about:plugins** in the address bar and hit enter.
Then, in the page that opens, look for a little + sign near the top right and click on it.
Then, take a screenshot of the region that shows information about **Flash** and post that here?

[IMG]http://i1160.photobucket.com/albums/q485/haplorrhine/1341251017.png[/IMG]
[IMG]http://ubuntuforums.org/[IMG]http://i1160.photobucket.com/albums/q485/haplorrhine/1341251017.png[/IMG]

---

### Post by Pilot6 on 2012-07-02
Disable flash 11.3

---

### Post by josekym on 2012-07-02
^^Unfortunately, it is not really a Flash 11.3 problem for me (although I also have problems with the latest flash version, which I solved with a downgrade).  Based on the other forum threads mentioned here, the problem seems to be with the older hardware (i.e. CPU lacking newer instructions sets) being used.  

Anyways, I'm sticking with GC v19.0.1084.56 for now, as well as Adobe Flash v11.1.102.63 for FF and Chromium.

---

### Post by lovinglinux on 2012-07-03
> **haplorrhine said:**
> It's not working for this computer unless I'm in the wrong directories.
```
haplorrhine@haplorrhine-desktop:~$ sudo mv libpepflashplayer.so.bak libpepflashplayer.so
**mv: cannot stat `libpepflashplayer.so.bak': No such file or directory**
```
I got the same message for */opt/google/chrome* and */opt/google/chrome/PepperFlash*

Instead of using command line, start file browser with gksudo to gain administrative rights, open the plugin directory, find the plugin file and rename it.

---

### Post by Cjames93 on 2012-07-03
does anyone have a like to download v19 or v17 of chrome as i cant seem to find one , or could anyone tell me a trusted site to look on? thanks

---

### Post by vasa1 on 2012-07-04
The good news is that work has started on the bug: [https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)

---

### Post by klugja on 2012-07-05
I looked in /var/cache, and I don't have level 19 Google Chrome anymore.  Can anyone tell me where to find Google Chrome 19.0.1084.56?

I tried CNET, but when you select a different level, you still get the latest, level 20, even though their download site changes the level to 19.

---

### Post by Pilot6 on 2012-07-06
You do not need Chrome 19. 20 works perfectly on old CPUs with disabled built in flash. If Chrome does not start just run in with --disable-bundled-ppapi-flash
External flash will be used.

---

### Post by vasa1 on 2012-07-10
> **vasa1 said:**
> The good news is that work has started on the bug: [https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)

The bad news is that the fix [seems to be limited]("https://code.google.com/p/chromium/issues/detail?id=134940#c57") to disabling Pepper Flash automatically for boxes with affected CPUs and allowing Chrome to start without a switch.
> Disable bundled PPAPI Flash on Linux ia32 when SSE2 is not available.

---

