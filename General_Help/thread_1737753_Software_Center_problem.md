---
title: "Software Center problem"
date: 2011-04-23
forum: General Help
---

### Post by Charobnjak on 2011-04-23
First of all, altho I am not really new to ubuntu since I had it for time now I still don't know a lot about it since I was not really interested in exploring it and probably won't understand some of the terms used so go easy on me

Now, since I have upgraded to ubuntu 10.10 (maverick) (maybe even earlier since I haven't been using it much) I have not been able to open Software Center. Trying to openit through terminal gave me the following result:

```

Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 145, in __init__
    self.history = get_apt_history()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 178, in get_apt_history
    apt_history = AptHistory()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 83, in __init__
    self.rescan()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 98, in rescan
    self._scan(history_gz_file)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 116, in _scan
    trans = Transaction(stanza)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 59, in __init__
    "%Y-%m-%d  %H:%M:%S")
  File "/usr/lib/python2.6/_strptime.py", line 270, in <module>
    _TimeRE_cache = TimeRE()
  File "/usr/lib/python2.6/_strptime.py", line 188, in __init__
    self.locale_time = LocaleTime()
  File "/usr/lib/python2.6/_strptime.py", line 70, in __init__
    self.lang = _getlang()
  File "/usr/lib/python2.6/_strptime.py", line 29, in _getlang
    return locale.getlocale(locale.LC_TIME)
  File "/usr/lib/python2.6/locale.py", line 497, in getlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: sr_RS

```

I have searched through other problems like this on the forums but none of the solutions were working for me so I hope there is someone here that can help me.

---

### Post by gufide on 2011-04-24
hmm... Someone good in python debugging may be able to answer to you... but I'm not very good in this domain...

---

### Post by Charobnjak on 2011-04-24
Thanks for replying.

So I have to wait for someone good with python to see this thread >.>. Hopefully it will be soon...

---

### Post by Charobnjak on 2011-04-24
noone?

---

### Post by ninjawhite on 2011-04-26
That is a Python bug, related with character encoding for some locale leangue setings. It seems that it is not fixed yet.       ( Ovo je direktno vezano za podešavanja lokalnog  jezika. U pitanju je Srpski. I dalje se može koristiti update putem konzole a i instalacija i deinstalacija programa)

---

### Post by matt_symes on 2011-04-26
Hi

What your locale information ? Open a terminal and type

```
locale
```

Post back results.

Kind regards

---

### Post by ivanovnegro on 2011-04-26
Thats really bad, I thought Ubuntu can handle Serbian.
You could try to change your locale and then log out and log in to see if you can use the Software Center.
You might file it as a bug maybe if this problem persists.

---

### Post by KegHead on 2011-04-26
Hi!

Have you tried to load via synaptic?

System...admin..synaptic..."software"

KegHead

---

### Post by Charobnjak on 2011-04-26
Hi!

> **matt_symes said:**
> Hi

What your locale information ? Open a terminal and type

```
locale
```Post back results.

Kind regards

```

LANG=sr_RS
LC_CTYPE="sr_RS"
LC_NUMERIC="sr_RS"
LC_TIME="sr_RS"
LC_COLLATE="sr_RS"
LC_MONETARY="sr_RS"
LC_MESSAGES="sr_RS"
LC_PAPER="sr_RS"
LC_NAME="sr_RS"
LC_ADDRESS="sr_RS"
LC_TELEPHONE="sr_RS"
LC_MEASUREMENT="sr_RS"
LC_IDENTIFICATION="sr_RS"
LC_ALL=

```

I see that Ivan suggested I change my locale, but how do I do that?

> **KegHead said:**
> Hi!

Have you tried to load via synaptic?

System...admin..synaptic..."software"

KegHead

I don't quite understand what do you mean? Synaptic works for me and I tried reinstalling software center through it many times and it didn't help at all.

---

### Post by ivanovnegro on 2011-04-26
To change the locale, first go to System-> Administration-> Region/Languages, something like this, Im on KDE so its a bit different and then there you can add new languages or just take English, I think its preinstalled, apply it as your system language and then logout/in and try the Software Center again.
It is really strange anyway but could you try also to switch to the locale "rs Latin", maybe it helps, its the same you can add it in the language settings and it will update the system adding everything needed tu run in another language environment. But apply it as the system wide language.

Edit: If Ninjawhite is right then this should be a bug in Python and you have to wait until a fix, in the meantime it seems you can only use Synaptic for removing and installing software, its basically the same.

---

### Post by Charobnjak on 2011-04-26
SOLVED! :D 

When I opened system>administration>language support it  said that language support wasn't completely installed and then it asked me if I want to download and install it now. When it installed I just reloged and it worked perfectly(even tho I didn't change the language, it's still serbian) :D

Thanks to all of you who helped me :D

---

### Post by ivanovnegro on 2011-04-26
> **Charobnjak said:**
> SOLVED! :D 

When I opened system>administration>language support it  said that language support wasn't completely installed and then it asked me if I want to download and install it now. When it installed I just reloged and it worked perfectly(even tho I didn't change the language, it's still serbian) :D

Thanks to all of you who helped me :D

Ah, yes, indeed man, I forgot to say that, thats normally one of the first things I do when I install fresh after updating the system, later I update the locale and it applies some updates also to the general language support. This helps to have for example the dictionary in OpenOffice/Libre Office for Serbian or whatever language, so there is no bug.

---

