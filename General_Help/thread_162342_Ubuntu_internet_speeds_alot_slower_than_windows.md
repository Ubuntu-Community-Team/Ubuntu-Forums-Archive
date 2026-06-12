---
title: "Ubuntu internet speeds alot slower than windows"
date: 2006-04-18
forum: General Help
---

### Post by njzillest on 2006-04-18
why is my ubuntu internet speeds alot slower than windows? 


im using broadband cable (optimum) and i connect through wire. 

is there a way to speed it up?? I have to wait forever when i open a site...

thanks,
Adel

---

### Post by 5-HT on 2006-04-18
Are you referring to browsing only?
Here's a link from the wiki that may be of help: [Firefox Tips and Tricks]("https://wiki.ubuntu.com/FirefoxTipsAndTricks")

In particular, IPv6 seems to be a lag culprit.

---

### Post by z_diver on 2006-04-18
I've found that the default setup of Firefox in Ubuntu is a little slow for some reason but it's never been a "forever" wait.  The only time that happens to me is when the first DNS server listed in resolv.conf is timing out for some reason.  Try Opera to see if it's any faster.  For me Opera is very quick in both Windows and Linux.

btw: a while ago I set some of the options referred to in that link above and Firefox's speed is roughly comparable to the MS version now, though not as fast as  Opera still.

Edit: Another nice firefox customization worth setting is changing the browser.urlbar.clickSelectsAll to true.  So about:config and search for urlbar.  Then you can select the url with one click instead of 3.

---

### Post by njzillest on 2006-04-18
thanks alot, yeah its my DNS and it often times out when connecting to the server. 

Its only when i browze (thats why its a DNS problem lol) I have faster speeds while downloading/uploading torrents.



well ill look into it tommorrow (its midnight here) and post if it solved my problem

---

### Post by agger on 2006-04-19
[QUOTE=njzillest]thanks alot, yeah its my DNS and it often times out when connecting to the server. 

Its only when i browze (thats why its a DNS problem lol) I have faster speeds while downloading/uploading torrents.



well ill look into it tommorrow (its midnight here) and post if it solved my problem[/QUOTE]

I'm using Firefox 1.5, and I'm not experiencing any speed issues at all in Ubuntu - nor did I, come to think of it, with the 1.2 version.

But yes, I do suppose DNS timeouts might be a problem. Curiously enough, I had a similar problem when I was using Windows 98 about a year back: First time the browser connected, it froze up to a minute before it started getting data: Afterwards, everything was fine. Maybe also some DNS misconfiguration, or maybe the Winsock installation was simply bogged down after five years.

---

