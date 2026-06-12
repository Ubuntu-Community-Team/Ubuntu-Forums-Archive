---
title: "Where'd the notifications go?!"
date: 2012-04-10
forum: General Help
---

### Post by Eirreann on 2012-04-10
In Ubuntu, I used to get these awesome notifications in the upper-right corner of the screen whenever someone messaged me, or when I'd connect to a network, or when the song would change on Banshee.  Now they don't appear.  Not only that, but when I turn up/down the volume via the keyboard the little pop-up looks different.  Could this be because I just installed Xubuntu and Lubuntu?

---

### Post by Eirreann on 2012-04-10
Nevermind; they haven't gone; they've just been replaced with ugly-looking white ones that may have come from Xubuntu or Lubuntu.... either way, I would like the cool-looking black ones back, please!

---

### Post by uRock on 2012-04-10
What changes have you already made to the theme? They are black with light gray lettering by default.

---

### Post by Eirreann on 2012-04-10
> **uRock said:**
> What changes have you already made to the theme? They are black with light gray lettering by default.

Yes, that's what I want them to look like again!  Right now they look like:
[IMG]http://i296.photobucket.com/albums/mm188/Loredaen/Screenshotat2012-04-10234845.png[/IMG]
[IMG]http://i296.photobucket.com/albums/mm188/Loredaen/Screenshotat2012-04-10235038.png[/IMG]

---

### Post by Eirreann on 2012-04-10
Whatever changes that were made to the theme were not made by me, but by the installation of either Xubuntu or Lubuntu.

---

### Post by kazztan0325 on 2012-04-11
Hi Eirreann,

I'm not sure if the following information would be able to fix your problem, but I think it would be worthy to try.

**"CONFIGURABLE NOTIFYOSD BUBBLES FOR UBUNTU: MOVE, CLOSE ON CLICK, CHANGE COLORS AND MORE"**
[http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html]("http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html")

---

### Post by Eirreann on 2012-04-11
> **kazztan0325 said:**
> Hi Eirreann,

I'm not sure if the following information would be able to fix your problem, but I think it would be worthy to try.

**"CONFIGURABLE NOTIFYOSD BUBBLES FOR UBUNTU: MOVE, CLOSE ON CLICK, CHANGE COLORS AND MORE"**
[http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html](http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html)

Interesting... I'll give it a go!

---

### Post by Eirreann on 2012-04-13
Okay, the NotifyOSD Configuration tool didn't work; any other ideas?  This is bugging the **** out of me!!!!!  Is there any other way to manually change the  theme?

---

### Post by Eirreann on 2012-04-13
[COLOR=Red]**Okay, I figured it out:**

[COLOR=Black]So I opened up the task manager and observed all of the tasks that were running.  I found one running called Xfce4-updatd, and when I paused that process none of the notifications or volume pop-ups would appear.  Thus I found out that my problem was that Ubuntu was getting some of Xubuntu's system files mixed up with it's own.  So the simplest fix to this issue is to uninstall Xubuntu using the instructions here:
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)
[/COLOR][/COLOR]

---

### Post by uRock on 2012-04-13
Another win from the psychocats site. I am happy you got it fixed. ;)

---

### Post by kazztan0325 on 2012-04-14
> **Eirreann said:**
> So the simplest fix to this issue is to uninstall Xubuntu using the instructions here:
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

I'm glad to hear you have solved the problem.

And thank you for the link which you put on.
It would be useful for me too, because I also like making "Frankenstein (i.e. ubuntu-desktop and other *buntu-desktop)" and sometimes encounter with problems.

---

