---
title: "Firefox with one gmail-window is taking 300Mb"
date: 2012-01-07
forum: General Help
---

### Post by alexei_ on 2012-01-07
Firefox with one gmail-window is taking 300Mb in Ubuntu 11.10 x64 after fresh restart. Is this expected?

---

### Post by xyzzyman on 2012-01-07
Mine uses 169 if I go right into gmail... But I have no extensions added as I am 99% of the time in Chrome. Extensions are what usually tack-on RAM.

---

### Post by alexei_ on 2012-01-07
Well, I have:
Addblock 
Firebug
Global Menu Bar integration
Memory restart
ViewSourceWith
Vimperator
Ubuntu Firefox Modifications

Still it does not makes sense for them to take 100Mb...
 10 years ago most desktops had less then 100Mb RAM...
 15 years ago 8Mb was enough for MS Windows with running applications...

---

### Post by bluexrider on 2012-01-07
open a terminal and type 'top' to see what what is happening. I personally use 'htop' which you can get from```
 sudo apt-get install htop 
```

---

### Post by alexei_ on 2012-01-07
I have htop for long time. There is something strange about it.
It actually shows 22 processes for firefox.
Each of them have exactly the same (except PID and CPU) properties which are:
PRI: 20
VIRT: 860M
RES: 295M
SHR: 14320
S: S
MEM%: 8

---

### Post by d3v1150m471c on 2012-01-07
you can set gmail to html only, btw.

---

### Post by alexei_ on 2012-01-07
> **d3v1150m471c said:**
> you can set gmail to html only, btw.
For "HTML only" I do not need FireFox (I could use elinks)

---

### Post by xyzzyman on 2012-01-07
> **alexei_ said:**
> 
Still it does not makes sense for them to take 100Mb...
 10 years ago most desktops had less then 100Mb RAM...
 15 years ago 8Mb was enough for MS Windows with running applications...

Windows XP could run on 64 but 10 years ago you were looking at 128-256MB's of RAM.

15 years ago you could run Windows 95 on 8MB's but 16-32 was more like it with some apps running. And no way could it have handled the websites now like gmail. The size of the code has increased 100 fold easily between all the HTML, CSS, javascript, ajax, etc...

Google Chrome breaks out it's RAM usage, and AdBlock in chrome is using 54MB's, flash plugin is using 19MB's, this ubuntuforums tab is taking up 61MB's, chrome itself 94MB's...

If you are on an older low-ram system, then Firefox/Chrome probably aren't for you and you should take a look at Dillo [http://www.dillo.org/](http://www.dillo.org/).

---

### Post by bluexrider on 2012-01-07
> **alexei_ said:**
> I have htop for long time. There is something strange about it.
It actually shows 22 processes for firefox.
Each of them have exactly the same (except PID and CPU) properties which are:
PRI: 20
VIRT: 860M
RES: 295M
SHR: 14320
S: S
MEM%: 8

In another terminal ```
sudo kill -9 'PID Number'
``` that will kill the running PID

restart firefox

---

### Post by alexei_ on 2012-01-08
> **bluexrider said:**
> In another terminal ```
sudo kill -9 'PID Number'
``` that will kill the running PID

restart firefox

Thanks, there is even a better way:
```

killall -9 firefox

```

---

### Post by bluexrider on 2012-01-08
Did that do any good?

---

### Post by alexei_ on 2012-01-08
Firefox restart apparently is needed from time to time... still FF takes too much of memory... With other app running 4Gb is not enough anymore. About 20-25% is taken by Firefox.

---

### Post by whatthefunk on 2012-01-08
I had the same problems and so switched to Opera.  Running at around 100 Mb at the moment with four tabs open and a video playing in one.

---

### Post by debd on 2012-01-08
[@alexei_]("http://ubuntuforums.org/member.php?u=1435809") with the add-ons you have its just normal.
and the gmail inbox itself is not quite a light page (xcept html only)..

---

### Post by lovinglinux on 2012-01-20
Hi,

I have 60+ add-ons installed and my Firefox starts with 220Mb. So I suspect it could be Firebug or Vimperator.

Keep in mind Firebug is a very slow extension in terms of startup and probably regular browsing. So if you don1t use it daily, I would recommend installing it on a separate profile or disable the extension until you nee it.

---

### Post by alexei_ on 2012-02-10
> **lovinglinux said:**
> 
 So I suspect it could be Firebug or Vimperator.


I have both of them. Vimperator for FF is what keeping me with FF. Similar "Vimperator" implementations for other browsers are not good.

BTW, I have FF (with all those plugins) also on Windows XP(32 bit) -- It is taking less them 400Mb with 40 opened tabs.

---

### Post by satnelav on 2012-02-12
I have this problem too. I've been able to use the previous versions of Firefox without too much hassle, but with the newest one (10) and the flash plugin enabled, my 512 MB RAM system can run nothing else, without the addons it is still 300 MB. This is very disappointing...

---

### Post by k999 on 2012-02-12
Make sure you disable firebug for the gmail website. You can customize that somewhere in firebug.

---

