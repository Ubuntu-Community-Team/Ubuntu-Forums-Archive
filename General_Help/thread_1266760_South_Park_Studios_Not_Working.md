---
title: "South Park Studios Not Working"
date: 2009-09-15
forum: General Help
---

### Post by betacortex on 2009-09-15
Whenever I go to SouthParkstudios.com and try to watch a video in firefox, the whole browser freezes and has to be force quit. This is really frustrating and trying to watch it through VirtualBox is irritating, so can anyone give me some help please?

Thanks

---

### Post by betacortex on 2009-09-15
Ummm... Haha Please?

---

### Post by yabbadabbadont on 2009-09-15
The versions of the OS, Firefox, and Flash plugin you are using just might help others to help you...  ;)

Edit: They must have changed something.  While I don't get any lockups, I am getting an error message instead of the video, while I used to be able to view them fine.

```
Error loading stylesheet. RSL http://media.mtvnservices.com/global/flex/rsl/framework_3.2.0.3958.swz failed to load. Error #2046
```

I'm going to disable adblock and see what happens.

Edit2: Nope, same error as before.

Flash works fine for me on most other sites, and it used to work on southparkstudios too.

To the OP, does flash also work on other sites for you?

Edit3: I can manually download the file listed in the error message.  I wonder what error "2046" is?


SOLUTION: at least for me (;))  Turns out that their website now requires that you allow third party flash content in your flash security settings...  <insert obscene explicative here>  I guess that from now on, I just won't bother watching their show.  (at least not at the official site...)

---

### Post by betacortex on 2009-09-16
Thanks I will try that when I get home. I'm sorry I didn't give the prelim info, that's my fault. Thanks for actually replying! :)

---

### Post by Shpongle on 2009-09-16
try allsp.com :-)

---

### Post by betacortex on 2009-09-16
So it seems that the newest season on the website works perfectly but the older episodes will not play and cause the browser to have to be force quited.

As for my comp info 

P4 3.0Ghz Build
9.04 Jaunty
Firefox 3.0.14
Flash Player 10

---

### Post by betacortex on 2009-09-17
Any more ideas please?

---

### Post by betacortex on 2009-09-20
Guess not...

---

### Post by Shinywalrus on 2009-10-08
Error 2046 in Flash denotes a certificate problem. The most common culprit, apparently, is incorrect system time. 
 
For me, the system time had reverted to a date in 2002 for some reason; adjusting it allowed me to view the site with no problems whatsoever.

---

### Post by shoup904 on 2009-11-05
> **Shinywalrus said:**
> Error 2046 in Flash denotes a certificate problem. The most common culprit, apparently, is incorrect system time. 
 
For me, the system time had reverted to a date in 2002 for some reason; adjusting it allowed me to view the site with no problems whatsoever.




When I started my computer this afternoon, the system time and date was completely off.  Apparently,  my computer traveled through time (backwards of course).  Date: 1601 Time 12-something am.  It was Nov 4-09 around 6pm.  :?: 


I could not watch the new southpark tonight and found this forum.

---

### Post by joehill on 2010-08-03
Hmm, none of these solutions work for me. I've tried allowing 3rd-party content and even changing my system time to make it look like I'm in the US. I wonder if it's detecting by my IP address that I'm not in the US (as many content providers do) and deciding I'm not in the right region.

Oh and I should note that I have the same problem with other Comedy Central sites too, such as Daily Show and Colbert Report.

Any other possible suggestions out there?

---

### Post by zorblek on 2010-08-20
I am also experiencing this problem, and none of the solutions suggested above work for me. I have also tried installing all the different flash packages for Ubuntu with no luck.

---

### Post by thalience on 2010-09-17
I just found that I had an old firefox profile hanging around in my home directory (.mozilla/firefox/), when firefox actually uses .firefox on my system. Deleting the old profile allowed me to view the videos on thedailyshow.com and southparkstudios.com.

You may think that this couldn't be the problem since the website fails in multiple browsers (chrome etc). However, I traced the plugin and found that it always tries to access the firefox (really xulrunner) certificate database even when run from other browsers.

I think the old profile was missing the certificate authority used to sign the .swz file, leading to the Error 2046 (certificate problem).

Hope this helps anyone who finds that it works from a fresh user account, but not for their normal one.

---

### Post by svbob on 2010-09-21
Deleting that profile (home folder/.mozilla/firefox/profile.ini ) worked great. up and running instantly.

---

### Post by kurt3rd on 2010-12-09
After some digging around on the internet the fix all solution is actually this:

RE: video problems
 	 
TheLongTailor
 
thelongtailor
Production Assistant
Posts: 7
Registered:
09-09-2010
Posted: 09-09-2010 4:49 PM

error 2046 video problem - solution , fix!!!

Hey world, I've finally fixed this problem, here's how;

1.) make sure you have flash player installed

2.) go to

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html)

-> there you'll see the flash player settings (it's no image but real settings window)

3.) uncheck the box at the bottom (that saves common Flash components to reduce download time)

Error 2046 problem fixed!

All credits go out to A.Alajmovic @ [www.Alphaverse.com](www.Alphaverse.com)

 
CREDIT:

[http://forums.thedailyshow.com/?page=ThreadView&thread_id=15215&pg=2](http://forums.thedailyshow.com/?page=ThreadView&thread_id=15215&pg=2)

---

