---
title: "Opera 10.10 and no flash"
date: 2009-11-27
forum: General Help
---

### Post by jamesobooth on 2009-11-27
Wasn't sure where else to post this, so here goes


I for the life of me cannot get flash running with Opera 10.10 on 32 bit 9.04.

I have tried the plugin from adobe's web site, the adobe plugin from the repositories, and the flashplugin-nonfree from the repositories.

I've made sure that the plugin is in the correct folder(s):
/usr/lib/opera/plugins
/usr/lib/flashplugin-installer
/usr/lib/adobe-flashplugin

I tried checking and unchecking the path to /usr/lib/mozilla/plugins as well

The libflashplayer.so file is there but opera won't see it!!!

I've made sure the paths are entered correctly in advanced - content - Plugin Oprions and verified permissions in the directories where the plugins are.

BAH!!!

---

### Post by NoaHall on 2009-11-27
Hm, my advice is to check whether it works with Firefox. If it does, reinstall it from FIREFOX, then try again.

---

### Post by TenPlus1 on 2009-11-27
remove all falsh plugins from your system via synaptic then search for:

adobe-flashplugin

and install that, works fine with Firefox and Opera...

---

### Post by wilee-nilee on 2009-11-27
Do you have java enabled in tools-preference-advanced content, it should be on but you never know.

---

### Post by rudy.b on 2009-11-27
I'm using Opera 10.10 with Flash working.  I installed it through the ubuntu-restricted-extras repository package and it worked without any tinkering on my part.

Checking my system, I see that the libflashplayer.so file is in /usr/lib/flashplugin-installer and Opera's plugin path is set to /usr/lib/opera/plugins:/usr/lib/flashplugin-installer:/usr/lib/mozilla/plugins.

---

### Post by jamesobooth on 2009-11-28
Yeah I've tried removing all flash then installing flash from the .deb I downloaded from Adobe, 
removed all flash again, sudo apt-get install adobe-flashplugin, 
remove all flash again, sudo apt-get install flashplugin-nonfree

Flash works fine with Firefox and Flock.

I made sure the libflashplayer.so was in the right directories and even copied it to /usr/lib/opera/plugins.

The paths are correct in Opera pref's
Java is enabled in Opera pref's as well.

I don't get it!

---

### Post by jamesobooth on 2009-11-28
How about this

Someone that has Opera 10 working, can you post what files you have in your:
/usr/lib/adobe-flashplugin or flashplugin-installer or flashplugin-nonfree 
and
your /usr/lib/opera/plugins folders?

---

### Post by darco on 2009-11-28
> **rudy.b said:**
> I'm using Opera 10.10 with Flash working.  I installed it through the ubuntu-restricted-extras repository package and it worked without any tinkering on my part.

Checking my system, I see that the libflashplayer.so file is in /usr/lib/flashplugin-installer and Opera's plugin path is set to /usr/lib/opera/plugins:/usr/lib/flashplugin-installer:/usr/lib/mozilla/plugins.

10.10 working fine w/above paths.

darco

---

### Post by rudy.b on 2009-11-28
> **jamesobooth said:**
> How about this

Someone that has Opera 10 working, can you post what files you have in your:
/usr/lib/adobe-flashplugin or flashplugin-installer or flashplugin-nonfree 
and
your /usr/lib/opera/plugins folders?

My /usr/lib/opera/plugins is empty and my /usr/lib/flashplugin-installer contains:
```

-rw-r--r-- 1 root root 10278616 2009-11-02 23:15 libflashplayer.so

```

---

### Post by Sioras on 2009-11-29
Hi,

I had trouble with flash, too. But the solution was pretty easy. I am running 9.10 64 bit and Opera 10.10 with Flash 10.

[http://ubuntuforums.org/showthread.php?t=1334756&highlight=9.10+64+bit+flash+opera]("http://ubuntuforums.org/showthread.php?t=1334756&highlight=9.10+64+bit+flash+opera")

I have done exactly as described on adobe page and it works!

Greets Sio

---

### Post by jamesobooth on 2009-12-02
UPDATE:

Flash still does not work in Opera 10.10.  I can't get Opera to recognize the plugin after trying everything listed above.

I also found out that Flock 2.5 is not properly running java.  "Something is wrong. Java is not working."

The only browser on my system running properly is Firefox.  It's running java and flash with no problems.

Guess I'll just stick with FF.  Bummed too.  I like Opera and Flock.

---

### Post by cmukialkra on 2009-12-02
I accept with file is in /usr/lib/flashplugin-installer 
and Opera's plugin path is set to
 /usr/lib/opera/plugins
:/usr/lib/flashplugin-installer
:/usr/lib/mozilla/plugins.

---

### Post by jamesobooth on 2009-12-02
> **cmukialkra said:**
> I accept with file is in /usr/lib/flashplugin-installer 
and Opera's plugin path is set to
 /usr/lib/opera/plugins
:/usr/lib/flashplugin-installer
:/usr/lib/mozilla/plugins.

Tried all possible combinations of the above paths.  Tried /usr/lib/firefox/plugins as well

---

### Post by stinkeye on 2009-12-02
Runs fine here.
Karmic and opera 10.10.
Dont know if it makes a difference but have you intalled sun java
```
sun-java6-jre
```
Some settings you might want to compare.
In the second screenshot there is an option to move up and down.
Maybe try putting */usr/lib/adobe-flashplugin* at the top.
I dont have a directory */usr/lib/flashplugin-installer*
So the solution might be to use [I]/usr/lib/adobe-flashplugin
[/I]

---

### Post by jamesobooth on 2009-12-03
uninstalled opera, flock, firefox and manually cleaned up all folders from usr/lib and ~/.opera, ~/.flock ...

uninstalled java
uninstalled flash

then reinstalled java and adobe-flashplugin

reinstalled FF
reinstalled flock
reinstalled opera

everything works.  I guess it's good to get java and all your plugins down before installing Opera.  I swear I did that before, but oh well.  This time it took!

---

### Post by ruario on 2009-12-19
Anyone else read this who is having problems, try [reading this]("http://my.opera.com/ruario/blog/flash-problems-on-linux").

---

