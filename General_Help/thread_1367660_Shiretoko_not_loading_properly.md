---
title: "Shiretoko not loading properly"
date: 2009-12-29
forum: General Help
---

### Post by JoetteB on 2009-12-29
When I tried to start Shiretoko today, it starts loading, but stops before any of the buttons load. A screenshot is attached. When I started FF 3.* I received an update. Could this be what caused the problem? If so, does anyone have a suggestion? It's not that FF doesn't work for me and if it's just borked, I can live with that.

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by synapsys on 2009-12-29
From the mozilla website, it appears that shiretoko is in alpha 1. This means that it's really not quite ready for normal use just yet. It also says....

> Shiretoko Alpha 1 is being made available for **testing purposes only**,               and is intended for web application developers and our testing community.  Current users of               Mozilla Firefox should **not** use Shiretoko Alpha 1.

---

### Post by JoetteB on 2009-12-29
To the best of my knowledge I'm not using Alpha 1. I've been using Shiretoko for the last several months with no issues, but I believe I do have it set up to automatically check for updates. Would that install an Alpha 1 update if it's not ready for wide release yet?

Is there a way to check what version this is since none of the buttons are loading?

---

### Post by synapsys on 2009-12-29
hmm, maybe I found an older page with google. From what I gather, shiretoko is basically firefox, and you should not be running both at the same time. So maybe pick one or the other? If you choose shiretoko, I believe re-installing would fix your problem.

---

### Post by raktarok on 2009-12-29
I can check the version for my firefox by doing ths from a termnal:

```
firefox -v
```

A similar command should also work for shiretoko.

Also try launching the browser from a terminal abd see if you can identify any problem from the output.

---

### Post by JoetteB on 2009-12-29
Unfortunately, I can't check the version I have of Shiretoko that way. I did attempt an uninstall/reinstall, with the same results when I tried to start Shiretoko.

I don't generally run both programs. I've been using Shiretoko exclusively and only went back to FF this evening when Shiretoko got borked.

I'm not sure how to make it run from a terminal. I'm just a user. Normally I'd corner my sysadmin (husband) and ask him to fix it, but he's not available. I expect I'll just need to wait for him to see if he can figure out what the issue is. 

Thanks for the help attempts!

---

### Post by lidex on 2009-12-29
Is this on Jaunty or Karmic?

---

### Post by JoetteB on 2009-12-29
> **lidex said:**
> Is this on Jaunty or Karmic?

I'm running Linux Mint, which I think is Jaunty.

---

### Post by lidex on 2009-12-29
Close all instances of Firefox.
Try this command in a terminal:
```
firefox-3.5 -profilemanager
```

Choose a new profile and start with that.

Edit: Alt+F2 run box would be better than terminal

---

### Post by lidex on 2009-12-29
I removed Firefox 3.0 all together. I believe Shiretoko is stable enough at this point and eliminates conflicts with profiles.

---

### Post by JoetteB on 2009-12-29
I tried the Alt+F2 earlier (when I didn't know how to start Shiretoko from a command line), and tried running it from the terminal as suggested. No joy.

Lidex - until tonight, I would have said exactly the same thing. That Shiretoko was nice and stable and no need to keep FF 3.0 hanging around.

---

### Post by dcstar on 2009-12-29
> **JoetteB said:**
> I tried the Alt+F2 earlier (when I didn't know how to start Shiretoko from a command line), and tried running it from the terminal as suggested. No joy.

Lidex - until tonight, I would have said exactly the same thing. That Shiretoko was nice and stable and no need to keep FF 3.0 hanging around.

I have to admit that I'm going back to using FF 3.0.* again.

I have tried (again) to use FF 3.5/Shiretoko over the last couple of weeks and the little trip-ups just become too annoying (stupid things like the lack of Gnome font anti-aliasing).

Back to what I know works, and doesn't seem to be any "slower" either.

---

### Post by lidex on 2009-12-29
OK. Try this. Right-click on your Shiretoko entry in your main menu and add the launcher to the desktop. Right-click on that shortcut and select "properties". In the command box field copy the command and then paste into Alt+F2 run box. Add a space, then "-ProfileManager" (no quotes). Click run button. Make sure all Firefox instances are closed first!!

Alternately, use the "-safe-mode" option.

---

### Post by lidex on 2009-12-29
> **dcstar said:**
> I have to admit that I'm going back to using FF 3.0.* again.

I have tried (again) to use FF 3.5/Shiretoko over the last couple of weeks and the little trip-ups just become too annoying (stupid things like the lack of Gnome font anti-aliasing).

Back to what I know works, and doesn't seem to be any "slower" either.

I have to admit the fonts are not great (read: look terrible) but it has worked well for me in general. I'm using the ubuntu-mozilla-daily ppa; v 3.5.8 pre.

---

### Post by JoetteB on 2009-12-29
Eureka! I restarted (not the first time I've done so since all of this started) and tried again, and this time Shiretoko loaded up properly and informed me that I was now using 3.5.5

It must have been an update that hung up or something. It's working like a champ now. Chalk another one up to "turn it off and back on and see what happens".

---

### Post by JoetteB on 2009-12-29
> **lidex said:**
> I have to admit the fonts are not great but it has worked well for me in general. I'm using the ubuntu-mozilla-daily ppa; v 3.5.8 pre.

Yeah, I'm not a huge fan of the fonts. Many of them by default are a bit small for my aging eyes. Thankfully mozilla has given me an easy fix for that! I'm not one of those who starts frothing at the mouth when presented with comic sans, so generally actual font choice don't usually bother me, just the size.

Thanks again for everyone's help!

---

### Post by lidex on 2010-01-03
Found a pretty slick fix for fonts in 3.5.x. Very simply:
```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig
```

Restart Firefox.

---

