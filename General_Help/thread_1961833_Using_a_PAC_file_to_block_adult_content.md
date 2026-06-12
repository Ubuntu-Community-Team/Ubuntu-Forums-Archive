---
title: "Using a PAC file to block adult content"
date: 2012-04-19
forum: General Help
---

### Post by ki4jgt on 2012-04-19
I read somewhere that you could block adult conent with a PAC file through the http proxy. The basic idea would be to redirect the browser to a dead proxy when URLs contained certain phrases. I know this would be a faulty system but it beats having nothing at all.

---

### Post by for.i.am.root on 2012-04-19
Hi

I've never used a PAC file, however, I have used /etc/hosts to kill certain sites. It does support wild cards, however, not keywords.

I'm sure there is a kid friendly hosts file somewhere though.

My google-fu can use some practice. I'll let you know what I find.

[http://hostsfile.org/pac.html](http://hostsfile.org/pac.html)

Instructions are in the 7-zip file on the left side.

Interestingly enough it only blocks url's containing the keywords, not  all sites. Some sites don't use "naughty" words in their URL.

---

### Post by ki4jgt on 2012-04-20
> **for.i.am.root said:**
> Hi

I've never used a PAC file, however, I have used /etc/hosts to kill certain sites. It does support wild cards, however, not keywords.

I'm sure there is a kid friendly hosts file somewhere though.

My google-fu can use some practice. I'll let you know what I find.

[http://hostsfile.org/pac.html](http://hostsfile.org/pac.html)

Instructions are in the 7-zip file on the left side.

Interestingly enough it only blocks url's containing the keywords, not  all sites. Some sites don't use "naughty" words in their URL.

I wouldn't know of any other free way to go about it in Linux. All the safe watching services cost an arm and a leg. There should be a FREE solution somewhere LOL but this was an idea I read up on a while back and had hoped not to have to use it as it's the most flawed system I know of.

---

### Post by for.i.am.root on 2012-04-20
I agree. I'll start digging onto it soon enough. My 6 year old is always bugging me about the computer so I will be building her a rig soon enough.

I'll let you know what I find.

---

### Post by for.i.am.root on 2012-04-20
If you want to configure a proxy server Content Security 2.0 looks promising. Home user is free.

So does an OpenDNS account, which is advertised as free but requires a stupid Windows app for updating the IP. I'm pretty sure you could use a redirect and dyndns to update your wan ip.

I will probably pick up an old P4 rig and use it as a firewall / proxy server and use Content Security. Looks very promising.

Sorry. Forgot links

Content Security 2.0
[http://www.quintolabs.com/subscriptions.php](http://www.quintolabs.com/subscriptions.php)

OpenDNS
[ http://www.opendns.com/home-solutions/parental-controls/]( http://www.opendns.com/home-solutions/parental-controls/)

---

