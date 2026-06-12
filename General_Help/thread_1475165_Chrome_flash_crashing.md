---
title: "Chrome flash crashing"
date: 2010-05-06
forum: General Help
---

### Post by brad1138 on 2010-05-06
Ever since todays update, which included a Chrome update, flash apps have been crashing all over the place. I keep getting a banner across the top telling me that it has crashed on this page. Anyone else seeing this?

---

### Post by TheSixthPandava on 2010-05-07
Yes, me too, exactly the same problem; ever since chrome update that happened yesterday, or two days ago, I can't remember precisely, flash is crashing in chrome.

Don't know what to do...

EDIT: I'm on Hardy, and since you're on Lucid, the problem isn't in version.

---

### Post by TheSixthPandava on 2010-05-07
up

---

### Post by kostkon on 2010-05-07
The newest version of Chrome comes with its own Flash. Thus, you'll need to go to
```
about:plugins
```
and disable the external flash plugin and then restart Chrome, if you want.

---

### Post by brad1138 on 2010-05-07
> **kostkon said:**
> The newest version of Chrome comes with its own Flash. Thus, you'll need to go to
```
about:plugins
```
and disable the external flash plugin and then restart Chrome, if you want.

I don't see a Chrome flash plugin, but I do have 2 Flash plugins. Shockwave Flash 10.1 r53 & Shockwave Flash 10.0 r45, Could they be conflicting?

---

### Post by kostkon on 2010-05-08
> **brad1138 said:**
> I don't see a Chrome flash plugin, but I do have 2 Flash plugins. Shockwave Flash 10.1 r53 & Shockwave Flash 10.0 r45, Could they be conflicting?
Yes, try disabling the 10.0 r45 one.

---

### Post by tora201 on 2010-05-08
Did not solve the problem....

---

### Post by TheSixthPandava on 2010-05-09
I did that; we'll see if it's gonna work; flash is crashing but not constantly.

---

### Post by learning_ on 2010-05-30
i am having the same problem, only i have one flash plugin installed. just the 10.0 r45

apparently the java isnt enabled either, yet i have downloaded it. but i cannot get it to become available to be activated on chrome..

---

### Post by justinmiller87 on 2010-06-28
Getting the same issue. Google search says it's Chrome on Linux in general. We're not just limited to it here on Ubuntu. I use the same Flash plugin for both Chrome and FF and no crashes occur in FF. People say the same about other browsers as well. Chrome only, so it has to be a Chrome issue, not a Flash issue for once.

---

### Post by BrendanM on 2010-07-13
For what it's worth, I'm having the same problem. I'm running Chromium, not the Google-branded Chrome, and my details are as follows:

```
Chromium 5.0.375.86 (49890) Ubuntu 10.04
```

```
Shockwave Flash
Description:	Shockwave Flash 10.1 r53
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
```

The symptoms of the crash are always the same. It frequently occurs on Pandora (though it happens on other sites), and it will simply stop playing music or responding to any mouse clicks. Reloading the tab immediately produces the ["Sad plugin face"]("http://northernfeel.files.wordpress.com/2008/09/flashcrash.gif") and the crashed plugin banner at the top. Reloading the tab a second time brings the player back and it works fine until the next time it crashes. I'd say it dies a couple times an hour during normal use of Pandora+other web browsing.

I haven't bothered to dig into this that much, because reloading the tabs is only mildly annoying, and it works fine in Firefox. I'm assuming it's a Chromium and/or Adobe bug, not an Ubuntu problem. If anyone knows the proper place to file a bug report, I would do so.

---

### Post by s7726 on 2010-07-21
Same problem again noticing it mostly with Pandora, although I've noticed it with grooveshark as well.

Chrome 6.0.466.0 dev

Flash 10.0 r32

---

### Post by killabee44 on 2011-03-09
Im also having this problem. If anyone knows a fix, please let us know. Thanks.

---

### Post by ianmaciel on 2011-03-11
I'm having the same problem, and I can't fix it.

I tried the plugin thing (they have said here) and also tried to remove completely Chrome and Adobe Flash (removing them also from user's folder) and reinstalling it, but the problem keep happening. 

I don't know more what to do...  was so good when chrome was working fine...

---

### Post by thuyuk on 2011-03-13
> **kostkon said:**
> Yes, try disabling the 10.0 r45 one.

It solved the problem! thanks! But, I also disabled one of the correct plugings, which one were in /opt/google/chrome/plugins and the other ~/.mozilla/plugins, just to be make sure.

---

### Post by runeh76 on 2011-03-13
Chromium 11.0.687.0 (76345) Ubuntu 10.10

Shockwave Flash
10.2 r152
/usr/lib/flashplugin-installer/libflashplayer.so

No problems

---

### Post by jw1949 on 2011-03-14
I re-installed Shockwave Flash from Synaptic and copied over the libflashplayer.so from another system - now it works !! tho' not sure why.

THX.

Chrome - 10.0.648.127  (10.10)
Flash - 10.1 r999

---

