---
title: "Browser(s) flicker and freeze or crash"
date: 2012-09-17
forum: General Help
---

### Post by shadow of the locust on 2012-09-17
I'm not sure if this is a browser problem or the flash plugin, but maybe someone can help.

When I open tabs in either Firefox or Chrome and have one or more with flash content, the other tabs flicker and flash and sometimes the browser freezes and force closes.

Details of my system which might help solve this include:

Ubuntu 10.04 (Lucid)

Kernel: 2.6.32-42-generic

Gnome 2.30.2

Flash version: 11.2.202.238

If you need any more details, let me know.

Thank you.

---

### Post by Kirk Schnable on 2012-09-17
It may be worthwhile to take a look in /var/log/syslog.  I seem to recall flash crashes used to show up in there (not sure if they still do... I haven't had as many flash issues since upgrading to 12.04).

Kirk

---

### Post by shadow of the locust on 2012-09-18
Thanks for your reply.

I checked there, and there is no mention of flash.  I don't really want to update to 12.04 because of unity.

Hopefully an update or a fix here will get everything running smoothly again.

---

### Post by Kirk Schnable on 2012-09-18
> **shadow of the locust said:**
> 
I checked there, and there is no mention of flash.  I don't really want to update to 12.04 because of unity.

Hopefully an update or a fix here will get everything running smoothly again.

I felt the same way about Unity ever since it came out. But when 12.04 was released, I forced myself to use it for a week. It does grow on you.

---

### Post by shadow of the locust on 2012-09-18
I have a netbook that I use to test various Linux distributions.  I'll try it there.  You never know, I might end up liking it too.  :smile:

Thanks for your help.

---

### Post by Kirk Schnable on 2012-09-18
> **shadow of the locust said:**
> I have a netbook that I use to test various Linux distributions.  I'll try it there.  You never know, I might end up liking it too.  :smile:
There's a few things about it which still irritate me... mostly related directly to its inability to be highly customized.  But for the most part, they've gotten the bugs out of it, and it's a pretty sleek looking UI.

We can still continue working on your flash issue... I wonder if Flash is keeping its logs somewhere else now.

---

### Post by shadow of the locust on 2012-09-19
The endless options for customisation is something I love about 10.04.

I've used Compiz and Cairo Dock to set my desktop up exactly the way I want.  I'm still willing to try something new, so we'll see what happens.

Regarding the flash problem, a new update to the Linux kernel seem to **so far** have made a difference.

The only problem I experienced last night regarding flickering video was in a Google Hangout and that was in the small video preview windows at the bottom of the screen.  Perhaps that is a Google plugin problem more than a flash one, but for now I'm back to being able to browse websites and watch video without crashes or quite so many glitches as before.

---

### Post by Kirk Schnable on 2012-09-20
Well, you know, Unity supports Compiz now, and a 3rd party application called MyUnity allows you to change some of the settings.

---

### Post by shadow of the locust on 2012-09-26
I upgraded to 12.04 and everything seems to be stable and flicker-free.

I installed Gnome and I'm using the classic version, so I've got everything set up almost the same as before.

Thank you for your help, Kirk.

---

