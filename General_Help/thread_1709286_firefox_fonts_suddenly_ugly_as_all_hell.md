---
title: "firefox fonts suddenly ugly as all hell"
date: 2011-03-18
forum: General Help
---

### Post by bobdobbs on 2011-03-18
Hi all.

I updated my system via apt-get. I noticed that new firefox packages had installed. So I restarted ff.

Upon restart, system fonts on web pages being displayed by ff are very ugly.

Solutions that I've tried:
I found links indicating that creating a .fonts.conf file would help, and tried a couple of pasted discovered files that people purported to fix the problem.
No luck.

One post in a bug report from 2010 indicated that the problem could be fixed by clearing a fontconfig cache file and running dpkg-reconfigure fontconfig.
This did not work.

I installed and ran ff-4.0 and swiftfox. They also have the same problem.

What is going on here, and how do I fix it?

---

### Post by Krytarik on 2011-03-18
Does it look similar to this?:
[http://ubuntuforums.org/showthread.php?t=1666744](http://ubuntuforums.org/showthread.php?t=1666744)

You may check/try some of those things we tried, so far also unsuccessful, but maybe it works for you.

---

### Post by bobdobbs on 2011-03-18
> **Krytarik said:**
> Does it look similar to this?:
[http://ubuntuforums.org/showthread.php?t=1666744](http://ubuntuforums.org/showthread.php?t=1666744)

You may check/try some of those things we tried, so far also unsuccessful, but maybe it works for you.

Yes, thanks.
That's the same problem.

I will  transfer my attention on this issue over to that thread.

---

### Post by seawolf167 on 2011-03-18
Just to ensure it isn't an easy fix - your font settings in Tools -> Options -> Content -> Fonts & Colors is set correctly?

---

### Post by bobdobbs on 2011-03-18
> **seawolf167 said:**
> Just to ensure it isn't an easy fix - your font settings in Tools -> Options -> Content -> Fonts & Colors is set correctly?


Hi Seawolf.

I don't have a 'tools' menu.

---

### Post by Krytarik on 2011-03-18
> **bobdobbs said:**
> Hi Seawolf.

I don't have a 'tools' menu.
*seawolf167* seems to actually mean "Edit -> Preferences -> Content -> Fonts & Colors" (at least in the en-US version of Firefox).

Does the issue relate only to the displayed websites or also to the menus and such?

---

### Post by bobdobbs on 2011-03-18
> **Krytarik said:**
> *Seawolf* seems to actually mean "Edit -> Preferences -> Content -> Fonts & Colors" (at least in the en-US version of Firefox).

Does the issue relate only to the displayed websites or also to the menus and such?

Thanks.

Those settings seem to be fine.

As far as I can tell, the issue only seems to relate to displayed websites. 
The fonts on the menus and on the toolbars and such seem to be fine.

---

### Post by thenickrulz on 2011-03-18
Just use chromium i am just starting to use it and it is a lot better than Firefox... you can even import your bookmarks so u can save all that hassle of having to get them again...:D

---

### Post by bobdobbs on 2011-03-18
> **thenickrulz said:**
> Just use chromium i am just starting to use it and it is a lot better than Firefox... you can even import your bookmarks so u can save all that hassle of having to get them again...:D

I need firefox for web development.

I also seem to have the same exact problem with chromium.

---

### Post by bobdobbs on 2011-03-20
bump

---

### Post by Krytarik on 2011-03-20
Please re-check if you a "~/.fonts.conf" in your home directory, and if so, rename it.

---

### Post by bobdobbs on 2011-03-21
> **Krytarik said:**
> Please re-check if you a "~/.fonts.conf" in your home directory, and if so, rename it.

Do you mean "rename it to something random, so that it gets ignored"?
Or "give it the correct name"?

Temporarily removing the file (and putting it into a backup dir) and then restarting ff, the problem still exists.

If the latter, what should I rename it to?

---

### Post by Krytarik on 2011-03-21
Yeah, I meant the first one, otherwise I would have given you the name. ;-)

It's a bummer, I stay on this.

---

### Post by pickarooney on 2011-03-21
> **thenickrulz said:**
> Just use chromium i am just starting to use it and it is a lot better than Firefox... you can even import your bookmarks so u can save all that hassle of having to get them again...:D

If it's hideous fonts you want, Chromium can't be beaten :D

---

### Post by Krytarik on 2011-03-22
> **Krytarik said:**
> *seawolf167* seems to actually mean "Edit -> Preferences -> Content -> Fonts & Colors" (at least in the en-US version of Firefox).

Which fonts do you have actually chosen there?

Also, check the font settings of KDE, especially regarding GTK apps and anti-aliasing. I guess you have to re-login after each change.

---

### Post by bobdobbs on 2011-03-27
> **Krytarik said:**
> Which fonts do you have actually chosen there?

serif, at 16px.
This is the default setting.

> **Krytarik said:**
> 
Also, check the font settings of KDE, especially regarding GTK apps and anti-aliasing. I guess you have to re-login after each change.

Are you sure I'd have to check these?
I haven't touched these settings, and the problem only exists in my browsers. (firefox and chrome).
The problem only popped up after I updated the ms core fonts package during an 'apt-get dist-upgrade'.

Also, the problem exists even if I'm using gnome or xfce4.

---

### Post by Krytarik on 2011-03-27
> **bobdobbs said:**
> serif, at 16px.
This is the default setting.

I was more meaning the "Advanced..." settings there.
> **bobdobbs said:**
> 
The problem only popped up after I updated the ms core fonts package during an 'apt-get dist-upgrade'.

Did you already try re-installing it, like I suggested in the other thread?:

1.) Make sure that it has been configured:
```
sudo dpkg --configure a
```
2.) Re-install it:
```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```
To confirm the upcoming dialog press Tab to jump to <Ok>, then press Enter/Return.

---

### Post by bobdobbs on 2011-03-28
> **Krytarik said:**
> I was more meaning the "Advanced..." settings there.


Apologies, but I can't seem to find advanced settings for fonts.
Where can I find this?

[QUOTE=Krytarik;10606595
Did you already try re-installing it, like I suggested in the other thread?:
[/QUOTE]

Yes. I did an apt-get purge, restarted X, reinstalled, and then restarted X again. No luck.


The ugly font problem is driving me batty.
Whats my next move?

---

### Post by Krytarik on 2011-03-28
> **bobdobbs said:**
> Apologies, but I can't seem to find advanced settings for fonts.
Where can I find this?
See attached screenshots.
> **bobdobbs said:**
> 
Yes. I did an apt-get purge, restarted X, reinstalled, and then restarted X again. No luck.

Did the mentioned confirmation dialog come up?
Did you confirm it?

Please run this command, to be sure:
```
sudo dpkg --configure -a
```

---

### Post by Copper Bezel on 2011-04-20
Hey, thanks for linking me here, Krytarik.

bobdobbs, for some reason, installing KDE alongside Gnome causes Gnome to render Qt parts with default (KDE) settings instead of the ones specified in KDE. However, you can force Qt subpixel font smoothing to work by installing the package qt4-qtconfig, which can be run with the command qtconfig. This will fix Firefox's font rendering. (Incidentally, Chromium *also* uses Qt rendering, so switching wouldn't have helped.)

You can also use it to conform (fully) Qt apps to your GTK+ widget style.

---

