---
title: "Google Chrome scrollbars buggy?"
date: 2011-10-21
forum: General Help
---

### Post by tpprynn on 2011-10-21
Is it just me (on four different computers and possibly three times as many operating systems) or is there a problem with the current Google Chrome's scrollbars. If I hover the mouse over them and try to drag, half the time nothing will happen. It seems to vary, and from site to site - it's not working right now on this site. I was thinking that Chromium seemed fine, but it seems to happen sometimes there too, though not as often. Never with Firefox or Opera though, which I don't use for very many other reasons...

Should I be looking for a Chrome forum at Google or somewhere or can someone solve this for me here? Does Chrome have anything like Firefox's about:config that can be meddled with? There's nothing relevant in the Preferences.

Thanks.

---

### Post by vasa1 on 2011-10-21
Google Chrome 14.0.835.202 (Official Build 103287) on 11.10 (Unity 3D)

No problems at all on any sites with scrollbars. I've made my own minimalistic ones by putting this code into ~/.config/google-chrome/Default/User StyleSheets/Custom.css
```
::-webkit-scrollbar { height: 6px; width: 6px; background: inherit; }
::-webkit-scrollbar-thumb { background: maroon; -webkit-border-radius: 1ex; }

```

---

### Post by tpprynn on 2011-10-21
Interesting. I tried your scrollbars and the problem is gone! They are a bit too impractically slim for me but I'll amend them a little bit, quite pleased to learn something new too! I'll mark this solved if all remains well after a couple of days.

I wonder if my issue has anything to do with the browser interacting badly with my gtk theme or something like that. I was thinking that it wouldn't be why, because Chrome and Chromium seem to use mostly their own elements.

Thanks.

---

### Post by vasa1 on 2011-10-21
> **tpprynn said:**
> ...They are a bit too impractically slim ...
I purposely kept them slim but with a strong color, since I mostly scroll up or down without really grabbing the "thumb". I slam the mouse cursor against the right hand side of the screen above or below the thumb and then click (I mostly browse in a maximized window). That's why I didn't make the scrollbar wide.

For better or worse, the scroll overlay thing hasn't yet come to Chrome. When that happens ...

---

