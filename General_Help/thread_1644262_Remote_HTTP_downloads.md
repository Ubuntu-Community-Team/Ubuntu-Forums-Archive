---
title: "Remote HTTP downloads"
date: 2010-12-13
forum: General Help
---

### Post by lamnep on 2010-12-13
Hi,

I have a question about using ubuntu to download files from an HTTP server remotely and didn't know where to put it, so hopefully it falls under general support.

Anyway, I am about to move into a place with an incredibly slow internet connection and a tiny data allowance and my brother has said that, if possible, I can use his internet connection to download any large files to a box I can just leave at his place, then I can simply come over to his place every few weeks and copy said files to a hard drive and all will be well.

The problem is that I am not sure how to do this, today I went out and bought a few parts and built a cheap computer with a HDD big enough to hold whatever I need, however when I got home I realised I had no idea how I was going to handle the software aspect of this.

So my question is: is there any way that I can access that computer remotely over the internet and schedule fairly large downloads from an http server?
Also after talking to a friend I was told that I need to install the server version of ubuntu if this is to work, is this correct?

Also, if its relevant the specs of the computer I have for this is using an "Intel Desktop Board D510M0 + Intel Atom Processor D510" which uses 64 bit architecture.

Thanks

---

### Post by dcstar on 2010-12-13
> **lamnep said:**
> 
........
So my question is: is there any way that I can access that computer remotely over the internet and schedule fairly large downloads from an http server?
........

```
man wget
```

---

### Post by murderous mouse on 2010-12-13
Sounds to me like you might be looking for a download manager with a WebUI, as far as I'm aware there isn't one, unless your looking at tormenting in which casebook could look at torrentflux, although I remember reading something recently about a download manager called fatrat, I can't remember how it turned out though so you will need to look it up.

---

### Post by matt_symes on 2010-12-13
Hi

> Also after talking to a friend I was told that I need to install the server version of ubuntu if this is to work, is this correct?No. I'm with dcstar on this one wget and maybe cron. You have not really explained what you want though. To access over the internet to the other PC look at ssh or team viewer. Are your strengths GUI or CLI? There are a number of solutions depending on exactly what you want.

Kind regards

---

### Post by lamnep on 2010-12-14
Sorry that what I said before wasn't particularly clear, all I am looking for is to be able to remotely control downloads over the internet, the specifics are not hugely important as I'm sure I'll adapt to whatever I end up being able to do.

As far as using a command line goes: this is fine, however I am wondering if it will work for me to be able to download multiple files, or whether I will need to input the command one at a time, waiting for the first to finish before adding the second and so on

As for murderous mouses suggestion: I'm not looking to torrent, they are http downloads so torrent flux wouldn't work and I had a look at fatrat and saw that it had been mentioned a few times in conjunction with a webui but there was no mention of *how*, it all seemed very vague so I downloaded it and had a look and ended up being asked to download x-server, which I did and from there I simply couldn't figure it out and I couldn't find much in terms of a manual or FAQ so I'll hopefully have another look at it tonight and try and figure it out.

---

### Post by misskimberly on 2010-12-14
your best bet is wget...unless you have access to VMWare and can then use several free windows/mac gui type downloaders.  For me, i ended up making my own instead of using wget.

---

