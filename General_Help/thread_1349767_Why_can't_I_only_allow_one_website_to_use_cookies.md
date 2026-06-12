---
title: "Why can't I only allow one website to use cookies?"
date: 2009-12-08
forum: General Help
---

### Post by sexyclient2 on 2009-12-08
Internet explorer allowes **websites,** not domains (google,) to either be allowed or denied the use of cookies -- why not any other browser?  I only want to check gmail in one tab, and use google search **separately**, not contribute to any profiling databases.

Does anyone know of a way to whitelist (or blacklist) individual websites (instead of their domains) thereby allowing (or disallowing) them to use cookies?  Does anyone know why only IE is ahead of the curve on this issue?

---

### Post by howefield on 2009-12-08
> **sexyclient2 said:**
> Does anyone know why only IE is ahead of the curve on this issue?

You are of course wrong about that. You merely need to learn how to drive your software.

Which browser are you using ?

---

### Post by sexyclient2 on 2009-12-08
Firefox 3.5.5 in ubuntu 9.10

---

### Post by sexyclient2 on 2009-12-08
solutions?

---

### Post by Clancy_s on 2009-12-08
I've never tried it since it's not something I want to do but try edit > options (or maybe called preferences, I'm not on my linux box atm), privacy, 

then deselect 'accept cookies from sites' and add those you do want to accept cookies from to the exceptions list.

---

### Post by sexyclient2 on 2009-12-08
> **Clancy_s said:**
> I've never tried it since it's not something I want to do but try edit > options (or maybe called preferences, I'm not on my linux box atm), privacy, 

then deselect 'accept cookies from sites' and add those you do want to accept cookies from to the exceptions list.

That only allows me to accept cookies from an entire domain (google.com, in the following example) but I just want a specific site on a domain (gmail.)  I'll use gmail as an example:

To to check my mail I only want to allow mail.google.com* (for accessing the mail) and [https://www.google.com/accounts/ServiceLogin?service=mail*](https://www.google.com/accounts/ServiceLogin?service=mail*) (for logging in to gmail.)  All of the cookie-handling methods for firefox, including the one you just described Clancey_s (and surprisingly also all of the plugins that I've found as well!) only allow you to block/allow cookies on a per-domain basis, rather than per-site (including domain.com/site/*, or google.com/accounts/* in our example.)

Internet explorer lets you, so why not firefox?  Why not chrome?

---

### Post by sexyclient2 on 2009-12-09
*bump

---

### Post by wilee-nilee on 2009-12-09
In firefix preferences-privacy you can set it to accept cookies from a specific site. I have mine set to accept cookies per session and to remove on closer of Firefox, no special sites saved

---

### Post by sexyclient2 on 2009-12-09
> **wilee-nilee said:**
> In firefix preferences-privacy you can set it to accept cookies from a specific site. I have mine set to accept cookies per session and to remove on closer of Firefox, no special sites saved
No, you can only allow or deny a **domain**, not a specific site like internet explorer allows you to do.  See the example in post # 6...

---

### Post by wilee-nilee on 2009-12-09
So your trying to avoid profiling, the method your trying to use will not do this, data is collected beyond cookies. This can be blocked in others ways to some extent, but IE does not give you any special protection in that you can use it the way you suggest.

If you want more privacy there are lots of threads on the forum about this.

---

### Post by sexyclient2 on 2009-12-09
Well, I haven't tested the feature in IE for myself, but you can allow/block cookies from trusted websites, and trusted websites, according to [these screenshots]("http://gisweb.hendersoncountync.org/GoMaps/Help/Internet_Explorer_7_Users_Make_GoMaps_a__Trusted_Site_.htm"), can be actual websites, not just domains...

What I'd ultimately like to do is be logged in to only one google service (gmail, for example) without being logged in to all the others, like docs or google's new "relevant" search.  That's it...

---

### Post by mkvnmtr on 2009-12-09
In Firefox I allow or disallow each cookie no matter where it comes from. It will also remember my choices. I believe some of my other browsers do the same.

---

### Post by sliketymo on 2009-12-09
What are you trying to hide from?Advertising?Use Adblock Pro, NoScript,Better Privacy,etc.

---

### Post by sexyclient2 on 2009-12-09
> **sliketymo said:**
> What are you trying to hide from?Advertising?Use Adblock Pro, NoScript,Better Privacy,etc.

You're providing a solution - thanks - but not to my problem.  I'm **very well** aware of those add-ons to firefox and what they do, thank you very much, but **none** of them actually do what I'd like done.  Maybe I'm being too ambiguous here?
> **sexyclient2 said:**
> What I'd ultimately like to do is be logged in to only one google service (gmail, for example) without being logged in to all the others... That's it...
This can be done quite easily in IE (the supposedly inferior browser) but I haven't yet found a way to do this in firefox, hence this thread.  Of all the extensions I've come across none of them actually allow you to circumvent the google cookie (for example) in any meaningful way.  To use gmail I have to allow **all** google's pages to access my cookies instead of much more simply (and privately) allowing only gmail (and google.com/accounts* for logging in of course) to access the cookie.

Maybe it can actually be done, though - hell it seems simple enough, though I'm no expert - hence this thread.

---

### Post by wilee-nilee on 2009-12-09
[http://www.scroogle.org/cgi-bin/scraper.htm](http://www.scroogle.org/cgi-bin/scraper.htm)
[http://www.ixquick.com/eng/](http://www.ixquick.com/eng/)

---

### Post by sexyclient2 on 2009-12-10
> **wilee-nilee said:**
> [http://www.scroogle.org/cgi-bin/scraper.htm](http://www.scroogle.org/cgi-bin/scraper.htm)
[http://www.ixquick.com/eng/](http://www.ixquick.com/eng/)
Thanks, but suggesting I go to different websites isn't as helpful as you may perceive it to be.  Doing so is tantamount to ignoring the problem instead solving it. It's like telling someone who wants to change their wallpaper to maximize their window -- absurd, yes?  Besides, I only ever used google.com and gmail as examples because they more clearly illustrate the problem I'm trying to solve.  I reiterate that the google services **are only xamples**, and just that.  

Once I'm able to selectively disallow cookies for an entire domain but allow cookies for specific sites within that domain - like Internet Explorer does - then I've reached my ultimate goal.  Anything else is uncivilized.

---

### Post by sexyclient2 on 2009-12-11
Addons, hacks, anything?  I can't believe there's NO way to do this in ANY browser other than Internet Explorer...

---

