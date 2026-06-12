---
title: "Why Firefox doesn't work as in Windows OS?"
date: 2010-11-23
forum: General Help
---

### Post by geek2330 on 2010-11-23
using ubuntu 10.10 and Firefox 3.6.12, while on a page i hit the backspace key on the keyboard and Firefox doesn't go back to the previous page......and yes i have focus in the page.

Also, while at a page if you use the mouse and click the address bar it does not highlight the entire url address, if i hit the F6 key then it does highlight the entire url.

This happens on 2 different ubuntu systems i have.

When using Firefox in Windows XP/Server these work, Backspace key will take you to previous page and clicking the address bar will highlight entire url.

Maybe something simple i am missing?

.

---

### Post by WorMzy on 2010-11-23
I'm inclined to say "because Ubuntu does it right", but that's just my opinion. The option to use the Windows style behaviour is there though, if you prefer. Simply browse to [about:config]("http://kb.mozillazine.org/About:config"), accept the disclaimer, and search for the following keys:
```
browser.backspace_action
browser.urlbar.clickSelectsAll
```

Set backspace action to "0" for history navigation; set clickSelectsAll to true for the self titled effect.

NOTE: In case you were wondering what the alternative key presses are, Alt+[Left Arrow] will take you backwards through your browsers history, and likewise, Alt+[Right Arrow] will take you forward.

Ctrl+L will select the Location bar and it's contents, or, as you have noticed, F6 will do so too.

---

### Post by geek2330 on 2010-11-24
that link is not valid, can you repost it please.

---

### Post by qamelian on 2010-11-24
> **geek2330 said:**
> that link is not valid, can you repost it please.
Just type: ```
about:config
``` in the browser address bar.

---

### Post by geek2330 on 2010-11-24
ahhh, thanks..!!

---

### Post by WorMzy on 2010-11-24
Yeah, apparently bbforums don't like colons.

[http://kb.mozillazine.org/About:config]("http://kb.mozillazine.org/About%3Aconfig")

---

### Post by Tosa on 2010-11-24
> **WorMzy said:**
> I'm inclined to say "because Ubuntu does it right"...

It may be so, but I prefer the Win way :p

Thank you for the hint!

---

