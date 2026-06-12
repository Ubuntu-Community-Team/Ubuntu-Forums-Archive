---
title: "No more firefox - Adobe flash"
date: 2012-04-29
forum: General Help
---

### Post by Quarkrad on 2012-04-29
Apologies as this is not completely a Ubuntu issue - but I've installed Ubuntu on a number of family/friends machines and they are all happy; especially the ealderly members now surfing with Firefox.  This issue about Adobe no longer supporting flash on Linux - I can't quite get to the bottom of it.  Firefox seems to work OK using Flash at the moment - does this mean as some time we are going hve to migrate/change to Google Chrome?

---

### Post by kurt18947 on 2012-04-29
> **Quarkrad said:**
> Apologies as this is not completely a Ubuntu issue - but I've installed Ubuntu on a number of family/friends machines and they are all happy; especially the ealderly members now surfing with Firefox.  This issue about Adobe no longer supporting flash on Linux - I can't quite get to the bottom of it.  Firefox seems to work OK using Flash at the moment - does this mean as some time we are going hve to migrate/change to Google Chrome?

As i understand it, Firefox/Linux won't be able to install versions of Flash after the current one but security updates will be provided for 5 years.  Adobe and Google have come up with Pepper to install Flash on Linux but right now only Google's Chrome browser supports it.  As long as web sites don't require flash versions newer than 11.xxx to work properly, I'm not sure there's an immediate problem.  

I can sort of see Adobe's position in that Adobe seems to tolerate Linux, barely; they see no significant $$$ in it.  Having to support only Pepper means less hassle and expense for Adobe.  I guess we'll see how this shakes out down the road.  Flash is not exactly a hot and growing technology but doing much on the web without it is a pain for now.

---

### Post by lovinglinux on 2012-04-29
No need to apologize. This is a real issue that affect Ubuntu users directly.

Adobe has ended support for Flash on Linux and made a deal with Google, which will implement PepperFlash plugin on Chrome. Adobe will continue to provide security updates for 5 years to the current flash plugin, but won't be fixing bugs or implementing new features.

The main problem is that the current version of Flash has many issues, specially in regard to hardware acceleration. Adobe has been struggling to deal with that recently and even turned hardware acceleration off on some flash builds. Since they won't be fixing any bugs, this buggy version is what we will have to use forever.

Google is trying hard to force the adoption of NativeClient and Pepper API technologies that they develop, but none of the majors browser vendors, including Mozilla and Opera, will adopt it. They don't think such technologies are good for the web and they will introduce more problems than benefits. Instead, they are promoting open standards like HTML5. For instance, Google uses Pepper to provide PDF capabilities in Chrome, while Mozilla is implementing such feature using only HTML5 and Javascript. Now, because of this deal with Adobe, Google will be implementing flash using Pepper and Chrome will be the only browser on Linux to have an updated Flash plugin.

Some people argue that by the time flash stops working on Linux, it won't be relevant anymore, because it will be replaced by HTML5. Well, I disagree. I think we will have major problems with flash sooner than later and I doubt flash will be replaced by HTML5 in 5 years. After all Goolge, which is a major player in the browser and streaming markets, is not investing on flash to simply replace it with HTML5.

Anyway, we are already experiencing many issues with Flash. If things continue with this pace, soon we will have to move to Chrome if we want to continue to use Flash.

The development version of Chrome 64bit has PepperFlash already, but it is unusable. You need to disable it to watch flash videos on YouTube.

Here are some recommended readings:

[http://ubuntuforums.org/showthread.php?t=1949908](http://ubuntuforums.org/showthread.php?t=1949908)
[http://ubuntuforums.org/showthread.php?t=1965858](http://ubuntuforums.org/showthread.php?t=1965858)
[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by rg4w on 2012-04-29
> **lovinglinux said:**
> Some people argue that by the time flash stops working on Linux, it won't be relevant anymore, because it will be replaced by HTML5. Well, I disagree. I think we will have major problems with flash sooner than later and I doubt flash will be replaced by HTML5 in 5 years.
I give it 50/50 odds or better than Flash will be gone for everything but standalone games in that time frame.

Here's where we are now:
- No iOS device can run Flash at all
- OS X "Mountain Lion" won't have Flash pre-installed
- Microsoft would prefer everyone use their plugin
- Most Android systems don't have Flash enabled by default, requiring the user to click to play; bad news for advertisers
- HTML5 support is getting better and better across browsers every month
- Adobe's lackluster execution on Flash performance/efficiency is becoming increasingly self-evident

Given all this, I agree with Adobe:  they see the future of Flash being a platform to develop apps, with at best a limited and ever-smaller role on the Web.

---

