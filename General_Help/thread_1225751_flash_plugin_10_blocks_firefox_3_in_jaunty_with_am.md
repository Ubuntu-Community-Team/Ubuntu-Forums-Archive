---
title: "flash plugin 10 blocks firefox 3 in jaunty with amd64"
date: 2009-07-28
forum: General Help
---

### Post by juancarlosun on 2009-07-28
Hi friends,
I have Jaunty, AMD64, Firefox 3, and (the experimental) flash plugin 10 for amd64.  And I have the next problem:  when I open any web page WITH FLASH (yahoo, youtube, etc.), my Firefox Browser CRASH in any moment, and I have to restart it.

What's a posible solution?

Thanks a lot!

---

### Post by Java Geek on 2009-07-28
What is you system type? I'm assuming 64 bit...? It could be simply because the plugin is experimental that there are browser crashes. Try another plugin to see if that fixes the problem

---

### Post by drs305 on 2009-07-28
Many of us have run Firefox and Adobe Flash 10 Alpha without any problems. I suggest you use Kilz' Get64bitFlash (64-bit Flash Alpha link) script from the following post. If I remember correctly it will remove all your current flash installs and install the current Adobe Flash 10 Alpha automatically:
[http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

Welcome to the Ubuntu forums.  :-)

---

### Post by QIII on 2009-07-28
Many possible solutions.

Here are two to try:

1.  Remove swfdec and gnash if they are installed.  They cause conflicts with Flash.  If that works, stop there.

2.  Start Firefox in safe mode from the terminal to disable plug-ins

```
firefox -safe-mode
```

or 

```
firefox-3.5 -safe-mode
```

If you don't get any crashes (you won't be able to use Flash, of course), start enabling your plugins one at a time to see if one of them is the culprit.


No guarantee, of course.  Just a couple of things to eliminate potential sources of problems.

---

### Post by juancarlosun on 2009-07-29
Thanks for your answer!  I didn't know the safe-mode for firefox.

> **QIII said:**
> Many possible solutions.

Here are two to try:

1.  Remove swfdec and gnash if they are installed.  They cause conflicts with Flash.  If that works, stop there.

2.  Start Firefox in safe mode from the terminal to disable plug-ins

```
firefox -safe-mode
```

or 

```
firefox-3.5 -safe-mode
```

If you don't get any crashes (you won't be able to use Flash, of course), start enabling your plugins one at a time to see if one of them is the culprit.


No guarantee, of course.  Just a couple of things to eliminate potential sources of problems.

---

### Post by juancarlosun on 2009-07-29
Hi drs305,

I was use your solution; it removes acroread too !!  jejeje, no problem, there is okular, kpdf, evince, etc.

Within 1 hour no problems with youtube and other flash pages.  Up to here, everything goes well......

Thank you very much !!  And thanks for your welcome.

> **drs305 said:**
> Many of us have run Firefox and Adobe Flash 10 Alpha without any problems. I suggest you use Kilz' Get64bitFlash (64-bit Flash Alpha link) script from the following post. If I remember correctly it will remove all your current flash installs and install the current Adobe Flash 10 Alpha automatically:
[http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

Welcome to the Ubuntu forums.  :-)

---

### Post by drs305 on 2009-07-29
juancarlosun,

I didn't recall that the script uninstalls acroread. You can reinstall it and it should not affect your flash settings. (I have both and flash works fine).

Glad you have your Flash now. :-)

---

