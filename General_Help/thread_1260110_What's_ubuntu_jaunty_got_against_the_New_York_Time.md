---
title: "What's ubuntu jaunty got against the New York Times?"
date: 2009-09-07
forum: General Help
---

### Post by mnoyes on 2009-09-07
Can't load the mytimes.com website in Ubuntu Jaunty, firefox 3.0.13. Have tried many solutions but to no avail -- am I doomed to get my news from AOL???:confused:

---

### Post by wojox on 2009-09-07
Just tried it with jaunty and firefox 3.0.13. Loaded right up.

Do you have adobe flash in about:plugins

Also no flash block addons from firefox?

---

### Post by howefield on 2009-09-07
At a guess,.. nothing.

Loading fine from here.

You can try sites like this when having trouble with a website..
[http://isitdown.co.uk/](http://isitdown.co.uk/)

There is another I normally use, but I can't find the link.

---

### Post by mnoyes on 2009-09-07
isitdown is a nice tool, thanks!

I know that others can access the NYT, but can't figure out why I can't... (just thought a provocative title would draw more attention :-)

I have the adobe flash plugin 10.0.32.18 installed, no flashblock or other flash players. I use open dns and wicd. I have ipv6 disabled. I have installed firefox 3.5, then uninstalled it and am back to 3.0.13. I have rebooted the router... 

mytimes.com resolves but does not connect -- if I have the terminology right -- and I have the same problem with another site: ila1588.org:confused:

Any other suggestions?

---

### Post by fandango11 on 2009-09-07
ive got firefox 3.0.13 and jaunty and mytimes.com loads without problem.

---

### Post by P4man on 2009-09-07
what happens when you try to browse it using its IP?

[http://199.239.137.217](http://199.239.137.217)

and what happens in other browsers?

---

### Post by mnoyes on 2009-09-07
Same problem when I use the IP number and when I browse in seamonkey and opera...

I tried on my old windows xp laptop and on a newer laptop also running xp (but a Japanese version) and had the same problem. So, is this a problem with my router? I have broadband service. Any ideas about where to start to find/fix the problem?

---

### Post by mnoyes on 2009-09-08
I posted on this problem earlier [here]("http://ubuntuforums.org/showthread.php?t=1259727") and have included more info in that post in response to a question. 

One new question: would using TOR enable me to get around the packet filter that seems to be the problem?:confused:

---

### Post by hibliss on 2009-09-08
I get the same packet filtered ping response, but the page loads fine for me. Where are you located in the World?

---

### Post by mnoyes on 2009-09-08
In Japan.

On another site -- [www.ila1588.org](www.ila1588.org) -- I get this from ping:

ping [www.ila1588.org](www.ila1588.org)
PING ila1588.org (74.50.28.205) 56(84) bytes of data.
^C
--- ila1588.org ping statistics ---
215 packets transmitted, 0 received, 100% packet loss, time 215457ms

---

### Post by mnoyes on 2009-09-09
Workaround?

Guessing that there might be some region issue, or some firewall problem, I installed TOR and foxyproxy (also installed privoxy, but couldn't figure it out and uninstalled -- well tried to uninstall via synaptic, but it seems it is still there?).

Now I can load nytimes.com ila1588.org and other websites.

With a little adjusting to TOR's settings (see [http://www.torproject.org/torbutton/faq.html.en](http://www.torproject.org/torbutton/faq.html.en)), I managed to get flash working. Though it still fails to stream well in large format.

Problems: 

TOR really does slow down the internet connection. 

It also seems to affect the loading of css files and images (only three of the smilies at right show up -- not :guitar: or :lolflag:  

I can't post a message or reply on this website while using tor (!)

I have yet to see if other problems crop up...

So, not a solution. What's the answer? Wait for Koala and firefox 3.5?

---

### Post by P4man on 2009-09-09
Does it happen in a live cd? In another OS ?

---

### Post by P4man on 2009-09-09
edit: oops, wrong thread

---

### Post by mnoyes on 2009-09-09
Merging this thread with another one:

[http://ubuntuforums.org/showthread.php?t=1259727](http://ubuntuforums.org/showthread.php?t=1259727)

Thanks for your feedback.

---

