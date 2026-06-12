---
title: "Cookie failures in a different city?"
date: 2011-01-14
forum: General Help
---

### Post by dewdrop_world on 2011-01-14
Wondering if anybody has seen anything like this.
 
Back in Guangzhou, I wasn't having any problems with cookies. I could log into forum sites etc. with "automatically log me in" enabled, and the cookie would be set and my next access would be authenticated right away.
 
Now I'm on vacation in Zhuhai and:
 
- Some sites retain login cookies properly (like this one).
 
- Others keep me logged in while the browser is open, but don't persist the cookie after the browser is closed.
 
- One (my blog) will not let me login at all!
 
The last problem is Linux specific -- I tried on my Mac, no issue. I haven't tried the others on the Mac. I also tested both Firefox and Chrome in Linux, same behavior. That suggests a system issue rather than a browser bug.
 
It all leaves me asking, "What the...?" I mean, I haven't done anything in either browser to disable cookies.

The only other difference is that, since coming to ZH, I removed network manager and installed wicd to try to solve a [WiFi WPA authentication issue](http://ubuntuforums.org/showthread.php?t=1666722) against a DLink router (didn't help). But I can't imagine wicd would magically invalidate cookies? That seems plain crazy.


 Puzzled,
James

---

### Post by wilee-nilee on 2011-01-14
If your keeping cookies chances are you have long term cookies that are tracking you, on the web, you would have them anyway without the better privacy FF addon. If you have the passwords saved in FF I would have it not save cookies. A double click or the first symbol of the savedpassword will bring up the whole password to login.

Those longterm cookies come up as addware hits in a av scan in windows. They are not a good thing.
[http://www.ehow.com/facts_5185198_adware-tracking-cookies_.html](http://www.ehow.com/facts_5185198_adware-tracking-cookies_.html)

---

### Post by dewdrop_world on 2011-01-14
Okay, but I can't post on my blog from my Linux machine because it tells me "cookies are disabled" when I try to log in. Disabling cookies won't help me with that problem. :)


And actually, I checked the cookie list in Chrome and tracking cookies are being set anyway -- so this buggy behavior vis-à-vis "good" cookies is not helping my privacy... though I do appreciate the reminder to monitor cookies more carefully and set exceptions.


What I'm after here is to get my system to work here in Zhuhai the way that it does in Guangzhou or in the US. It makes no sense to me at all that I have full access to my blog from one city but only guest access from another city, and only on my Linux box.


James

---

### Post by no2498 on 2011-01-15
is it because your on a different sever 
sounds like a cache problem to me but im no guru

---

### Post by dewdrop_world on 2011-01-16
I don't quite understand. Which "different server" am I on? (Do you mean ISP?)


Also, it couldn't possibly be an ISP problem because there is no issue on my Mac. This problem is Ubuntu-specific, and only for my website and a couple of other phpBB forums.


The problem persists after clearing the browser cache and deleting cookies. What else could be cached? (Possibly something system-level, since multiple browsers are affected.)


Worst case now is that the Ubuntu experts will say "it's a b2evolution problem" and the b2evolution people will say it's an Ubuntu problem. Well, it's a problem somewhere.


I guess I should probably just let it go. I'm hoping, when I go back home a few weeks, that it will all be back to normal. But I don't know -- if some system setting changed behind my back, I could still be screwed at that point. Ubuntu is my primary OS and I really don't want to have to go to the Mac just to post on my blog.


James

---

