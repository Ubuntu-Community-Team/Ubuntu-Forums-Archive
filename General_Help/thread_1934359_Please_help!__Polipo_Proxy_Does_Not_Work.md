---
title: "Please help!  Polipo Proxy Does Not Work"
date: 2012-03-02
forum: General Help
---

### Post by Kissell on 2012-03-02
I have followed dozens of guides to setup Polipo as a proxy for Tor, and none of them work...  

Here's what I do.

```

sudo apt-get install tor

```

Then in the Chromium browser I change my my preferences to use the proxy 127.0.0.1:9050.  And it works, I can go to [https://check.torproject.org/]("https://check.torproject.org/") and it says Tor is working.  Great!  But it is slow.

So I do:
```

sudo apt-get install polipo

mv /etc/polipo/config /etc/polipo/config.original

wget http://dangertux.no-ip.org/downloads/config -O /etc/polipo/config

sudo /etc/init.d/polipo restart && sudo /etc/init.d/tor restart

```

Everything looks good...  I can still get to websites with Tor...  but then I go to change my proxy settings to use 127.0.0.1:8118 so that I can go through the Polipo proxy...  and nothing, no websites will connect anymore.  

I've verified this same thing happens on several computers...  so I don't understand why it's not working for me, dozens of guides look like it works okay for them.

The config file looks good...  and I've completely disabled the ufw firewall.  "sudo ufw disable"  but no luck connecting using Polipo.

---

### Post by Paddy Landau on 2012-03-02
> **Kissell said:**
> But it is slow.
Tor will be slow. Very slow. It is primarily meant for people in closed countries to be able to access the wider Internet securely. But it is entirely volunteer-supported.

---

### Post by jim_deadlock on 2012-03-02
+1 for slow - you're never going to get around that

I don't know how old your version is but these days you don't have to mess around installing anything, you just grab the browser bundle and run it. It's an amazing thing to behold.

---

### Post by Kissell on 2012-03-02
So nobody uses Polipo or Privoxy anymore?  

There is no reason to do that?

I actually don't see the benefit,  because I assume my browser should be handling any functions the proxy would.  

But I wanted to try it.

BTW: I have the latest version now, I've added the GPG Keys because the Ubuntu repos are out of date...  but it doesn't make any difference, I can always get Tor to work, but never with one of those proxies.

---

### Post by jim_deadlock on 2012-03-02
I've been messing around with the polipo and privoxy installations like you for several years and I know what a pain it used to be, that's why I'm extremely impressed with the new bundle they created just recently. I highly recommend you give it a try, it's fantastic because:

a) It's so incredibly easy to use, you don't even have to install it you just decompress it and it's ready to go, slap it on your flash drive or anywhere.

b) The bundled browser has all the proper security in place so you don't have to worry about optimising your "normal" browser.

Edit: Privoxy can be useful independently of Tor, it's good if you want to customise the content in your browser, for example if you want to block ads or replace certain words (bad language etc). Polipo is more about caching and getting a smooth connection, I don't think it's necessary any more.

Edit again: I just re-read your original post and you're doing it wrong anyway, the Tor website has always said NOT to use the repositories because the versions are permanently out of date.

---

### Post by Kissell on 2012-03-02
> **jim_deadlock said:**
> 
Edit again: I just re-read your original post and you're doing it wrong anyway, the Tor website has always said NOT to use the repositories because the versions are permanently out of date.

I've got the newest version by installing additional private repositories, I just didn't include those steps to make it less complicated, because it doesn't work both ways.

I'm more interested in just getting the proxy to work, than actually using Tor.  As you've said, there are other useful reasons to be using a proxy.

---

### Post by jim_deadlock on 2012-03-02
Does this help?

[https://www.torproject.org/docs/faq.html.en#TBBPolipo]("https://www.torproject.org/docs/faq.html.en#TBBPolipo")

---

### Post by Kissell on 2012-03-02
Oh, thanks for finding that...

There is a ton of information out there about people recommending the use of polipo...  even with Ubuntu 11.10, but it appears they are out of date according to Tor themselves.

I guess I'll just go do something else...  like figure out how to convert some bash scripts into python...

---

### Post by ottosykora on 2012-03-03
Polipo, Privoxy for TOR , no definitely no, this is completely out of date. The current versions of tor do not need it and will not use it by default.
The mechanism is self contained in the tor itself.

+1 for bundle use

the tor devs have apparently problems with most current browsers, as number of functions, plugins, addons may try to bypass tor and then it becomes useless.

if you want install it still,
Get tor from torproject.org, and not from the standard repo, set the torproject ppa
Follow closely the instruction on the torproject website, then all will work.
You need then only to use torbutton for your firefox.

Note however: 
the default installation runs the tor on boot, so if you want start it somehow by hand, to change some parameters or configure and start it with vidalia, you need to stop it first.



BTW: one should not use any other browser currently then firefox, as tor devs seem to have difficulties to get any other browser to work safely with tor.

---

