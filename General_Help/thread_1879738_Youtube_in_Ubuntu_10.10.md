---
title: "Youtube in Ubuntu 10.10"
date: 2011-11-12
forum: General Help
---

### Post by oooryan on 2011-11-12
Alright so i installed Ubuntu on my desktop.  This desktop its pretty much the media computer for a tv.  So youtube is extrememly important for it.  Before Ubuntu I had windows 7 on this computer and the youtube videos streamed flawlessly.  Coupled with the fastest internet connection you can get in canada...1080p on youtube was like watching a bluray movie!!
But now in Ubuntu, when I try to watch a video in either chrome or firefox...regular resolution has slight lag and 1080 isn't even watchable.  My own suspicion is that hardware acceleration (im pretty sure that means youtube is using the gpu) is activated in Windows and not in Ubuntu.  I bought a pretty good video card for it (hd 6750) and windows plays streaming amazing..I  read somewhere that hardware acceleration doesn't work in linux..and the cpu for this machine is not that great at all (single core)...im hoping that information about linux and hardware accelration is outdated and there is something out there to help me with this....otherwise will i have a buy a new cpu?  Or can i run windows 7 in ubuntu with that virtual box thing and watch videos in there?

Is this the reason why steve jobs hated flash so much?

---

### Post by Lars Noodén on 2011-11-12
You can use [HTML5](http://www.youtube.com/html5) now on Youtube.  So Flash is not necessary any more.  Good riddance.  

Adobe is [stopping development](http://www.zdnet.com/blog/perlow/exclusive-adobe-ceases-development-on-mobile-browser-flash-refocuses-efforts-on-html5-updated/19226) of Flash for mobile devices so it is a matter of time before it dies out completely.  There no point in developing two sites, one for mobile devices and another for the rest when HTML5 can cover all of them.

---

### Post by flurospar on 2011-11-12
You might also like to have a look at [Flashvideoreplacer]("https://duckduckgo.com/?q=Flashvideoreplacer+%21amo")

---

### Post by blueridgedog on 2011-11-12
You should also try youtube with desktop effects turned off.  System -> Preferences -> Appearance -> Visual Effects...select none.

---

### Post by SeijiSensei on 2011-11-12
First, make sure you're using the ATI proprietary driver.  (You can install it with the "Additional Hardware" applet.)  Sadly, ATI has typically not invested the same level of effort into its Linux drivers as it has for Windows.  You can also search Google for "ubuntu ati flash" and see if any of the advice available there helps.

I'm doubtful you'll be able to watch 1080p content with a single-core processor and no video hardware acceleration.  You could try Windows in Virtualbox, but that may not be very helpful either. Windows will be talking to the virtual video hardware within the virtual machine.  However the proprietary "Guest Additions" to VB now support [hardware acceleration]("http://www.virtualbox.org/manual/ch04.html#guestadd-video"); maybe that will work for you.

---

### Post by blueridgedog on 2011-11-12
> **SeijiSensei said:**
> You could try Windows in Virtualbox, but that may not be very helpful either. Windows will be talking to the virtual video hardware within the virtual machine.  However the proprietary "Guest Additions" to VB now support [hardware acceleration]("http://www.virtualbox.org/manual/ch04.html#guestadd-video"); maybe that will work for you.

If the host OS has no or limited acceleration, then the guest won't have acceleration.

---

### Post by oooryan on 2011-11-12
How can i watch videos on youtube with html5? do i have to uninstall flash? because if it is rapidly becoming obsolete I don;'t even want it anymore slowing down my ubuntu system....will watching it in html 5 allow hardware acceleration? because i would like to use my videos card gpu to process the videos since it works so well in windows!

i know i can just get a new processor (i can upgrade to a 6 core) but the whole goal of this media desktop was to see how much I can push the limits of its power by reducing the amount of work the processor has to do (its the weakest link on my computer)...I go a good video card for graohic stuff...and an ssd will help everything load faster...there has to be a way to configure ubuntu to watch streaming videos with the gpu doing the work

---

### Post by Rockman-X on 2011-11-12
Give minitube a try. Minitube does not use flashplayer to watch youtube video's 

Download Minitube Site: [http://pkgs.org/search/?keyword=minitube](http://pkgs.org/search/?keyword=minitube)

---

### Post by Lars Noodén on 2011-11-13
> **oooryan said:**
> How can i watch videos on youtube with html5? 

Go to Youtube's HTML5 page and follow the super short instructions there:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by oooryan on 2011-11-13
Okay so youtube in html only works for videos without ads...for videos i actually want to watch (music videos etc..) it has to play in flash...hopefully this will be fixed in the near future....but when i watch no ad html5 videos, it still isn't up to my expectations in a streaming video..it still lags a bit...this might be because im using google chrome...apparently the newest firefox and even internet explorer 9 are currently better at html5 video streaming....theres absolutely no way i am installing internet explorer on this computer especially because it might only be the best at html5 video in windows...and firefox did better than chrome in html5, but still wasn't as good as i hoped...do i have to turn on hardware acceleration on html5 manually in chrome and firefox?  because that could be the reason for a slow stream...i also would prefer chrome to browse so hopefully the next version of chrome performs better at html5 video streaming

also I really don't mind using minitube for youtube videos until i upgrade this computers cpu...its a great alternative to using your gpu to watch youtube (correct me if im wrong) in my situation...but when i downloaded minitube and launched it...it wasn't playing any videos...i would search for a video and the results would come up and it would just skip through all the results without playing anything..if i put it in full screen...i would see the first frame of every result from beginning to end...if this an unstable version?  I have ubuntu 10.10 so maybe I should find an older version of minitube?

---

### Post by SeijiSensei on 2011-11-13
Many commercial video sites won't work if you block ads.  Hulu is more permissive than most; it just shows you a billboard complaining that you're not watching the ads then plays the video anyway after the alloted time has passed.  Other video sites won't play anything at all if you have ad blocking enabled.  With AdBlock Plus, you can open the list of "blockable items" and try picking and choosing what to permit if you know what to look for.

---

### Post by oooryan on 2011-11-13
Let me get this right....you're saying if i use ad blocker to block youtube ads, it will trick chrome and firefox into thinking its a video with no ads therefore allowing me to watch it in html5? cause it didn't work, it still plays videos with ads in flash...and it still shows the ads....maybe im not configuring it right? is there a specific filter I should use?

and anyone have anything on the minitube bug i seem to have?

---

### Post by SeijiSensei on 2011-11-14
That's actually the opposite of what I was saying.  Commercial video sites will often not let the video play at all if you block ads.  Visit Hulu with full-bore ad-blocking enabled, and you'll get a billboard where the blocked ad should appear.  How do they know you're blocking ads?  Because your browser isn't requesting the required advertising objects.

I see many postings on these forums about problems playing advertiser-supported videos, where the poster thinks the problem has something to do with Linux.  Oftentimes the problem is that the person is region-blocked (outside the regions in which performance rights apply), or that he or she is blocking ads.  People who complain about videos that use Silverlight to impose digital-rights-management restrictions are another example.

All this stems from the "it's all free (or should be free)" mentality that's pretty widespread among Internet users.  Monetization of the Internet continues apace and is not going to stop any time in my lifetime, and probably not in yours either.

---

