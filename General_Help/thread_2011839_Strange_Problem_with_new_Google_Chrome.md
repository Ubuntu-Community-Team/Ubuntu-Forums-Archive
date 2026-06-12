---
title: "Strange Problem with new Google Chrome"
date: 2012-06-27
forum: General Help
---

### Post by craig10x on 2012-06-27
I got the update today (in update manager) for the new version of Google Chrome
(20.1132.43-r1438) ...

In all the prior versions of Google Chrome (running on my ubunto 12.04) everything was fine...

On this new version, there seems to be major flash related problems....
On streaming radio stations, they are having trouble "buffering"...at the same time, i hear weird "gibberish" sounds...

And on some of these stream tuners the station wil not come in at all..On other stream tuners, the station will come in, but every few minutes it starts to buffer and the gibberish sounds comes back for a minute or two and then the station comes back in...

Going over to you tube videos, some are playing very speeded up....

I'm assuming this must be a bug in the new Chrome version 20..

Is anyone experiencing this with version 20?
Anyone know if it is a known bug? and is there any resolution for this?
(other then waiting for a possible fix)...

It's very strange behavior...and i have never had this before until this version was installed today...

All feedback appreciated ;)

---

### Post by Stanwilliamsmusic on 2012-06-28
It may be because of Pepper, no seriously lol,  My Chrome Browser stopped working altogether after the update today, and  I have reinstalled several times will Not even  start up.
I even purged it and installed beta version etc. and i had some  neat plugins, oh well.

The bad part is that  I was using Chrome's   flash player in Firefox   ( with the script from Flash-aid plugin) 
The first thing I noticed was  when a friend sent me a video in my gmail that the flash was dead in Firefox   so
I went to try it in Chrome and Chrome  would not even start, I had not tried it since the update earlier today.
That was the Only way I have had Any flash to work on Firefox since I Installed  11.10 after Maverick became unsupported.
 Now I Have NO Flash at all, period!    and I am  a musician... 
(I have Firefox 14.0)
I don't want to go back to Windows! I have  been on Linux 7 years now, 
 and html5 isn't quite there yet, or rather isn't implemented   widely enough at any rate.


   

In your Chrome directory (since todays update) you should see a directory named  PepperFlash, in it is a file named    libpepflashplayer.so
Or it is on my  system and mine is in: 

 opt/google/chrome/PepperFlash

 I am not sure what Adobe expects the rest of us to do, without I suppose . 
Flash has been  broken for quite some time for me as far as the  flash-plugin from Adobe goes anyway, and Gnash or Lightspark won't work for me  form the things i need to do with music, videos, etc.
I Was using Chrome's flash player for Firefox also until this.

Here is more   info on Adobe's blog  about Adobe partnering with Google,
 and  "Pepper",   their new flash player, (apparently).

[http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

An excerpt:
[B]code-named &#8220;Pepper&#8221; aims to provide a layer between the plugin and  browser that abstracts away differences between browser and operating  system implementations.

Adobe has been able to partner with Google in providing a &#8220;Pepper&#8221;  implementation of Flash Player for all x86/64 platforms supported by the  Google Chrome browser. Google will begin distributing this new  Pepper-based Flash Player as part of Chrome on all platforms, including  Linux, later this year.[/B] **For Flash Player releases after 11.2, the Flash Player browser plugin  for Linux will only be available via the &#8220;Pepper&#8221; API as part of the  Google Chrome browser distribution and will no longer be available as a  direct download from Adobe. Adobe will continue to provide security  updates to non-Pepper distributions of Flash Player 11.2 on Linux for  five years from its release.**


 
:guitar:

---

### Post by vasa1 on 2012-06-28
It's working for me with the usual stuff ... Google Docs, YouTube (but because of my slow net speed, I have to let the video go to the end and then hit replay). I don't know anything about streaming radio and why it would need Flash.
I've kept only the Pepper Flash enabled. I disabled the other one.

---

### Post by craig10x on 2012-06-28
I figured something happened in this update that was causing it....
Yes, streaming radio is actually flash driven, so it would be affected by this...
So, it has something to do with this new "pepper" thing (lol)?

Would love to know what to do to correct it, i really love using Chrome....
For the moment, i re-installed chromium (from the ubuntu software center) and that works fine because it is version 18 from awhile ago...

How about that google chrome beta? does that work properly?
Also, anyone who have any ideas what to do with this new pepper business...
please enlighten me ;)

---

### Post by craig10x on 2012-06-28
Update: based on the info you guys provided me, i tried two experiments...
I went to the plug ins and:

1) disabled the regular shockwave flash and just left Pepper enabled...
      Same weird problems

2) then i re-enabled the regular shockwave flash and DISABLED the new Pepper flash and guess what?   PROBLEM TOTALLY GONE!

Soooo...looks like it's problems with the new Pepper Flash which was added apparently, as of this new version 20....

I hope they get that Pepper Flash fixed eventually, meanwhile at least i got things working normal again...thank goodness...

Are they going to continue having both in there (shockwave regular flash and the new pepper)...i hope so (unless they get pepper working properly)...

---

### Post by vasa1 on 2012-06-28
> **Stanwilliamsmusic said:**
> ...  My Chrome Browser stopped working altogether after the update today, and  I have reinstalled several times will Not even  start up.
...
FWIW, [https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)

---

### Post by craig10x on 2012-06-28
Another update: this morning (just for an experiment) i re-enabled pepper and now the streams and videos are playing fine (so i have both plug ins on as they were originally set up on here)...

However, either way (pepper on or off) i have noticed (on my psensor temperature monitor) that temps are running much higher with chrome browser open and even more when i put the stream radio on)...

And others here have mentioned having other problems with it...so seems like this new version has quite a few bugs in it...

Hope they get this straightened out shortly and send down an updated version with fixes... :-(

PS: pepper flash plug started to act up again so i shut it off...so using ubuntu's flash instead solves it for me for now...and cpu temps seem to be more normal now...
I guess this new "pepper flash" has some kinks that still need to be smoothed out!

---

### Post by vasa1 on 2012-06-28
> **craig10x said:**
> Another update: this morning (just for an experiment) i re-enabled pepper and now the streams and videos are playing fine (so i have both plug ins on as they were originally set up on here)...
...
So your problem went away by itself?
Also wanted to ask ... do you have any of the **about:flags** switches enabled? Some of them may cause problems.

---

### Post by craig10x on 2012-06-28
> **vasa1 said:**
> So your problem went away by itself?
Also wanted to ask ... do you have any of the **about:flags** switches enabled? Some of them may cause problems.

I'll check that...
Well, i did re-enable "pepper" for a while but it started to act up again, so i ended up disabling it again...so, that way i am actually running off the adobe flash that was installed in the ubuntu restricted extras package...not the chrome built in "pepper" plug in...

I think i will leave it disabled until an updated version properly fixes it...

Running with my native adobe flash, i am not having any problems at all...both streaming radio and you tube videos are now functioning normal...

Oh...i checked the "flags" thing....sounds dangerous...don't think i will mess with those! (lol)...
Pepper has been reported by Chrome developers as having various "issues" so no doubt that is causing a lot of these problems..i will use my "temporary fix" until they get it smoothed out...

---

### Post by MickM on 2012-06-28
I too am having the same problem with streaming and youtube. I have tried to fix by disabling the plug-ins but to no avail.I am having the problem with Google Chrome and Firefox.

---

### Post by th1 on 2012-06-29
I don't have flash on firefox anymore since the only way to get it working was using flashaid to install chrome plugin in firefox... any ideas on how to reinstall chrome 19?

---

### Post by sanukcm on 2012-07-01
I was having the same problems, along with a few of my own. 

You can see the details here: 
[http://askubuntu.com/questions/158283/flash-videos-go-haywire-in-fullscreen-mode-in-google-chrome-20](http://askubuntu.com/questions/158283/flash-videos-go-haywire-in-fullscreen-mode-in-google-chrome-20)

In the end, this worked: 

[LIST]
[*]type ```
about:plugins
``` in the url bar
[*]click details
[*]disable flash (11.3), chrome defaults to system installed flash (11.2)
[/LIST]

Hope this helps!

---

### Post by cybergalvez on 2012-07-01
I had to disable pepper becuase it would freeze all the time. Hopping it will be fixed soon

---

### Post by catmandog on 2012-12-02
No, when your starting your computer - try the previous version of the kernel. 
my chrome and yourtube and fakebook pages are rendering fine now.

---

