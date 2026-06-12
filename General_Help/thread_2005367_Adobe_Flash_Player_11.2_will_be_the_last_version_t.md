---
title: "Adobe Flash Player 11.2 will be the last version to target Linux"
date: 2012-06-17
forum: General Help
---

### Post by Silvernail on 2012-06-17
On this website ```
http://get.adobe.com/flashplayer/?no_redirect
```

Have you seen this statement"
> 
NOTE: Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. Adobe will continue to provide security backports to Flash Player 11.2 for Linux.


My question is how will this affect me?

---

### Post by blackbird34 on 2012-06-17
AFAIK In Firefox, each time you install Flash  in any way (repositories), it'll still be 11.2.
On the other hand, you can get subsequent versions inside Google Chrome, they have a special plugin system and a special partnership with Adobe.

[https://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](https://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

[http://www.geek.com/articles/news/adobe-makes-flash-for-linux-a-chrome-exclusive-20120222/](http://www.geek.com/articles/news/adobe-makes-flash-for-linux-a-chrome-exclusive-20120222/)

---

### Post by unimatrix on 2012-08-03
It means you will not be able to use websites that require the latest Flash anymore. Except in Chrome, fortunately.

---

### Post by Uikri on 2012-08-04
> **unimatrix said:**
> It means you will not be able to use websites that require the latest Flash anymore. Except in Chrome, fortunately.

Why the hell would they do that?

---

### Post by argoz17 on 2012-08-04
I'm assuming that this means at some point Google Crome would have to ship as Ubuntu's default browser, there would be no sense in having a pre installed browser that supported almost no current websites.

---

### Post by pavelchjen on 2012-08-06
ShokwaveFlash will still be afalable, know as gnash.
But still we may face some incompatibilities issues.
Right now it works for me. 
Also sites like youtube produce wrorkaround for firefox 4,  you can play videos on 12.04 without installing any flash player.
[http://www.youtube.com/html5/](http://www.youtube.com/html5/)

---

### Post by SeijiSensei on 2012-08-06
> **Uikri said:**
> Why the hell would they do that?

Because they don't want to spend money supporting a platform like Linux with a very small market share.  Why else?

> **pavelchjen said:**
> ShokwaveFlash will still be afalable, know as gnash.

Gnash is not a solution for streaming from commercial sites that employ the DRM features in Flashplayer.  [Amazon Instant Video]("http://ubuntuforums.org/showthread.php?t=2037242") already has compatbility problems on Linux and requires the installation of the deprecated HAL system to work.  According to Amazon they now expect to find version 11.3 of Flash; Linux will never have a version beyond 11.2.

> **unimatrix said:**
> It means you will not be able to use websites that require the latest Flash anymore. Except in Chrome, fortunately.

And for those of us who don't want our browsers telling Google about every little detail of our browsing histories?  Is there a solution that works with Chromium as well?

---

### Post by dcstar on 2012-08-08
> **unimatrix said:**
> It means you will not be able to use websites that require the latest Flash anymore. Except in Chrome, fortunately.

The "latest Flash" is basically an ongoing race to keep fixing the massive security holes that keep getting discovered in (usually Windows) Flash.

I haven't seem too many web sites requiring the "latest" Flash to actually play anything.

---

### Post by vexorian on 2012-08-08
> **SeijiSensei said:**
> Because they don't want to spend money supporting a platform like Linux with a very small market share.  Why else?

They have been supporting Linux for a while now. And we now have more market share.

The real reason is that google gave them the perfect excuse. Google designed their new plugin API that allows plugins to be cross platform. When flash targets this plugin API they cover android and Linux/GNU systems in one-shot, so they are saving a lot of money.

> 
Gnash is not a solution for streaming from commercial sites that employ the DRM features in Flashplayer. 
Is this a good or bad thing?

> And for those of us who don't want our browsers telling Google about every little detail of our browsing histories?  Is there a solution that works with Chromium as well?

The way I am reading this, the chrome flash player plugin will work in any browser implementing PEPPER. At this moment that means chrome and chromium. But if it becomes an important deal, then mozilla and opera will probably be motivated to implement Pepper. At first mozilla didn't find the point in implementing Pepper, but that was because there were no plugins that *only* worked in Pepper. But if getting new flash becomes an issue that forces other-wise firefox-liking users to move to chrom(e|ium) then mozilla will dedicate all time on it.

---

### Post by kurt18947 on 2012-08-08
> The way I am  reading this, the chrome flash player plugin will work in any browser  implementing PEPPER. At this moment that means chrome and chromium. But  if it becomes an important deal, then mozilla and opera will probably be  motivated to implement Pepper. At first mozilla didn't find the point  in implementing Pepper, but that was because there were no plugins that *only*  worked in Pepper. But if getting new flash becomes an issue that forces  other-wise firefox-liking users to move to chrom(e|ium) then mozilla  will dedicate all time on it.

Does Pepper work in Chromium?  I thought it was Chrome only but I'm not  well versed.  I agree that if flash versions >11.2 become important,  other browsers will implement Pepper.  

As I understand it, the problem with moving to HTML5 for Amazon video, Netflix etc. is that there is no way to implement DRM (digital rights management) with HTML5 and movie studios etc. won't make their content available without DRM.   So it seems that until that issue is solved, flash or (worse) Silverlight will still be used.

---

### Post by SeijiSensei on 2012-08-08
> **vexorian said:**
> They have been supporting Linux for a while now. And we now have more market share.
Perhaps, but not enough it appears.  More market share in the case of Linux is at most a percentage point or maybe two.  Adobe doesn't really care about the end-user part of Flash anyway since they give it away.  For them, it's always about the developer tools which is where they make their money.  Development tools for Flash would be useless if Flash wasn't supported on Windows, but on Linux?  Not enough "there" there.

> Is this a good or bad thing?
Both.  Pragmatically, I want the Linux platform to work with DRM-encumbered content like that found on sites like Amazon Instant Video.  Politically I'd prefer a world without DRM, but that's a pipe dream.  The content industries won't let unencumbered material be distributed by their licensed partners, so Linux needs to work with DRM systems.  At least Flash works on more platforms than Silverlight does.  Support for Silverlight seems to have collapsed in the past couple of years, though, since Flash provides DRM solutions that work across platforms.

> **kurt18947 said:**
> As I understand it, the problem with moving to HTML5 for Amazon video, Netflix etc. is that there is no way to implement DRM (digital rights management) with HTML5 and movie studios etc. won't make their content available without DRM.
I *could* see proprietary binary-only libraries to provide DRM services on platforms like Linux, but financially there is little justification for investing the resources to develop one.  In particular it would have to work with programming from all content providers.  I don't see anyone caring enough about Linux to develop a widely-supported DRM solution for the platform.  Take Netflix, for instance.  They have hinted at supporting Linux for a couple of years now but have never done so.  They could develop a proprietary binary-only player for Netflix content on Linux, but ultimately it's just not worth it.

---

### Post by kurt18947 on 2012-08-08
> I *could*  see proprietary binary-only libraries to provide DRM services on  platforms like Linux, but financially there is little justification for  investing the resources to develop one.  In particular it would have to  work with programming from all content providers.  I don't see anyone  caring enough about Linux to develop a widely-supported DRM solution for  the platform.  Take Netflix, for instance.  They have hinted at  supporting Linux for a couple of years now but have never done so.  They  could develop a proprietary binary-only player for Netflix content on  Linux, but ultimately it's just not worth it. 		                   		  		  		  		  		 		 			 				 				* 					 						Last edited by SeijiSensei; 1 Hour Ago at 05:04 PM.. 					 					 				*


In my non IT pro mind, this might be the best justification for something like Pepper.  It'd be less expensive and therefore more nearly cost-effective to support Linux for  companies like Netflix and Amazon video if they could develop *one* binary or whatever that would work on all distros, or at least all currently supported versions of the major players and wasn't a support nightmare.  One of the complaints I've seen from the major commercial companies about supporting linux is that it's too fragmented.

---

### Post by jwbrase on 2012-08-08
> **kurt18947 said:**
> Does Pepper work in Chromium?  I thought it was Chrome only but I'm not  well versed.  I agree that if flash versions >11.2 become important,  other browsers will implement Pepper.  

One article, though, implied that Adobe is only offering a delivery channel for the Pepper plugin through Chrome (which I take to mean they're only making it available through Chrome's internal plugin manager and not to Linux distros to be put into repositories), and that it wouldn't be available even to browsers that did implement Pepper.

> 
As I understand it, the problem with moving to HTML5 for Amazon video, Netflix etc. is that there is no way to implement DRM (digital rights management) with HTML5 and movie studios etc. won't make their content available without DRM.

To which I say "[content industry delenda est]("http://en.wikipedia.org/wiki/Carthago_delenda_est")".

I'm generally of the opinion that the content industry does more harm than good to society to begin with, and when you add DRM into the picture, the sequence of events "we stop buying their stuff, they shrivel up and go bankrupt" looks pretty good.

---

### Post by vexorian on 2012-08-09
> One article, though, implied that Adobe is only offering a delivery channel for the Pepper plugin through Chrome (which I take to mean they're only making it available through Chrome's internal plugin manager and not to Linux distros to be put into repositories), and that it wouldn't be available even to browsers that did implement Pepper.
 Things are not very clear yet. 

I just assumed it is not chrome-exclusive but pepper-exclusive, because otherwise it would have been a strange move for Google to make. Google need chromium to give legitimacy to chrome. And they would also love to make other browsers implement Pepper. So it made sense to me that they made the deal with flash as part of a strategy to make other browsers use pepper. But if it is really chrome exclusive, then I can't really understand google's motivation behind this.

Edit: I'd say they are at least working to make pepper flash work in chromium: [http://code.google.com/p/chromium/issues/detail?id=140506](http://code.google.com/p/chromium/issues/detail?id=140506)

---

### Post by keithgreysr on 2012-09-16
> **jwbrase said:**
> One article, though, implied that Adobe is only offering a delivery channel for the Pepper plugin through Chrome (which I take to mean they're only making it available through Chrome's internal plugin manager and not to Linux distros to be put into repositories), and that it wouldn't be available even to browsers that did implement Pepper.



To which I say "[content industry delenda est]("http://en.wikipedia.org/wiki/Carthago_delenda_est")".

I'm generally of the opinion that the content industry does more harm than good to society to begin with, and when you add DRM into the picture, the sequence of events "we stop buying their stuff, they shrivel up and go bankrupt" looks pretty good.

Spot on! The more the "content industry" tries to lock down EVERYTHING, the more inclined I am to grab one of the 300 VHS tapes or 200 DVDs or 2000 books that I *OWN* and watch/read that then deal with their BS online...

---

### Post by ubuntu27 on 2012-09-16
> **kurt18947 said:**
> Does Pepper work in Chromium?  I thought it was Chrome only but I'm not  well versed.  I agree that if flash versions >11.2 become important,  other browsers will implement Pepper 

Good news: 

[How To Make Chromium Use Flash Player `Pepper` From Google Chrome]("http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html")

---

### Post by vexorian on 2012-09-16
> **ubuntu27 said:**
> Good news: 

[How To Make Chromium Use Flash Player `Pepper` From Google Chrome]("http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html")
Terrible monopolistic news.

Needing to install google chrome before being able to use flash in another browser. This is a market grab by all looks.

---

### Post by siafulinux on 2013-06-28
I would rather use Firefox through Wine which seems to be working just fine and installed Flash 11.7 without any problems. It's not ideal but it works.

---

### Post by SurfaceUnits on 2013-06-29
Adobe Flash Meets Its End
It's been clear for a few years now that  unless mobile Flash's performance and reliability improved, it was a  goner; that day has now come, and soon, desktop Flash will soon follow.
November 9, 2011 11:13am EST

In  the eternal battle for Web supremacy, one of the major warriors just  laid down its weapons. Adobe confirmed this morning that it will cease  all development of mobile versions of Flash. That means that Android,  BlackBerry OS, and other devices that had touted Flash capability as one  of their key selling points will soon no longer matter.

Web  developers are already moving away from Flash to HTML5. YouTube has an  HTML5 mode (albeit in beta). HTML5 doesn't do as much as Flash on the  programming side, but it's getting there. Besides, developers want their  sites to work on the iPhone and iPad&#8212;which brings us to Apple.

With  Flash gone on the mobile side, it's likely that we'll begin to see it  disappear on the desktop as well. It's the same conundrum developers  always face: how many platforms do you want to run your product on, with  all the extra time, money, QA, employee skills, training, and technical  support that comes with it? If you can get what you need done with  HTML5, which current browsers support out of the box, do you want to be  dependent on external plug-in installs that you have no control over?

Flash  served its purpose for a long time. It brought us a more powerful Web,  and helped shift it from its hypertext-based roots to something far more  interactive and useful, beginning as early as the late 1990s. And now,  Flash's time has officially passed&#8212;on mobile devices and otherwise.

[http://www.pcmag.com/article2/0,2817,2396094,00.asp](http://www.pcmag.com/article2/0,2817,2396094,00.asp)

Old news,,,yawn

---

### Post by prodigy_ on 2013-06-29
> **vexorian said:**
> Terrible monopolistic news.

Needing to install google chrome before being able to use flash in another browser. This is a market grab by all looks.
If I understand correctly you only need one library. So you can copy it to whatever location you want and then uninstall Chrome.

---

### Post by craig10x on 2013-06-29
It's bother to have to set up pepper in chromium...just use google chrome for pete sake and stop crying about google sending you targeted ads....you see ads anyway so why not have more relevant ones :D
If Firefox wants to stay up with the times they would need to adopt pepper also...I prefer Chrome myself as i think it's a better browser but you Firefox fans should pressure mozilla to get on the hopper and get it for you on their browser...

Chrome has the latest version and most up to date adobe flash you can obtain now on linux....

---

