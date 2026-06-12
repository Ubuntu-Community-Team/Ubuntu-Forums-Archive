---
title: "I need to delete Firefox, don't know how."
date: 2010-06-21
forum: General Help
---

### Post by zaktan71 on 2010-06-21
Well um, I looked up 2girls1cup and the website won't let me close the browser, every time I force quit it and open it again, the same page keeps poping up. So I need to know how to delete Firefox or I need to know how to close it and have it go to my homepage again, if there is like a setting for that or something. Please help!

---

### Post by Leppie on 2010-06-21
try deleting the firefox profile directory, this will also delete any add-ons you may have installed:
```
rm -Rf .mozilla/firefox/*.default
```
after that, firefox should create a new profile folder when launching first time.

otherwise you could try to purge firefox:
```
sudo aptitude purge firefox
```

---

### Post by zaktan71 on 2010-06-21
> **Leppie said:**
> try deleting the firefox profile directory, this will also delete any add-ons you may have installed:
```
rm -Rf .mozilla/firefox/*.default
```
after that, firefox should create a new profile folder when launching first time.

otherwise you could try to purge firefox:
```
sudo aptitude purge firefox
```


Wait whoa? How do I delete the profile directory, or purge. Im a major Ubuntu newb. I'm sorry I asked this stupid question though, I shouldn't have looked it up.

---

### Post by Leppie on 2010-06-21
i gave you the commands to issue for those operations. you will have to issue those commands in a terminal, go to Applications>Accessories>Terminal
then copy and paste the first command into the terminal and hit enter ;)

the first command will remove the profile folder, the second will remove firefox completely from your system.

---

### Post by zaktan71 on 2010-06-21
You, my dear sir, are a GOD.

---

### Post by Leppie on 2010-06-21
> **zaktan71 said:**
> You, my dear sir, are a GOD.
well no... a leprechaun possibly...
but, did this solve your issue?

---

### Post by zaktan71 on 2010-06-21
Yes it did work. Im soo happy now. Now can I install it again and have it be back to normal?

---

### Post by Leppie on 2010-06-21
you should be able re-install it without too much problems.
not sure though what it was that they did to your machine.
anyways, to re-install firefox, just issue this command in a terminal:
```
sudo aptitude install firefox
```

---

### Post by wilee-nilee on 2010-06-21
Let me show you something, the round colored icons are from the WOT web of trust FF ad on anything but green has been reported to be a problem install wot and watch where you click. You aslo should at the least have noscript installed to block flash.
[ATTACH]161150[/ATTACH]

---

### Post by warfacegod on 2010-06-21
> **Leppie said:**
> well no... a leprechaun possibly...
but, did this solve your issue?

@zaktan71: He's right, I'm the only god around here.

Please be a little more careful in the future. Using Linux isn't entirely without it's risks. It's not nearly as bad as Windows but still...:p

Here's an idea. Open the Edit menu> select Preferences> General tab> under Startup> make sure it ***doesn't*** say "Show my windows and tabs from last time". This might help to prevent this from happening again.

---

### Post by wilee-nilee on 2010-06-21
@the only god;) installing bleachbit will scrub that baby clean and should be used often. Personally I have FF set to save nothing and always be private with numerous addons.

---

### Post by warfacegod on 2010-06-21
You can't give away *all* the secrets in one go, hoss. SHEESH!

---

### Post by Leppie on 2010-06-21
another very good addon is betterprivacy, deletes flash cookies (which otherwise are horribly persistent).

---

### Post by wilee-nilee on 2010-06-21
> **Leppie said:**
> another very good addon is betterprivacy, deletes flash cookies (which otherwise are horribly persistent).

And ghostery to keep those trackers at bay.
@warfacegod thats my job.
[ATTACH]161152[/ATTACH]

---

### Post by warfacegod on 2010-06-21
AdblockPlus is a good place to start. NoScript is another.

---

### Post by Leppie on 2010-06-21
i use trackmenot as well...
and googlesharing is great as well, though not very compatible with the google toolbar...

---

### Post by qweabab1 on 2010-06-25
I tried it but failed

---

### Post by Leppie on 2010-06-25
> **qweabab1 said:**
> I tried it but failed
what have you tried, and what didn't work?
and actually, what is the issue you're having?

---

### Post by warfacegod on 2010-06-25
> **qweabab1 said:**
> I tried it but failed

Well you know what they say; try, try, again and all that.

Right now I suggest trying to provide details. Lots and lots of details. What the problem is. What you have tried. And anything else you think might be helpful.

---

