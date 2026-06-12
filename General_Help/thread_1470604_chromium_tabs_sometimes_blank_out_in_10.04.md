---
title: "chromium tabs sometimes blank out in 10.04"
date: 2010-05-03
forum: General Help
---

### Post by derande on 2010-05-03
running Chromium 5.0.342.9 (43360) Ubuntu in most recent Lucid.
never had this issue in 9.10 but while using Chromium, occasionally if i'm running multiple tabs, i notice that the tabs are still there but all turn blank.
when i run my mouse cursor over the tabs and they repopulate with the webpage names.
this never causes a problem, just annoying because i have to mouse over them to see what tabs are which pages and obviously shouldn't happen.

anyone else ever notice this after a fresh upgrade to lucid and installing chromium from the ppa?

thx.

---

### Post by clhsharky on 2010-05-03
HI derande

I been using chromium in lucid since a3. I don't believe its Lucid, chromium has had maybe 3 glitches up to now. And yes I'm experiencing that glitch right now. It usually takes 1 or  2 days for them to resolve any problem. Chromium is still in testing and gets updated all most every day. You can use chrome if you want stable release. They have all way fixed it in the past.

Sharky

---

### Post by JimTaverna on 2010-05-03
Not quite. Same problem here in Chrome Dev 375.28. Started a few dev releases ago when I was using UNR 10.4 RC. Even the Beta 342 had this issue.

I've got Linux Mint 8 loaded. See what happens...

---

### Post by JoelJohnson on 2010-06-01
I'm using Chromium 5.0.342.9 (43360) Ubuntu. I'm using Ubuntu 10.04.  I have this problem every time a tab moves to a new domain (Like when I'm doing a Google search and I click on a result).

---

### Post by xfearxnxloathing on 2010-06-01
why dont you just use google chrome for linux?

---

### Post by JoelJohnson on 2010-06-01
What would be the difference? I know the difference between Chrome and Chromium, but I don't know how using Chrome over Chromium would fix a painting problem.

Chromium is already in the repos.

---

### Post by xfearxnxloathing on 2010-06-01
> **JoelJohnson said:**
> What would be the difference? I know the difference between Chrome and Chromium, but I don't know how using Chrome over Chromium would fix a painting problem.

Chromium is already in the repos.


less bugs...

---

### Post by JoelJohnson on 2010-06-01
> **xfearxnxloathing said:**
> less bugs...

Do they ... not use the same code base? I have a hard time believing that Chrome has less bugs than Chromium...

[http://www.google.com/support/forum/p/Chrome/thread?tid=380b7ffc5d845696&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=380b7ffc5d845696&hl=en)

---

### Post by xfearxnxloathing on 2010-06-01
> **JoelJohnson said:**
> Do they ... not use the same code base? I have a hard time believing that Chrome has less bugs than Chromium...

[http://www.google.com/support/forum/p/Chrome/thread?tid=380b7ffc5d845696&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=380b7ffc5d845696&hl=en)

chrome IS the stable version.  other than that, idk man.  why do developer or beta unless it appeals to you for a reason?

---

### Post by JoelJohnson on 2010-06-01
No, Chrome is the Google branded version of Chromium. Chromium is the code base of Chrome. For Chrome, Google simply adds extra features (such as the auto-updater in windows and some proprietary codecs for video and such). Other than that, there's no difference. The Chrome Beta build is the same as the Chromium Beta build. The Chrome Stable build is the same as the Chromium Beta build.

As for the topic at hand, I added Chromium's Beta repo and updated, and it appears the painting problem has been fixed.

EDIT: I lied... the painting problem continues to be a problem even in the beta build.

---

### Post by xfearxnxloathing on 2010-06-01
> **JoelJohnson said:**
> No, Chrome is the Google branded version of Chromium. Chromium is the code base of Chrome. For Chrome, Google simply adds extra features (such as the auto-updater in windows and some proprietary codecs for video and such). Other than that, there's no difference. The Chrome Beta build is the same as the Chromium Beta build. The Chrome Stable build is the same as the Chromium Beta build.

As for the topic at hand, I added Chromium's Beta repo and updated, and it appears the painting problem has been fixed.

EDIT: I lied... the painting problem continues to be a problem even in the beta build.

from your posted link above: Google Chrome is simply a "rebranding" of Chromium, but is a little more ready for public consumption.

> Stable: The, well, stable version of Chrome, which is [COLOR="Red"]absolutely ready for public consumption[/COLOR]. Updates about every 6 months.
Beta: Still [COLOR="Blue"]relatively stable[/COLOR], but you may see new, untested features in it. [COLOR="Red"]No guarantees[/COLOR]. Updates every few weeks (I think).
Dev: Think of it as the Beta version, except it's the boiling pot of new features/testing. Absolutely no guarantees.  Updates weekly.

just saying you could try it out, you can actually have both installed, i did before upgrading to the 64bit version of 10.04 LTS.

---

### Post by JoelJohnson on 2010-06-01
Installed Chrome. And it appears to draw fine. Which made me realize that I have a theme installed in Chromium so I disabled it, and it seem that it's drawing fine as well. I'll update here if I notice any more problems.

---

### Post by xfearxnxloathing on 2010-06-01
> **JoelJohnson said:**
> Installed Chrome. And it appears to draw fine. Which made me realize that I have a theme installed in Chromium so I disabled it, and it seem that it's drawing fine as well. I'll update here if I notice any more problems.

glad it seems to be fixed for you. what skin was it?

---

### Post by JoelJohnson on 2010-06-01
I was using the Ambiance Theme with System Titlebar:
[https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp](https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp)

Now I'm using the GTK+ Theme and System Titlebar

I have noticed though that the back/forward/refresh/home buttons seem to disappear now. But that's hardly as annoying.

---

### Post by xfearxnxloathing on 2010-06-01
> **JoelJohnson said:**
> I was using the Ambiance Theme with System Titlebar:
[https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp](https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp)

Now I'm using the GTK+ Theme and System Titlebar

I have noticed though that the back/forward/refresh/home buttons seem to disappear now. But that's hardly as annoying.

i use this and only because i like the looks of it, dont care for vista relation, it's just a skin.  
[http://stamga.deviantart.com/art/Aero-Theme-CRX-Version-1-5-144788434?q=boost:popular+google+chrome+theme&qo=15](http://stamga.deviantart.com/art/Aero-Theme-CRX-Version-1-5-144788434?q=boost:popular+google+chrome+theme&qo=15)

a few others you might like based on your skin picking.
[http://burnsplayguitar.deviantart.com/art/Sonetto-2-0-Google-Chrome-109177103?q=boost:popular+google+chrome+theme&qo=5](http://burnsplayguitar.deviantart.com/art/Sonetto-2-0-Google-Chrome-109177103?q=boost:popular+google+chrome+theme&qo=5)
[http://pigletiger.deviantart.com/art/ShinyWhite-for-Google-Chrome-146654686?q=boost:popular+google+chrome+theme&qo=3](http://pigletiger.deviantart.com/art/ShinyWhite-for-Google-Chrome-146654686?q=boost:popular+google+chrome+theme&qo=3)

---

