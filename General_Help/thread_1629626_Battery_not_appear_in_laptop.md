---
title: "Battery not appear in laptop"
date: 2010-11-23
forum: General Help
---

### Post by yiannis66 on 2010-11-23
My battery Icon dosn't showup.
I did ```
gnome-power-manager
```
I recieve back ```
(gnome-power-manager:7752): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9dc3c70'
TI:20:33:45   TH:0x9d5f6d8   FI:gpm-main.c   FN:main,250
- Power Manager is already running in this session.
Traceback:
   gnome-power-manager() [0x806487b]
   gnome-power-manager() [0x80574b2]
   /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x3b9bd6]
   gnome-power-manager() [0x804ebc1]
```
and I also did
```
killall gnome-power-manager
gnome-power-manager --verbose
``` 
and the resolt is
[http://pastebin.com/uzVkcYQm]("http://pastebin.com/uzVkcYQm")
How can we fix that small proplem?

---

### Post by yiannis66 on 2010-11-24
at the and is not so small proplem!!!!

---

### Post by bobcollard on 2010-11-24
I know you are  running Gnome, but I remember it having a Power Management preference similar to the one below.  Check to see if the part labeled "If Battery is Present" is on?

---

### Post by yiannis66 on 2010-11-24
thnks for the replay.
I give alt+f2 ,in the window I give gnome-power-manager
and nothing is happen . I can't find any like yours.

---

### Post by bobcollard on 2010-11-25
In the Panel under System there should be Preferences and under that should be Power Manager, not sure of name.  Click that and it should come up with a menu something like mine.  Like I said, I don't have Gnome so not sure of exact location.

---

### Post by Rockroehre on 2010-11-25
I'm running ubuntu 10.10 (maverick), but I think it should be the same for lucid: Go to System > Preferences > Power Management, like bobcollard said. Choose the tab "General". Under the heading "Notification Area" there are options for the icon display. Choose what suits you best, hit "close" and your problem should be solved.

---

### Post by yiannis66 on 2010-11-25
&#927;.&#922; &#921; I find it,but is not working at all.
I give ```
$ apt-cache policy battery-status
```
and I have back ```
W: Unable to locate package battery-status
```

---

### Post by bobcollard on 2010-11-25
```
sudo apt-get install battery-stats
```
```
sudo apt-cache policy battery-stats
```

---

### Post by wangsuda on 2010-11-25
I don't know if this will work, but it won;t do any harm:

1. Press Alt + F2, to open run apllication
2. Type gconf-editor and uncheck / apps / gnome-power-manager / notify

---

### Post by yiannis66 on 2010-11-26
I did that you said bobcollard:
```
 Installed: 0.3.5-1ubuntu1
  Candidate: 0.3.5-1ubuntu1
  Version table:
*** 0.3.5-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ lucid/universe Packages
        100 /var/lib/dpkg/status
```
This is what I get but nothing in the icon yet.

---

### Post by bobcollard on 2010-11-26
Sorry, I'm confused.  Are you trying to find the battery status via the icon in the Panel or Terminal?  We give you installation for Icon you look things up in terminal.  We give you Terminal Commands you look in Icon.  Perhaps it is a language barrier?

For the Icon:  Go to System > Preferences > Power Management. Choose the tab "General". Under the heading "Notification Area"  there are options for the icon display. Choose what suits you best, hit  "close" and your problem should be solved.

---

### Post by yiannis66 on 2010-11-26
Sorry,I know my english are not the best.
I try to help us much I can:
So at the moment I have the Icon of Battery but dosen't show me detals about the status of battery.

---

### Post by bobcollard on 2010-11-26
> **yiannis66 said:**
> Sorry,I know my english are not the best.
I try to help us much I can:
So at the moment I have the Icon of Battery but dosen't show me detals about the status of battery.
Hover your mouse pointer over the icon, don't click on it.

---

### Post by yiannis66 on 2010-11-27
Nothing happens when I do  it,Only when I left click shows that is always charged[IMG]http://img256.imageshack.us/img256/5931/screenshotmu.jpg[/IMG]

---

### Post by bobcollard on 2010-11-28
Good, so you get results.  It will not tell you that unless you click on it.  At least it works.  Anything else I can help you with?

---

### Post by yiannis66 on 2010-11-28
The proplem now is that dosen't show anythink else of that,
Always the same like you see in screenshot.

---

### Post by johnbrown678 on 2010-11-28
This is the same problem, which I am facing. the above mentioned solutions are not working for my laptop.

---

### Post by bobcollard on 2010-11-28
What other information are you looking for this icon to give you?  That is all it does.  In my bar it says "Battery 100% Running on AC Adapter"  That's it.

---

### Post by asvestomix on 2010-11-28
I think he means it doesn't show  how much battery life remaining..
It just says full all the time

---

### Post by bobcollard on 2010-11-28
> **asvestomix said:**
> I think he means it doesn't show  how much battery life remaining..
It just says full all the time
That varies with the way you charge your battery and how far you discharge it before recharging it.  See this site for a Q&A:
[http://www.dell.com/content/topics/global.aspx/batteries_sitelet/en/batteries_faq?c=us&l=en&cs=19](http://www.dell.com/content/topics/global.aspx/batteries_sitelet/en/batteries_faq?c=us&l=en&cs=19)

---

### Post by yiannis66 on 2010-11-28
> I think he means it doesn't show how much battery life remaining..
It just says full all the time
Yes you are correct.
This site you give me is not helping coz is proplem in 
Ubuntu .
Also I but it in launchpand.

---

### Post by yiannis66 on 2010-12-05
I Solved the proplem folloing the [http://georgia.ubuntuforums.org/showthread.php?t=1495123&page=24]("http://georgia.ubuntuforums.org/showthread.php?t=1495123&page=24")
So after the update of the Bios everything is O.K
Thanks for the help

---

