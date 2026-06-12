---
title: "Scroll with scroll wheel button"
date: 2010-05-02
forum: General Help
---

### Post by linmix on 2010-05-02
I have been looking all over the forum to find out how to use the scroll wheel button to scroll by moving the mouse.

I would like to be able to scroll by moving the mouse while holding the mouse wheel button down, preferably with varying speed depending on the mouse movement. 

BTW, I'm running Ubuntu 10.4

---

### Post by Exp HP on 2010-05-02
I believe this behavior is defined on a per-application basis.  The standard action for middle-click in Linux is to paste, and so developers for Linux consider that in their applications.

To get scrolling in Firefox, here's what you can do, though it requires going into advanced config:

Enter **about:config** into the address bar.
Click **"I'll be careful, I promise!"**
Type **autoScroll** into the filter.
It should bring you to _general:autoScroll_.
Double-click _general:autoScroll_ to make it **true**

Most applications don't have an option like this, unfortunately.  Hopefully you'll get used to it eventually. The middle-click paste is actually pretty convenient if you use it, because you never have to copy anything (just select and middle click)... but then again, you don't have to copy anything if you drag-and-drop paste, either, and that doesn't take up a mouse button, so I'm on the fence as to whether or not I like Linux's middle-click paste.  But you have to get used to it either way.

---

### Post by linmix on 2010-05-02
Just the thing I was looking for!

Actually FireFox is pretty much the only application I use this in. I had looked for mouse configuration entries in about:config, but hadn't seen this one yet.

The middle mouse button for pasting is also pretty awesome and works even after setting the scroll behaviour! Many thanks again.

---

