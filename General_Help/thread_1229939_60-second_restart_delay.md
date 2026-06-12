---
title: "60-second restart delay"
date: 2009-08-02
forum: General Help
---

### Post by DGeeez on 2009-08-02
I don't remember when it started, but it's fairly recent that Ubuntu gives me a "The computer will restart in 60 seconds", and then begins countdown. I don't know if there's a good reason that I need to wait that long, or why I now get it consistently, and I don't see this problems in Ubuntu-related threads. Some have got a message like this as a Windows virus, and that's freaking me out, except that it hasn't shut me down when I don't want it to. If I don't want to wait a whole minute before it begins the process, sometimes there's a nasty beep, and then restart begins, but it's annoying when I have to deal with this, and then I wonder if I should wait. Anybody know what this is?

Thanks.

---

### Post by doas777 on 2009-08-02
the 60-second thing is part of ubuntu jaunty, and you should see it every time you reboot. the beep too, though that should be better in karmic. you don;t have to wait the 60 seconds if you don't want to; just  click the "Shutdown now" button.

---

### Post by rCXer on 2009-08-02
Like doas777 said, It's part of Ubuntu. To get rid of it...

* Right click on your username (the "Fast User Switch Applet") and select Preferences.
* Uncheck "Show confirm dialogs for logout, restart and shutdown"

---

### Post by DGeeez on 2009-08-03
Hey, guys, thanks - it's good to know that there's nothing wrong here! But does anyone know if it's really doing anything which would be worth waiting for during that 60 seconds of our time, should we choose to wait? I have not noticed my fan running any faster while it's counting down, as it will in it's final gasp before shutdown or restart (while doing stuff like writing recovery images, or anything which would prevent system performance problems), but if there isn't a purpose for this, then who decided to annoy us with it?

---

### Post by doas777 on 2009-08-03
> **DGeeez said:**
> Hey, guys, thanks - it's good to know that there's nothing wrong here! But does anyone know if it's really doing anything which would be worth waiting for during that 60 seconds of our time, should we choose to wait? I have not noticed my fan running any faster while it's counting down, as it will in it's final gasp before shutdown or restart (while doing stuff like writing recovery images, or anything which would prevent system performance problems), but if there isn't a purpose for this, then who decided to annoy us with it?


no the 60 seconds is there for the user. the PC is doing nothing (or whatever it was doing when you asked it to shutdown).

the 60 seconds is there so that any other users connected to the box have time to save their work, etc. the counter is just there to make sure you don't hit the button and walk away, not realizing that there was a confirmation box sitting on the screen.

---

### Post by DGeeez on 2009-08-04
It's a bad idea - it must go!

I've just got to say, this distro is really moving in the wrong direction when it starts to nag those who rejected Vista as badly as the same, or in some ways worse. This particular nag is not even a Vista nag, it's a nag original, and it couldn't be more ridiculous. Microsoft may give you a "other users may be connected" warning, but that's a little more intelligent than just starting a no-purpose-given countdown - sheesh!!! So, Ubuntu engineers, there may just be more than one user sharing YOUR box, but I, like at least half of your users, am the sole user of the network-connected box at my job, as with the box at home in my cave, and an intelligent operating system should recognize the difference, so that it won't nag you when you are the only logged in user.

---

### Post by Hobgoblin on 2009-08-04
> **DGeeez said:**
> This particular nag is not even a Vista nag, it's a nag original,

This is very much a Unix/Linux idea.  Perhaps it seems out of place on a single user desktop but it can easily be turned off.  But for some I can see it being useful.

---

### Post by DGeeez on 2009-08-05
Heh heh - "fast user switcher applet" - how many times can you say that fast in 60 seconds? 

Thanks, rCXer! Well, it took me awhile to figure out what the above refers to. I didn't know it referred to the gnome panel icons, which are referred to as "widgets" when you go to add one to it, and it sounded to me more like something you would find under the Adm... menu - LOL!

The feature is easily disabled, when you know where to go change it, but why should anyone need to? Isn't computing technology advanced enough that a system would know when there are other users logged in, and not nag you when you are the only one? Sorry, but I just can't ignore the appearance of something so half-baked, no matter how much I didn't pay for it.

Anyway, this mission-impossible-inspired feature can be amusing when you look at it that way, and it may be useful to some, but for the purpose of preventing scrolling errors on that small drop down where one might shut down instead of logout, how about launching a window full of big buttons in place of that scrolling menu? I know, it's KDE-style, and I prefer GNOME in most ways, but hybridization is sometimes good for evolution.

---

### Post by CatKiller on 2009-08-05
> **DGeeez said:**
> HSorry, but I just can't ignore the appearance of something so half-baked, no matter how much I didn't pay for it.

It's a safety-net. If you pressed the button when you didn't mean to, you get a chance to cancel. If you want to shut down immediately, you can press the appropriate button. If you definitely meant to press the button and you've wandered off to do something else, the computer will still shut down as you'd expect.

There are at least two posts that I can remember where it turned out to be useful; one poster had a shorting power switch and the other had a small child that loved to press buttons. In both cases, having the confirmation dialogue helped them to not lose their work because the computer had just shut down.

> for the purpose of preventing scrolling errors on that small drop down where one might shut down instead of logout, how about launching a window full of big buttons in place of that scrolling menu?

You mean like if you use the Shut Down... applet rather than the User Switcher applet?

---

### Post by DGeeez on 2009-08-05
> **CatKiller said:**
> It's a safety-net. If you pressed the button when you didn't mean to, you get a chance to cancel. If you want to shut down immediately, you can press the appropriate button. If you definitely meant to press the button and you've wandered off to do something else, the computer will still shut down as you'd expect.

There are at least two posts that I can remember where it turned out to be useful; one poster had a shorting power switch and the other had a small child that loved to press buttons. In both cases, having the confirmation dialogue helped them to not lose their work because the computer had just shut down.



You mean like if you use the Shut Down... applet rather than the User Switcher applet?

Hail, Catkiller-god!:D

Well, the only error which is conceivable for one who isn't sharing his PC would be caused by a scrolling error on the tiny drop-down menu. As far as pressing the button when you didn't mean to, and then scrolling down to anything fatal, has anyone actually done that? With text on either side of the button (I've got my login name on one side, and the date on the other), it seems no easy feat of accident. But then again, if the shutdown system was changed so that a window of options was launched, as is done with KDE distros, then two actions would be required for an error. I think the KDE menu system is far more tedious for all of the horizontal scrolling which it requires, but when it's time to restart, nothing was ever made easier. It's something which you won't turn away from, thinking it's done already, when it isn't. Not an issue with a shutdown, but there were a number of times when I was forced to restart because of upgrades, new software I was trying, or the failure of others which I had tried. I'd go to get a beer, and when I came back, the restart hadn't even begun yet - that's when it can get annoying!

---

### Post by t0p on 2009-08-05
> **DGeeez said:**
> 
The feature is easily disabled, when you know where to go change it, but why should anyone need to?

This is one of Linux's great strengths - its almost infinite configurability.  No matter what the default settings are, someone will not like them.  So we can change the operating system's behaviour in myriad ways until it suits our every foible.

---

### Post by ugm6hr on 2009-08-05
> **DGeeez said:**
> But then again, if the shutdown system was changed so that a window of options was launched, as is done with KDE distros, then two actions would be required for an error. 

Also the Xfce default, if you are interested.

---

### Post by CatKiller on 2009-08-05
:)
> **DGeeez said:**
>  Well, the only error which is conceivable for one who isn't sharing his PC would be caused by a scrolling error on the tiny drop-down menu. As far as pressing the button when you didn't mean to, and then scrolling down to anything fatal, has anyone actually done that? With text on either side of the button (I've got my login name on one side, and the date on the other), it seems no easy feat of accident.

It's not just the User Switcher applet. The countdown option is for any of the shutdown methods. Like the power button on the front of the case. Or the keyboard.

Your keyboard might not have a power button on it, but mine does. And my cat will often wander across the keyboard to get somewhere else. I, for one, am glad that it won't immediately shut down should she put her paw on that particular button :)

EDIT:

> **DGeeez said:**
> I'd go to get a beer, and when I came back, the restart hadn't even begun yet

You must keep your fridge remarkably close to your computer.

---

### Post by quixote on 2009-11-11
I have to add my vote to the "this is a really dumb idea" group.  I've been using Ubuntu since Dapper and I love it.  I've been using unix since 1978.  I had no idea the supposed function of that 60 sec countdown (*_60 seconds!_*) was to allow hypothetical other users to save work.

I've also been irritated by it for months.  I had no idea that you could simply turn it off.  I mean, hello?  There's no helpful message on the box that you can go to prefs and untick the 'show confirms on logout, etc'.  I don't usually spend my time exploring every item on every menu on every new install of Ubuntu.

So, anyway, what I'm trying to say is either 1) make the system smart enough to see whether it's single user, or better 2) present a choice the first time it comes up.  

Don't just make everyone deal with YASD (yet another stupid dialog).  If an ancient unix user like me didn't figure out you could just turn it off, there's probably plenty of others too.

---

### Post by asbesto on 2009-11-30
> **rCXer said:**
> Like doas777 said, It's part of Ubuntu. To get rid of it...

* Right click on your username (the "Fast User Switch Applet") and select Preferences.
* Uncheck "Show confirm dialogs for logout, restart and shutdown"

I can't find this on 9.10! 

How to disable this stupid thing? :(

---

### Post by quixote on 2009-12-01
I just looked it up for karmic a week ago, and I've already forgotten how it's supposed to be done.  Maybe it was under System > Preferences > Login settings?? (I'm going to burst if I don't carp again about how stupid it is to hide this preference under three layers in different places each time!)  Anyway, don't give up hope.  I know it can be done, I just don't remember how.  Search for karmic 60 second delay, or the like?

---

### Post by ed-koala on 2009-12-01
No one has asked this yet, so I will ... can you set the time to something other than 60 seconds? Like 10 seconds?

---

### Post by audiomick on 2009-12-01
> **ed-koala said:**
> No one has asked this yet, so I will ... can you set the time to something other than 60 seconds? Like 10 seconds?

That may not be possible.
I assume the button in the gui issues the shutdown command. If you look at

```
man shutdown
```

you will see that the _TIME_ option can only be expressed in minutes or time of day. This would indicate that 60 sec is the shortest possible.

For an immediate restart:

```
sudo shutdown -r now
```

---

### Post by ed-koala on 2009-12-01
lol, infinitely configurable my ****! lol  Found one thing that isn't!!  Not that it bothers me, I either hit the button or walk away.

---

### Post by dcstar on 2009-12-01
Set this Gconf (Applications-System Tools-Configuration Editor) key and you will no longer get the 60 second stuff:

```
/apps/indicator-session/suppress_logout_restart_shutdown
```


PS Can the OP now mark this thread as Solved?

---

### Post by Robb987 on 2009-12-29
very, very annoying feature! Why would one program a feature like this?

---

### Post by audiomick on 2009-12-29
Hi.
It's been said already but: the function hails back to the days when Unix systems ran on a mainframe and had multiple users. They had to be warned when the administrator was about to shut down the system, so there is a function to do so.

Why put it on a desktop? Have you never hit the shutdown button, then suddenly remembered something else you wanted to do. I have. Heaps of times...;)

---

### Post by Robb987 on 2009-12-30
> **audiomick said:**
> Hi.
It's been said already but: the function hails back to the days when Unix systems ran on a mainframe and had multiple users. They had to be warned when the administrator was about to shut down the system, so there is a function to do so.

It would be useful for Ubuntu server edition, if there was a GUI... Not for a laptop that is started and shut down 15 times a day.

> **audiomick said:**
> Why put it on a desktop? Have you never hit the shutdown button, then suddenly remembered something else you wanted to do. I have. Heaps of times...;)

why not remove the Close button from the GUI and use the  command: "shutdown -P 1"  in the terminal.

I use Ubuntu because of a total lack of these amazing "are you sure?", "are you really sure?", "you must be kidding, are you sure?" stupid list of questions in Windows!

Click and go, I like it!

---

### Post by duffed on 2009-12-30
Just change the conf and stop crying. Its only 60sec and only when you reboot or shutdown don't need to panic. If its not useful for you it could be for other people. Linux is not design ONLY for YOUR need. Open your mind!

---

### Post by duffed on 2009-12-30
[http://ubuntuguide.net/disable-60-seconds-delay-notification-in-ubuntu910karmic](http://ubuntuguide.net/disable-60-seconds-delay-notification-in-ubuntu910karmic)

---

### Post by jamesisin on 2009-12-30
This thread appears to be solved and should be marked as such.

---

