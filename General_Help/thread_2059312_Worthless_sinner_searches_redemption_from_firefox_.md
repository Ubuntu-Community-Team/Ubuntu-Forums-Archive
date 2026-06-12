---
title: "Worthless sinner searches redemption from firefox wrath"
date: 2012-09-17
forum: General Help
---

### Post by Klympf on 2012-09-17
I am a poor, worthless sinner that keeps on visiting websites like google image search. When I commit those sins, firefox crashes and freezes my whole system, no mouse or keyboard input possible. 

Then I have to do a hard shutdown and reboot. Then, the wrath of firefox hits me again by the cynical face of fsck. It has to run always twice - first as an automatic function, but it quits because it cannot resolve conflicts alone. 

Then the maintenance shell comes up telling be that fsck has to be run manually. The whole home partition is scanned a second time, prompting me to answer to a litany of miraculous questions always with yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes, yes. Then, I can log in again. 

What can I do to relieve me from some of the pains? Should I light some candles? Would it help to be nicer to my neighbors? 

Or is there at least a way to have fsck start automatically with the -a option enabled, so it needs to run only once and answer the questions that can be only answered with 'yes' with yes by itself? 

I don't ask for a resolution of firefox to display ordinary websites without desktop freezes because I know that this is not possible, at least not in this life. 

Pray for me to ease my pain! May the sysadmin be with you!

---

### Post by Cheesemill on 2012-09-18
Sounds to me like your hard drive is dying, continually having to run fsck points to this.

---

### Post by vasa1 on 2012-09-18
> **Cheesemill said:**
> Sounds to me like your hard drive is dying, continually having to run fsck points to this.
We need a new section devoted to last rites ;)

---

### Post by SlugSlug on 2012-09-18
[QUOTE=vasa1] Do we really need to requote the previous post in its entirety?             [/QUOTE]



Sorry couldn't resist ;)

---

### Post by Cheesemill on 2012-09-18
Try booting from a Live CD and visiting the same sites to see if the problem still occurs.
If not then it points to a dying HD, if you still get the hangs then it's probably time to test your RAM instead.

---

### Post by vasa1 on 2012-09-18
> **SlugSlug said:**
> Sorry couldn't resist ;)
That was a reincarnation, not a requote ;)

---

### Post by matt_symes on 2012-09-18
Hi

> **Cheesemill said:**
> Try booting from a Live CD and visiting the same sites to see if the problem still occurs.
If not then it points to a dying HD, if you still get the hangs then it's probably time to test your RAM instead.

If you try this good idea then make sure the LiveCD is not using the hard drive swap.

Kind regards

---

### Post by The Cog on 2012-09-18
I don't know about your firefox freezes, but next time, try this instead of a hard reset:
1: Press and hold both the Alt and Ctrl keys
2: Press and release SysReq or PrntScrn (either seems to work for me)
3: Press and release the K key
4: Release Alt, Ctrl
This should kill the GUI and drop you back to the login screen

---

### Post by Statia on 2012-09-18
> **The Cog said:**
> 
1: Press and hold both the Alt and Ctrl keys
2: Press and release SysReq or PrntScrn (either seems to work for me)
3: Press and release the K key
4: Release Alt, Ctrl
This should kill the GUI and drop you back to the login screen

And if that does not work: Alt-SysRq REISUB

(mnemonic: Raising Elephants Is So Utterly Boring)

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by Klympf on 2012-09-22
Thank you for all the hints and for reading through my somewhat sarcastic post. :rolleyes:

These special REISUB tricks are definitely worth mentioning here, so more people learn about them, but it does not work in my case, the keyboard is totally dead. 

The harddisk was replaced some time ago and is fine, according to SMART. 

I did a lot of things tracking down the source of my crashes. I updated java and cleaned out the sqlite databases, some of which were corrupt. 

But the freeze seems to be connected to graphics-intense sites like image search or some online news sites. 

mozilla has a [page with debugging tipps]("https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding") and **disabling hardware acceleration **seemed most closely connected to my problems. So far, I ran sessions in safe-mode and normal mode where I did several image searches in parallel and opened some known-to-cause-problems news sites, too, without a freeze. 

I am not totally convinced that the problem is solved but I would report back in a few days if it is indeed the case for me. That would be a good thing because if you google "firefox google image search freeze" the problem is not uncommon but an easy solution is hard to find.

---

### Post by Buntu Bunny on 2012-09-23
Um, wouldn't it be easier to use a different browser?

---

### Post by Klympf on 2012-09-27
> **Klympf said:**
> I am not totally convinced that the problem is solved but I would report back in a few days if it is indeed the case for me. That would be a good thing because if you google "firefox google image search freeze" the problem is not uncommon but an easy solution is hard to find.

The error pertains and Firefox still freezes my desktop.

---

### Post by dragonfly41 on 2012-09-27
Have you tried the flash-aid add-on for firefox?

---

### Post by Klympf on 2012-10-12
One solution that works: 

Run Firefox under Microsoft Windows!!

---

### Post by kurt18947 on 2012-10-12
Sounds a little like a video driver conflict.  If you have proprietary drivers enabled, disable or uninstall them.  If you don't have proprietary drivers enabled and they are available, try enabling.

---

### Post by Klympf on 2012-11-02
You are probably right, I tried out the free and the closed driver, it didn't help, though I think that the video driver is pretty close to the problem. But we will never know.

**I finally solved the problem by performing a dist upgrade to 10.04.** This was relatively easy to do, but needed preparation and oversight. 

I made backup images of my root and home partitions, cleaned up the system from unnecessary files to free disk space, set the software sources. 

After the upgrade, I cleaned again to get rid of old files and packages, upgraded the kernel manually to the latest version in the repos.

---

### Post by Klympf on 2012-11-02
> **Buntu Bunny said:**
> Um, wouldn't it be easier to use a different browser?

:) I indeed tried webkit-based epiphany, but  I missed my plugins and it runs noticeably slower on my machine.

---

### Post by Klympf on 2012-11-02
> **dragonfly41 said:**
> Have you tried the flash-aid add-on for firefox?

thanks, maybe a helpful plugin for less experienced users, but I had already set up my flash (and java) configuration manually. I was quite sure everything was alright and I did not want to mess with it again.

---

