---
title: "how to change size of on-screen keyboard"
date: 2011-03-22
forum: General Help
---

### Post by robofighter on 2011-03-22
How do I change the default size of the on-screen keyboard on ubuntu netbook remix.

I have a Dell Inspiron Duo, it functions as a Tablet Hybrid in which its screen can flip out to look and act as a function as a Tablet. However when I bring up the on-screen keyboard to use for typing on tablet mode, it is often too small for finger input (computer does not use a stylus) Resizing will be too difficult. So I need to know how to increase the default size of the on-screen keyboard when it comes up.

Also how do I bring one up for the lock screen as well?

Also, the on-screen keyboard is a program called onboard.

---

### Post by Favux on 2011-03-22
Hi robofighter,

I'll quote from my mini HOW TO:  [http://ubuntuforums.org/showpost.php?p=7959338&postcount=8](http://ubuntuforums.org/showpost.php?p=7959338&postcount=8)
> For OnBoard use:
```
onboard -s 684x200 -x 170 -y 568 &
```
These values will display the onBoard at about 2/3 the screen width at the bottom.  The -s settings control size and the -x and -y values control location.  You can experiment with them.  For example a smaller keyboard in a different location:  -s 500x130 -x 15 -y 15 &

---

