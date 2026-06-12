---
title: "Firefox hangs frequently, Ubuntu 10.04"
date: 2010-12-08
forum: General Help
---

### Post by Cenko on 2010-12-08
Hi,

I'm using firefox 3.6.8 on ubuntu 10.04

Whenever I try to open a site, most frequently firefox hangs, and even if one tab hangs, all firefox hangs.

It feels like when it has problem connecting to a site, it hangs all firefox.

Is it a common issue? I searched but could not find it.

---

### Post by lovinglinux on 2010-12-08
Do you mean the interface becomes unresponsive and you can't click on anything or the page simply won't load?

---

### Post by Cenko on 2010-12-08
Exactly, it freeze and becomes unresponsive. I face this program in two different computers, both having Ubuntu 10.04.

In chromium I have no such problem...

---

### Post by lovinglinux on 2010-12-08
Disable ipv6 and disable "Block reported attack sites and web forgeries". See [http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

---

### Post by Cenko on 2010-12-08
That solved it, thanks!

---

### Post by lovinglinux on 2010-12-08
> **Cenko said:**
> That solved it, thanks!

You are welcome.

---

### Post by AlexanderDGreat on 2010-12-21
@lovinglinux - I love your blog site, and I love the solution now my Firefox stops being gray.

Thanks. :)

PS I wonder what caused this, I mean, last few months it wasn't like this.

---

### Post by AlexanderDGreat on 2010-12-22
Sorry... Spoke too soon... I'm STILL having this weirdness in Firefox.

Whenever I'm doing something in Firefox, it just randomly TURNS GRAY, STOPS for a while, fades out, but it's still there.

Then I wait for a few seconds, SOMETIMES 1 MINUTE!

Then it comes back functioning again.

I did turn off ipv6, and Block reported attack sites and web forgeries... **STILL PROBLEM persists.**

**Help!**

---

### Post by lovinglinux on 2010-12-22
> **AlexanderDGreat said:**
> @lovinglinux - I love your blog site, and I love the solution now my Firefox stops being gray.

Thanks. :)

PS I wonder what caused this, I mean, last few months it wasn't like this.

You are welcome.

> **AlexanderDGreat said:**
> Sorry... Spoke too soon... I'm STILL having this weirdness in Firefox.

Whenever I'm doing something in Firefox, it just randomly TURNS GRAY, STOPS for a while, fades out, but it's still there.

Then I wait for a few seconds, SOMETIMES 1 MINUTE!

Then it comes back functioning again.

I did turn off ipv6, and Block reported attack sites and web forgeries... **STILL PROBLEM persists.**

**Help!**

Does it happen on any web site or even when Firefox is left alone for a while or it happens on particular web pages?

---

### Post by AlexanderDGreat on 2010-12-23
> Does it happen on any web site or even when Firefox is left alone for a while or it happens on particular web pages?

Thank you lovinglinux, yes it happens on any website, particularly on websites with javascripts or java.

By the way, I installed Oracle (Sun) Java Runtime Environment (JRE) over the OpenJDK (open source). Do you think they're related?

Yes, I think it also happens when I'm just reading an article and NOT doing anything at all.

It also happens when I'm in [http://localhost](http://localhost) because I'm making a program PHP + MySQL.

---

### Post by lovinglinux on 2010-12-23
> **AlexanderDGreat said:**
> Thank you lovinglinux, yes it happens on any website, particularly on websites with javascripts or java.

By the way, I installed Oracle (Sun) Java Runtime Environment (JRE) over the OpenJDK (open source). Do you think they're related?

Yes, I think it also happens when I'm just reading an article and NOT doing anything at all.

It also happens when I'm in [http://localhost](http://localhost) because I'm making a program PHP + MySQL.

Have you tried to create a new profile or start Firefox in safe mode?

---

### Post by AlexanderDGreat on 2010-12-23
> Have you tried to create a new profile or start Firefox in safe mode? OK but will the new profile delete all my bookmarks? and settings? If I'm in safe mode, what's the pros and cons?

Does this mean, I'll have to run safe mode all the time from now on? But I wasn't running safe mode ever before.

---

### Post by lovinglinux on 2010-12-24
> **AlexanderDGreat said:**
> OK but will the new profile delete all my bookmarks? and settings?

No, as long as you don't delete your current profile. You can create as many profiles as you want. Obviously that each profile will have it's own bookmarks, passwords and settings.

See [http://firefox-tutorials.blogspot.com/2010/05/profiles.html](http://firefox-tutorials.blogspot.com/2010/05/profiles.html)

> **AlexanderDGreat said:**
> If I'm in safe mode, what's the pros and cons?

When in safe mode, extensions are temporarily disabled. So if the problem is caused by an extension, which is not uncommon, then it will vanish in safe mode.

> **AlexanderDGreat said:**
> Does this mean, I'll have to run safe mode all the time from now on?

No, safe mode is only for troubleshooting or for fixing a profile that doesn't even start.

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by AlexanderDGreat on 2010-12-30
Hi lovinglinux, I hope it's not of much a burden, I've come to you for help, how come when I FULL SCREEN a YouTube video in Firefox, it just shows half?

Here's an example.

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/full_screen_troubles.jpg[/IMG]

---

### Post by lovinglinux on 2010-12-30
> **AlexanderDGreat said:**
> Hi lovinglinux, I hope it's not of much a burden, I've come to you for help, how come when I FULL SCREEN a YouTube video in Firefox, it just shows half?

Here's an example.

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/full_screen_troubles.jpg[/IMG]

See this [http://ubuntuforums.org/showthread.php?t=1653899](http://ubuntuforums.org/showthread.php?t=1653899)

---

### Post by AlexanderDGreat on 2010-12-31
OK, but I tried those it didn't work. The weird thing is on my other computers with Ubuntu 10.04 also this doesn't happen.

Maybe it's my video card Nvida 9500GT. Anyway, thanks for your help. :)

---

