---
title: "Ad virus http://www.doublecklick.org"
date: 2012-04-17
forum: General Help
---

### Post by coolercooler on 2012-04-17
Hi all, I keep getting search engine or links redirect, and the redirect ad virus is doing my head in. I can't figure out what to do, every 2/3 searches I keep getting redirected to sites I don't want to be on or when I click a link sometimes I get [http://www.doublecklick.org/](http://www.doublecklick.org/) then redirect.

I thought maybe the system was infected, so did a complete reinstall with full HDD format then installed Ubuntu 10.04LTS, downloaded latest Firefox, still Google searches kept redirecting, Goggled for help and added this /etc/hosts file 
```
0.0.0.0 ad.au.doubleclick.net
0.0.0.0 ad.doubleclick.net 
0.0.0.0 http://www.doubleclick.org/
0.0.0.0 ad.doubleclick.org
0.0.0.0 http://www.doublecklick.org
0.0.0.0 doublecklick.org 
```

Still had same problem so thought maybe it's google so I changed search engine to Bing, I still get same redirect problem.

Now I think maybe it's my ISP TalkTalk but before I change them, it still could be Ubuntu or something is still infected on the system.  I don't know what to do.

Thanks for any help

---

### Post by sffvba[e0rt on 2012-04-17
Try chancing your DNS to something like Google's DNS and see if it stops. - [How to]("https://developers.google.com/speed/public-dns/").


404

---

### Post by westie457 on 2012-04-17
Hi try this.

Open Firefox in the browser-bar type in about:plugins.

In that page install 'noscript' and 'adblockplus'.

Restart Firefox and check if that helps.

---

### Post by winh8r on 2012-04-17
> **westie457 said:**
> Hi try this.

Open Firefox in the browser-bar type in about:plugins.

In that page install 'noscript' and 'adblockplus'.

Restart Firefox and check if that helps.

+1 to this advice and I would add Ghostery to the addons that you select and have it block all the trackers too.

(You will be amazed at how many trackers and data gathering applications there are on some sites)


Hope this helps

---

### Post by coolercooler on 2012-04-17
> **westie457 said:**
> Hi try this.

Open Firefox in the browser-bar type in about:plugins.

In that page install 'noscript' and 'adblockplus'.

Restart Firefox and check if that helps.

Thanks all, I didn't mention in my original post but I have already added adblock plus 2.0.3 but it didn't help.

However I've now added the Google's DNS server and add noscript plugin, lets see what happens.

---

### Post by coolercooler on 2012-04-20
Update:  It seems to worked so far I've not had the pop-ups on the ubuntu machine with script blocked and Google dns server, however my android tablet also gets redirected.

It would be better to know whats cause of this and deal with it directly to get it rid.

Thanks to all

---

