---
title: "ebay and msn login problems"
date: 2011-07-27
forum: General Help
---

### Post by shadow of the locust on 2011-07-27
Following a recent update in 10.04, I have lost the ability to sign in to ebay via firefox.  My dad has also suddenly experienced this problem after updating 10.10 on his laptop.

The sign in screen appears and we can type in both username and password, but the screen then hangs with no progress bar appearing and eventually suggests that a dll file is being downloaded from signin.ebay.

I also suddenly acquired a problem with signing in to msn through pidgin.  It says that I am signed in in another location.  I made sure that I had logged out everywhere else and tried again, but still got the same error.  I also checked with empathy but got the same result.

In an attempt to fix the problem, I restarted my router, cleared the cache in firefox and restarted the computer, but the same thing happened.

Neither of the problems occur when I try ebay or msn through pidgin in windows 7.

Any suggestions or possible fixes would be greatly appreciated.

Thanks.

---

### Post by xx58 on 2011-07-29
:rolleyes: When I sign in on eBay, then it is hangs like no connections,,,, so I just highlight everything after [www.ebay.com](www.ebay.com) and deleting, then click reload current page and then I am sign in on ebay.

Welcome eBay sign in:
ID    - XXXXXXXX
Password - xxxxxxx
Click - sign in

[COLOR=Blue]coming next: [/COLOR]http://my.ebay.com/ws/eBayISAPI.dll?MigrateVisitor&PageType=1883&hc=1&hm=v%7F.rp*a6gfa%3C3&hc=2&hm=v%7F.rp*a0d0a4b&hc=2&hm=v%7F.rp*g3%605a27&hc=2&hm=v%7F.rp*4gd771c&hc=2&hm=v%7F.rp*%60%3C%3Fee4b&hc=2&hm=v%7F.rp*%3Adbd%3B1%3E&hc=2&hm=v%7F.rp*0f03%600d&hc=2&hm=v%7F.rp*g252%6066&hc=2&hm=v%7F.rp*%60%3C%3Fee4b&hc=2&hm=v%7F.rp*267%3Eb%3D7
DELETING: everything after:  [http://my.ebay.com](http://my.ebay.com)
and then click
reload current page
and VOILA
[COLOR=Red]you are - sign in and in your eBay page.

[/COLOR]_[COLOR=Blue]NEVER MIND:[/COLOR]_

The page isn't redirecting properly
Firefox has detected that the server is redirecting the request for this address in a way that will never complete.                                                                                      This problem can sometimes be caused by disabling or refusing to accept
    cookies.

---

### Post by shadow of the locust on 2011-07-31
I have progressed slightly with this problem.

I set the router back to factory settings and still had problems with ebay uk and msn sign in.

To test if it was a router problem, I tried another router and everything started to work.

Does anyone know why the old router would suddenly cause a problem with a small selection of websites and programs but otherwise seem to function as normal?  No settings were changed before the problems started.

I would continue to use it if I could get it working normally again.

---

### Post by shadow of the locust on 2011-07-31
Having spent a few hours searching I have finally got everything working again.

I have recently switched providers to talk talk and I discovered on a site that the mtu setting should be 1400.

Changing my router settings fixed the problem.

---

