---
title: "firefox error 503"
date: 2010-07-25
forum: General Help
---

### Post by sdowney717 on 2010-07-25
clicking here
 [http://forum.woodenboat.com/showthread.php?117746-Do-you-agree-with-the-Supreme-Court](http://forum.woodenboat.com/showthread.php?117746-Do-you-agree-with-the-Supreme-Court)

gives me this here
503 Service Unavailable
The server is temporarily busy, try again later! Powered By LiteSpeed Web Server
LiteSpeed Technologies is not responsible for administration and contents of this web site!

In fact clicking most links in that forum gives me the error on firefox 3.6.
Chrome works, firefox gives me the error.
So anyhow its a pain, what do you think is happening?

---

### Post by lovinglinux on 2010-07-25
Clear the browser cache.

---

### Post by sdowney717 on 2010-07-25
thanks,what is easiest way to do that?
I ended up opening in a new profile and it worked.

---

### Post by sdowney717 on 2010-07-25
just tried it this way and still get 503

---

### Post by lovinglinux on 2010-07-25
> **sdowney717 said:**
> just tried it this way and still get 503

Is it working with a new profile?

---

### Post by sdowney717 on 2010-07-26
yes, it is fine with a new profile

---

### Post by lovinglinux on 2010-07-26
> **sdowney717 said:**
> yes, it is fine with a new profile

Good. That was the next step I would recommend. For future reference see: 

[[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)

[Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by jerenept on 2010-07-26
Your proxy settings may be incorrect. Ensure they are correct.

---

### Post by sdowney717 on 2010-07-26
here is what it looks like
only does it on that site, really strange.

---

### Post by eric_1982 on 2010-07-26
Does it seem to be random on every website page, were it work on minute and break the next? Can you tell me a little bit about your network setup
Example: DSL Modem > Linksys router > computer
Do you connect through wireless or over an Ethernet cable?

when you to do a ping on a site that is giving you trouble do you get the same completed packets every time?


I had a issue very similar a while back,It ended up being a DNS issue. I was being handed one valid DNS server name and one that was not valid. I would check is your DNS settings. You could even try testing it by statically setting your dns to google's open DNS. 8.8.8.8 and 8.8.4.4

---

### Post by sdowney717 on 2010-07-27
thing is the problem is only on that site
If I I click on a forum link to read an actual post, then I get the error.
All the main forum headers are readable,

The problem goes away If I right click and select 'open link in new profile'
So I dont think it is anything to do with networking.
The problem does not exist in Chrome browser.
I think the main default firefox profile is messed up in some way.

---

### Post by sdowney717 on 2010-07-27
see the screen shot showing a main header page working on the site
then I click a link to read a forum thread and I get the error

---

### Post by sdowney717 on 2010-07-27
screenshot in chrome showing I can click on a thread and read it.
If I open the thread in a new profile I can read it in firefox

---

### Post by lovinglinux on 2010-07-27
Is probably some settings. For instance some launchpad.net features don't work properly of you don't have the default value for **network.http.sendRefererHeader**.

---

