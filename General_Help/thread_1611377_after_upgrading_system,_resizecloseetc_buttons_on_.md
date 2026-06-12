---
title: "after upgrading system, resize/close/etc buttons on left hand side"
date: 2010-11-01
forum: General Help
---

### Post by osmorphyus on 2010-11-01
this is really lame, i upgraded my ubu system and now my close/resize/minimize window control buttons are on the left side of my windows.


how can i put them back on the right side?  ewww...  who thought that was a good idea?

---

### Post by HiImTye on 2010-11-01
thats actually the intended behavior

right click your desktop and choose a different theme
you can also try a different window decorator like Emerald if you want

---

### Post by junapp on 2010-11-01
> **osmorphyus said:**
> 
how can i put them back on the right side?  ewww...  who thought that was a good idea?
You might get used to it, I did.
[http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)

change em back:
[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

---

### Post by mywai on 2010-11-01
Install Ubuntu Tweak and launch it from Applications/System Tools

Under Desktop, click Window Manager Setting, first item on the list is the choice of placement of all this icons, left or right.

or Alt+F2 to open the Run Application; 
type "gconf-editor" without the ";
on the side pane, open /apps/metacity/general and double click the button_layout item;
change the value to :minimize,maximize,close;
click OK

---

### Post by osmorphyus on 2010-11-02
i just changed the theme.  its theme dependant.

the upgraded theme changing the buttons is horrible.  truly disgusting.  it is the thing that should not be in the world of operating systems trying to make a big change.


they should let you know its gonna hijack your theme that way.  the colorcheme was nice too, but yeah - epic fail to whoever designed that.

---

### Post by _khAttAm_ on 2010-11-02
> **osmorphyus said:**
> i just changed the theme.  its theme dependant.

the upgraded theme changing the buttons is horrible.  truly disgusting.  it is the thing that should not be in the world of operating systems trying to make a big change.


they should let you know its gonna hijack your theme that way.  the colorcheme was nice too, but yeah - epic fail to whoever designed that.

Here is a tip to move them to right in any theme:
Alt+F2 and type in the following:
```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```
Press enter and you are done.

---

### Post by osmorphyus on 2010-11-02
sweet tip!

i wish i had the ability to "like" your post!  thanks!

---

