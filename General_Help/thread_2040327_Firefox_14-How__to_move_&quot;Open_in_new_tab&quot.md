---
title: "Firefox 14-How  to move &quot;Open in new tab&quot; to top?"
date: 2012-08-10
forum: General Help
---

### Post by emarkay on 2012-08-10
I did a quick search, nothing recent - had some chrome edits for FF8, but AWAK, everyday is another chance to be updated (or is  that upgraded - Ubuntu needs to define that...), changing things here and there randomly...

---

### Post by Vaphell on 2012-08-10
'open in new tab' is the first option in my FF
besides why bother when you can middleclick or ctrl-click to do that?

---

### Post by vasa1 on 2012-08-10
> **emarkay said:**
> I did a quick search, nothing recent - had some chrome edits for FF8, but AWAK, everyday is another chance to be updated (or is  that upgraded - Ubuntu needs to define that...), changing things here and there randomly...

You should elaborate on your question rather than ^^^

---

### Post by emarkay on 2012-08-11
> **Vaphell said:**
> 'open in new tab' is the first option in my FF
besides why bother when you can middleclick or ctrl-click to do that?

No middle button on this mouse...

Strange.

---

### Post by emarkay on 2012-08-11
> **vasa1 said:**
> You should elaborate on your question rather than ^^^

The Q is: Firefox 14-How  to move "Open in new tab" to top?  
aaah never mind this old curmudgeon;  he who still loves those MS-DOS days...

---

### Post by vasa1 on 2012-08-11
```
This code in userChrome.css will move "Open Link in New Window" to the top of the context menu.
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* only needed once */
#contentAreaContextMenu > * { -moz-box-ordinal-group: 2; }
#context-openlink { -moz-box-ordinal-group: 1 !important; }

```
From: [https://support.mozilla.org/en-US/questions/791244#answer-147289](https://support.mozilla.org/en-US/questions/791244#answer-147289)

With a little imagination I suppose you could get what you want.

You can also search for Menu Editor in extensions like I did ;)
[https://addons.mozilla.org/en-us/firefox/addon/menu-editor/](https://addons.mozilla.org/en-us/firefox/addon/menu-editor/)

---

### Post by vasa1 on 2012-08-11
BTW, I've removed a lot of stuff I don't need from the right-click menu and have "Open link in new tab" as the topmost of the retained options. This is with Firefox 15 (beta):

---

### Post by Vaphell on 2012-08-11
> No middle button on this mouse...

Strange.

So you don't get to copy paste with highlight/middle-click either? One of the best features ever.
5 bucks and you have a generic mouse with scrollwheel acting as a middleclick.

you can still use ctrl/shift for new tab/window. Context menus are for noobs ;-)

---

### Post by pqwoerituytrueiwoq on 2012-08-11
usually if you left and right click at the same time it treats it as a middle click

---

### Post by vasa1 on 2012-08-11
> **Vaphell said:**
> ... Context menus are for noobs ;-)
We are the (oppressed) majority ;)

---

### Post by emarkay on 2012-08-14
Thanks all!

Old Skool Rulez... :)

---

### Post by vasa1 on 2012-08-14
> **emarkay said:**
> Thanks all!

Old Skool Rulez... :)

Hmmm ...

Let's see the thread title is: 
Re: Firefox 14-How  to move "Open in new tab" to top?
And it's marked [solved].

---

