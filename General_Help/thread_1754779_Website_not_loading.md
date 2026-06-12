---
title: "Website not loading"
date: 2011-05-10
forum: General Help
---

### Post by tilii on 2011-05-10
[SIZE=1]I currently have 3 browsers installed, Firefox 3.6.17, Epiphany 2.30.2 and Midori 0.2.2.

A few updates ago (not sure quite when) Firefox refused to load googlemail.com. However I could access it in Epiphany so that wasn't a major issue. But now *none *of them will load paypal.co.uk. Yet I have used all of them at one point or another to access the site on a regular basis.

Firefox gives an error of "Connection was interrupted while page was loading"
Epiphany gives an error of "Connection terminated unexpectedly" or just hangs.
Midori just hangs with the progress bar about half way.

I use Firefox Portable 3.6.12 in windows and that loads fine.

Can anyone offer any hints as to why this has suddenly occurred? I tend to enjoy a simple set up and don't fiddle with settings much so I am just left wondering.

Thanks in advance

EDIT: This is what is in the Firefox error console...
[www.paypal.com]("http://www.paypal.com") : server does not support RFC 5746, see CVE-2009-3555

EDIT (again) Firefox error console message appears for other sites too even if I can access them so I guess it's not related after all. Sorry.
[/SIZE]

---

### Post by jerrrys on 2011-05-11
create a new user on your system and then (while your logged in as new user) try firefox. did it work?

---

### Post by neu5eeCh on 2011-05-11
The usual response in these situations is to boot up Firefox in safe mode - such that no add-ons (if any) are enabled. If you can access the site, then one of your add-ons is causing the problem. The next step, if that's the case, is to disable all your add-ons, then re-enable them one by one. & etc...

You're also using an older version of FF. To find out if this is the problem, have you tried using a newer version? If you prefer FF 3.x. you can install FF4 in it's own directory. 

See [this site]("http://hogueweb.com/2011/02/09/running-multiple-versions-of-firefox-simultaneously/") for guidance.

---

### Post by tilii on 2011-05-11
Thanks for the replies jerrrys and VTPoet but no luck on either suggestion I'm afraid.

Given that I can access googlemail.com with Epiphany at the moment is there any way to compare what the browsers are doing when they are loading the pages?

---

### Post by neu5eeCh on 2011-05-11
So, trying Firefox 4 didn't work? Or a different profile?

As to your question: No, I personally don't know of a way to compare what the browsers doing. However, if all of your browsers are refusing to load a given page, then this doesn't sound like a browser issue. Firewall? How are you connecting to the Internet? What kind of modem? If it's DSL, have you checked your firewall settings? Usually it's something like 192.168.1.1 or 0.1.

**Edit:** A while back, I couldn't receive PGP Keys. Turns out, I had turned on my DSL Firewall and the Firewall was preventing authentication.

---

### Post by tilii on 2011-05-11
Ah... apologies... just to clarify...

Logging in as a new user didn't make a difference and neither did *safe mode*.

No firewall in Linux. I use a ZTE M112 dongle on the 3 network so it's the same connections in Windows other than a firewall used there and as said FF 3.6.12 works great there.

I can't say for certain that the googlemail issue started at the FF 3.6.13 updates but I have had to use Epiphany for that for a while now and now that I can't access paypal on the Linux side it's time to look into matters.

At least I've got Windows as a last resort.

---

