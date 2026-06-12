---
title: "Need help!! Awn not working properly"
date: 2010-11-21
forum: General Help
---

### Post by pedal2themedal on 2010-11-21
I am trying to set up my awn similar to this, 

[http://www.omgubuntu.co.uk/2010/09/how-to-fully-replace-your-gnome-panels-with-awn/](http://www.omgubuntu.co.uk/2010/09/how-to-fully-replace-your-gnome-panels-with-awn/)

My problem lies in two areas though.

1. I dont have the option for the digital clock in my applets like I should. Is there a repository somewhere or someone I can get it from?

2. Whenever I try a theme that is set up like that, the whole dockbar shows up but doesn't look right(See enclosed screen shot).

I have tried completely uninstalling it and installing the newest version, but it still does the same thing.

Any help would be much appreciated!!

---

### Post by Pollox on 2010-11-22
For the clock, I think you want awn-applets-python-extras. I would just install all the awn-applets stuff. I am not sure what your screen shot is trying to demonstrate.

---

### Post by stinkeye on 2010-11-22
Is Metacity your window manager?
If so enable compositing.
**gconf-editor** /apps/metacity/general/compositing_manager

Did you enable the awn-testing repository as described in the article you referenced?

---

### Post by pedal2themedal on 2010-11-22
> **stinkeye said:**
> Is Metacity your window manager?
If so enable compositing.
**gconf-editor** /apps/metacity/general/compositing_manager

Did you enable the awn-testing repository as described in the article you referenced?

Enabling composting fixed the problem. It also made the other applets show up (Weird huh).

But at least it is working now. 

Thanks for the help, robert

---

