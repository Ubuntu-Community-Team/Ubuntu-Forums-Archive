---
title: "Firefox and data collection"
date: 2010-09-03
forum: General Help
---

### Post by HuaiDan on 2010-09-03
I live in China, where a number of websites, including facebook, are blocked. This alone isn't an issue, as I don't use facebook. 
The problem arises when facebook (presumably) tries to collect information on my browsing habits. Instead of loading the desired page, firefox hangs up on googleapis.com or facebook.net, and waits several minutes. While this happens, I can see "Waiting for facebook.net..." or "connecting to googleapis.com" in the lower left panel of the browser. I can't view the page until firefox times out on these sites, which is really getting annoying and wasting a lot of my time.

How do I get the page I want to view to load without waiting for firefox to time out on these sites that I want nothing to do with?


Edit: I don't use NoScript or ABP, these plugins cause firefox to crash constantly, which is even more annoying.

---

### Post by lovinglinux on 2010-09-03
You can use [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/9609/"), which specifically block web bug trackers, like Google Analytics and such.

You could also use [BlockSite]("https://addons.mozilla.org/en-US/firefox/addon/3145/"), which requires to add those sites to the list.

Another option would be to use a firewall IP blocker like [Moblock]("http://moblock-deb.sourceforge.net/") or [Iplist]("http://iplist.sourceforge.net/") or add the IPs to [hosts file]("http://www.google.com/search?q=hosts+files+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0").

I would also disable the option to block web forgeries and attack sites in Firefox's Security preferences, since they can slow down Firefox when querying Google servers.

---

### Post by HuaiDan on 2010-09-04
Thanks a million, Ghostery is exactly what I needed. I'll give it a run and see how stable it is. No crashes yet.

---

### Post by lovinglinux on 2010-09-04
> **HuaiDan said:**
> Thanks a million, Ghostery is exactly what I needed. I'll give it a run and see how stable it is. No crashes yet.

You are welcome. Let me know if you have additional problems.

---

