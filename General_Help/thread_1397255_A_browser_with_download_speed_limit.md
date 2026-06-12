---
title: "A browser with download speed limit?"
date: 2010-02-03
forum: General Help
---

### Post by Garret88 on 2010-02-03
It sounds weird but on Linux I can't find a browser that allows to set a download speed limit.
I found an extension for Firefox but it works only on Windows.
I know the existence of download managers like d4x, wget, jdownloader, etc... but some downloads can only be done by browser.
I know trickle too but if I want to change the speed limit I have to 'restart' the command (interrupting the current download).
Then I didn't find an extension for Chromium.

---

### Post by Jackzor on 2010-02-03
Install FireFox under wine and use Firefox Throttle

:D

---

### Post by Garret88 on 2010-02-03
> **Jackzor said:**
> Install FireFox under wine and use Firefox Throttle

:D
I would use a more "clean" solution

---

### Post by Jackzor on 2010-02-03
> **Garret88 said:**
> I would use a more "clean" solution

Well.. I did google around a bit for you and I decided that wine would solve your problems. But I will try to find a better solution for you. Although I do feel like that will work flawlessly

---

### Post by Dayofswords on 2010-02-03
just wondering...

why do you want to slow it down?

---

### Post by Garret88 on 2010-02-03
> **Dayofswords said:**
> just wondering...

why do you want to slow it down?
So if I am downloading at maximum I can't surf on the internet. So when I surf I put it down, and when I don't I set the maximum velocity.

---

### Post by Jackzor on 2010-02-03
Alright. I dunno much about this and I do not play on testing it. But after reading the page it sounds nice.

I would still use wine+firefox+Throttle 

[http://lartc.org/wondershaper/](http://lartc.org/wondershaper/)

---

### Post by Garret88 on 2010-02-03
> **Jackzor said:**
> Alright. I dunno much about this and I do not play on testing it. But after reading the page it sounds nice.

I would still use wine+firefox+Throttle 

[http://lartc.org/wondershaper/](http://lartc.org/wondershaper/)
I have firefox always opened. I don't want to have wine always on also because I use ubuntu x86_64 and I need to install the lib32 dependencies.
As I said before I would avoid this solution ;)

---

### Post by Jackzor on 2010-02-03
> **Garret88 said:**
> I have firefox always opened. I don't want to have wine always on also because I use ubuntu x86_64 and I need to install the lib32 dependencies.
As I said before I would avoid this solution ;)

Well, I looked for a good 30 minutes including these forums and couldn't get anything. I'm sure you have been looking around too and finding nothing. There for I am done with this thread and I do apologize for not being of further assistance to you.

I do hope you find what you are looking for.

---

### Post by lovinglinux on 2010-02-03
> **Garret88 said:**
> So if I am downloading at maximum I can't surf on the internet. So when I surf I put it down, and when I don't I set the maximum velocity.

Something must be wrong with your network setup, because I can download whatever I want, download torrents at the same time and my browsing experience doesn't slows down.

You are not using dial-up are you?

Perhaps you could tweak your Firefox network settings with these:

[http://kb.mozillazine.org/Network.http.max-connections](http://kb.mozillazine.org/Network.http.max-connections)
[http://kb.mozillazine.org/Network.http.max-persistent-connections-per-server](http://kb.mozillazine.org/Network.http.max-persistent-connections-per-server)
[http://kb.mozillazine.org/Network.http.keep-alive](http://kb.mozillazine.org/Network.http.keep-alive)
[http://kb.mozillazine.org/Network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6)

Also check [this](http://lovinglinux.megabyet.net/?page_id=220#Speed--Optimization-1).

---

### Post by Runaway1956 on 2010-02-08
> **Garret88 said:**
> It sounds weird but on Linux I can't find a browser that allows to set a download speed limit.
I found an extension for Firefox but it works only on Windows.
I know the existence of download managers like d4x, wget, jdownloader, etc... but some downloads can only be done by browser.
I know trickle too but if I want to change the speed limit I have to 'restart' the command (interrupting the current download).
Then I didn't find an extension for Chromium.


[http://lartc.org/wondershaper/](http://lartc.org/wondershaper/)

Wondershaper is sweet.  I'm almost_certain that you'll find it in one of Ubuntu's repositories.  It's possible that I used a Debian repository, but I can't remember for certain.

It's command line, it takes up to 15 minutes to read the documentation, and it takes up to another 10 minutes to configure it to your liking.  In half an hour or less, you can have ALL of your bandwidth under control, so that you can run Synaptic, download a torrent, download with Firefox, AND browse at a reasonable speed, all at the same time.

Why limit just your browser, when you can control EVERYTHING?

Even better, if you have your home/office networked, you can install the wondershaper on just the gateway machine, and control ALL the internet traffic for the entire network.

You don't even need to be a guru.  Download it, read the documentation, and put it to use.  Running as a daemon may be difficult for a beginner - so IF you are a beginner, go ahead and download it, read, then post more questions.  ;)

---

### Post by Runaway1956 on 2010-02-08
Also - Firestarter firewall offers some limited QOS service.  Not nearly as effective as Wondershaper, but it will limit downloads somewhat, and give priority to interactive traffic, such as a flash game.  Firestarter is most definitely available through Ubuntu's repositories. 

(Sorry, I don't have a Debian box at hand, so I can't check which repository. Or, not easily, anyway.)

---

