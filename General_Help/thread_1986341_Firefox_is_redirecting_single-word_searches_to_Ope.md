---
title: "Firefox is redirecting single-word searches to OpenDNS"
date: 2012-05-24
forum: General Help
---

### Post by vancinas on 2012-05-24
Any single word search made in the Firefox address bar is automatically  being redirected to OpenDNS Guide. If my search for something that has  more than one word in it the search proceeds as normal, going through  the default search engine. I have disabled all of my add-ons and started Firefox in safe mode, resetting all preferences to their defaults, but this is still happening. I even used apt-get to reinstall Firefox. Does anybody know how to fix this? Thanks!

By the way, I'm using Firefox 12.0 on Ubuntu 12.04.

---

### Post by phaed on 2012-05-25
Do you use OpenDNS for your DNS requests? It looks like Firefox is not processing the word as a search term but passing it as the domain name, and because it's a nonexistent domain name, OpenDNS responds with a search query.  This guide might help you:

[https://support.mozilla.org/en-US/kb/Location%20bar%20search](https://support.mozilla.org/en-US/kb/Location%20bar%20search)

Make sure that Internet keyword searches are turned on.

---

### Post by wilee-nilee on 2012-05-25
> **vancinas said:**
> Any single word search made in the Firefox address bar is automatically  being redirected to OpenDNS Guide. If my search for something that has  more than one word in it the search proceeds as normal, going through  the default search engine. I have disabled all of my add-ons and started Firefox in safe mode, resetting all preferences to their defaults, but this is still happening. I even used apt-get to reinstall Firefox. Does anybody know how to fix this? Thanks!

By the way, I'm using Firefox 12.0 on Ubuntu 12.04.

Check if opendns is actually being accessed if you are using it. 

[http://www.opendns.com/welcome/](http://www.opendns.com/welcome/)

If you are not getting it look here this is what I had to use to get it back, post 1

[http://ubuntuforums.org/showthread.php?t=1968061](http://ubuntuforums.org/showthread.php?t=1968061)

I also have noscript installed blocking all but a few web addresses including google, so my search typing brings nothing up, till I hit enter.

---

### Post by vancinas on 2012-05-25
Well, I do have keyword searches enabled and I am getting access to OpenDNS. I have found an acceptable workaround though. I installed an add-on called InstantFox, which provides custom keyword searching. It has a "Standard Search Without Shortcuts" option that allows you to specify a search URL that all address bar searches should be sent to. I don't know why that add-on is able to override the browser's behavior when the built-in configurations can't, but I'll take what I can get. Thanks for you help!

---

