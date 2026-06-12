---
title: "How can I remove the keyboard icon from indicator applet?"
date: 2010-10-15
forum: General Help
---

### Post by -Ziggy- on 2010-10-15
This thread helped me to remove the mail icon from the indicator applet: 
[http://ubuntuforums.org/showthread.php?t=1470786](http://ubuntuforums.org/showthread.php?t=1470786).

But now I want to remove the ugly keyboard icon and its letters also, leaving just the sound and torrent icons. What should I do?

Thanks.

---

### Post by ubun_two on 2010-10-15
Are you talking about iBus icon?

If so, click on it, and go to Preference.  There is an option to remove it from the status bar.

---

### Post by -Ziggy- on 2010-10-15
> **ubun_two said:**
> Are you talking about iBus icon?

If so, click on it, and go to Preference.  There is an option to remove it from the status bar.

No, I'm not talking about that one. When you add the indicator applet you get three icons by default: sound, mail and keyboard. I want to take rid of the last one.

Thank you anyways.

---

### Post by VMC on 2010-10-15
I'm a little confused myself. Can you take a snapshot of the item you want removed.

---

### Post by -Ziggy- on 2010-10-15
> **VMC said:**
> I'm a little confused myself. Can you take a snapshot of the item you want removed.

Of course! 

[IMG]http://i146.photobucket.com/albums/r249/Tristan_Nieve/Pantallazo.png?t=1287187606[/IMG]

---

### Post by diafanos on 2010-10-16
oh, yes! this is really ugly and annoying. Using the faenza icon pack, the icon is getting even worse!

---

### Post by diafanos on 2010-10-16
I think, I just found a solution. Open gconf-editor and uncheck the
```

/apps/gnome_settings_daemon/plugins/keyboard/active

```

Log off and and the next time you will log in, the keyboard indicator will be gone.
I don't know if there is any drawbacks by doing this, but until now, everything works fine in my computer:)

---

### Post by -Ziggy- on 2010-10-16
> **diafanos said:**
> I think, I just found a solution. Open gconf-editor and uncheck the
```

/apps/gnome_settings_daemon/plugins/keyboard/active

```Log off and and the next time you will log in, the keyboard indicator will be gone.
I don't know if there is any drawbacks by doing this, but until now, everything works fine in my computer:)

Yay! That really solved the problem.

Definetly it was a very ugly icon. I won't miss it.

Thanks dude. : )

---

### Post by monkeyKata on 2010-10-17
> **diafanos said:**
> I think, I just found a solution. Open gconf-editor and uncheck the
```

/apps/gnome_settings_daemon/plugins/keyboard/active

```

Log off and and the next time you will log in, the keyboard indicator will be gone.
I don't know if there is any drawbacks by doing this, but until now, everything works fine in my computer:)

Is the entire keyboard selector gone, or is it still there and just the keyboard icon is removed?

---

### Post by -Ziggy- on 2010-10-17
> **monkeyKata said:**
> Is the entire keyboard selector gone, or is it still there and just the keyboard icon is removed?

The entire keyboard selector is gone, not just the icon. Anyways, that's what I wanted, I don't if there's another way to remove just the icon.

---

### Post by krstep on 2010-10-17
> **diafanos said:**
> I think, I just found a solution. Open gconf-editor and uncheck the
```

/apps/gnome_settings_daemon/plugins/keyboard/active

```

Log off and and the next time you will log in, the keyboard indicator will be gone.
I don't know if there is any drawbacks by doing this, but until now, everything works fine in my computer:)
This works, but I can't switch through languages with ALT + Shift now (yes it's setup, it worked before).
Anyway to solve this, or just remove the keyboard icon not the whole thing?

---

### Post by M.Saber on 2010-11-18
it worked but I use another language ( Arabic ) and i can't switch b/w Arabic and English so I restored it again  ......  really ugly icon to be in Ubuntu 10.10
I hope I can find a way to change it 

Ty

---

### Post by krstep on 2010-12-22
Bumping this thread.
Isn't there a way to return it to the small 3 letters like they were in 10.04?

---

### Post by Koala Kid on 2010-12-29
> **krstep said:**
> Bumping this thread.
Isn't there a way to return it to the small 3 letters like they were in 10.04?

bump. really annoying.

---

### Post by rockorequin on 2011-01-24
I agree, it's really annoying and takes up way too much room on the gnome-panel.

The trouble is that it's due to code that Canonical changed to move the keyboard indicator from the notification panel to Ubuntu's indicator applet, so it's not an upstream bug and Canonical doesn't care about it - I logged a bug for it at [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/631989](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/631989), but it has been marked wishlist.

---

### Post by Jony35359595 on 2011-07-20
[[img]http://s2.share.te.ua/333777/Screenshot.png[/img]](http://s2.share.te.ua/b333777/Screenshot.png)
1. in gconf-editor, check /desktop/gnome/peripherals/keyboard/indicator/showFlags
2. install set of flags using sudo apt-get install famfamfam-flag-png
3. make a softlink: ln -s /usr/share/flags/countries/16x11 ~/.icons/flags
In the next login, you should see flags in indicator applet.
You'r capt. ;)

---

### Post by rockorequin on 2011-07-20
> **Jony35359595 said:**
> [[img]http://s2.share.te.ua/333777/Screenshot.png[/img]](http://s2.share.te.ua/b333777/Screenshot.png)
1. in gconf-editor, check /desktop/gnome/peripherals/keyboard/indicator/showFlags
2. install set of flags using sudo apt-get install famfamfam-flag-png
3. make a softlink: ln -s /usr/share/flags/countries/16x11 ~/.icons/flags
In the next login, you should see flags in indicator applet.
You'r capt. ;)

Thanks! I didn't know about the famfamfam-flag-png package, I had manually downloaded flags from somewhere, but not all of them were present and the ones that were present were enormous and looked silly in the indicator - now it looks much better.

---

### Post by ljungkvist on 2012-02-07
In case anyone else on 11.10 are trying to do this without success, here's how I got it to work:

[http://ubuntuforums.org/showpost.php?p=11390956&postcount=6](http://ubuntuforums.org/showpost.php?p=11390956&postcount=6)

---

