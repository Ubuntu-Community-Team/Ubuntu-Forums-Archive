---
title: "How to deal with npviewer.bin"
date: 2009-09-17
forum: General Help
---

### Post by FiReSTaRT on 2009-09-17
From the homework that I've been doing and personal experience, this process goes nutso (takes up 20-50% of CPU usage) on 64-bit Ubuntu when running Flash on Firefox. Up until now, I'd open System Monitor, scroll to it, click on it and click on End Process. 
After reading a thread in the archives, I came across some command line solutions [http://ubuntuforums.org/showthread.php?t=647961](http://ubuntuforums.org/showthread.php?t=647961) I figured, why not make it easy? Just create a launcher with the **killall npviewer.bin** command and click on it every time you hear the fan goin' crazy.
[IMG]http://img33.imageshack.us/img33/1702/screenshotyk.png[/IMG]

---

### Post by elphaba on 2009-09-18
I'm having similar problem and have also done some research.  Looks like this problem has been around a while, at least since early 2008.

I did a "top" and saw npviewer listed as hogging the cpu.  

I like your idea and have implemented it. Thanks.

---

### Post by philinux on 2009-09-18
If it's the 32bit plugin on 64 bit giving headache then uninstall it and
try the 64 bit plugin from adobe.

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

### Post by FiReSTaRT on 2009-09-21
AFIK it's not running under the wrapper. I'd figure that the stock FF install would automatically install the apropriate driver, unless I'm WAY off and there are some issues with the 64bit driver that I'm not aware of. I try to keep my system and packages relatively stock unless there are serious functionality issues (don't get me started on suspend) or I'm helping a developer test something.
This method at least turns a major annoyance into a minor one.

---

### Post by FiReSTaRT on 2009-12-03
If you're also running Opera, this command in the launcher will take care of both browsers in 1 shot:
> killall -9 npviewer.bin /usr/lib/opera/operapluginwrapper-ia32-linux /usr/lib/flashplugin-installer/libflashplayer.so
I click on it every time I hear the fan come on :D

---

### Post by Defrector on 2009-12-15
I can totally vouch on the npviewer issues as I have been experiencing them for quite a while. Here's the story as I understand it:

Adobe makes a 32-bit and 64bit version of flash for linux/mozilla. Their 32-bit version is more or less considered stable and their 64-bit versions have been in alpha most of the time. At the time of this reply, 64-bit  ubuntu's flashplayer-nonfree package installs the 32-bit version and then uses npviewer (or nsplugin) to adapt it to work in 64bit land.

In my view this adapter is a real pain in the bottom. It may end up hogging memory, using up CPU, freezing up the browser, crashing flash altogether and resulting in blank boxes until the browser is restarted, hanged processes, the whole nine yards.

So why do we even waste our time adapting the 32-bit version to work in 64-bit?

My best guess is that it is hit-and-miss with the 64-bit version of the plugin: either it works well or not at all. It is possible to remove the ubuntu-installed flash, do a search for "flash plugin, ubuntu 64-bit alpha" and some relevant links come up, particularly, look for a 64-bit download from the adobe site. I have successfully used the alpha version before. After upgrading to 9.10, nsplugin was back. Removing the 32-bit flash and installing the 64-bit flash resulted in unusable problems-this doesn't mean it won't work for you though.

I pray for the hypothetical day when Gnash manages to trivialize the Adobe problem.

---

### Post by jsilve1 on 2009-12-17
FWIW, the 64 bit plugin is here:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Haven't tried it yet so can't speak to its quality. But npviewer.bin is killn' me.

---

### Post by stivakos on 2010-01-01
Or, if you run Compiz, you can assign a key combination to execute the command "killall npviewer.bin". My combination is Alt+z so it becomes handy when the cpu usage getting high.

System -> Preferences -> CompizConfig... -> in "General" group you choose "Commands". Then it's easy to deal with it.

Hope it helps...

---

### Post by cnbiz850 on 2010-05-16
> **jsilve1 said:**
> FWIW, the 64 bit plugin is here:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Haven't tried it yet so can't speak to its quality. But npviewer.bin is killn' me.


Tried the 64bit version.  npviewer is gone, but instead, Firefox take about 40% of CPU nearly constantly with 30 tabs open.  Then I installed flashblock extension, it is now down to about 5%.

---

### Post by rickrich on 2010-08-27
> **FiReSTaRT said:**
> From the homework that I've been doing and personal experience, this process goes nutso (takes up 20-50% of CPU usage) on 64-bit Ubuntu when running Flash on Firefox. Up until now, I'd open System Monitor, scroll to it, click on it and click on End Process. 
After reading a thread in the archives, I came across some command line solutions [http://ubuntuforums.org/showthread.php?t=647961](http://ubuntuforums.org/showthread.php?t=647961) I figured, why not make it easy? Just create a launcher with the **killall npviewer.bin** command and click on it every time you hear the fan goin' crazy.
[IMG]http://img33.imageshack.us/img33/1702/screenshotyk.png[/IMG]

Do you have an icon for this????

---

