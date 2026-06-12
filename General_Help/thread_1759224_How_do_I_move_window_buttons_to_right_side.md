---
title: "How do I move window buttons to right side?"
date: 2011-05-15
forum: General Help
---

### Post by belltown on 2011-05-15
I'm running Ubuntu 11.04 (Nasty Narwhale), using the Classic (No effects) desktop. The window buttons (close, minimize, maximize) are on the upper left-hand side of my windows. I'm used to having them on the upper right-hand corner. Any idea how I move them to the right side?

---

### Post by ChaosChris2009 on 2011-05-15
[CENTER]Get Ubuntu Tweak, head to the Windows Settings Manager, from there you'll be able rearrange the buttons anyway you want.

Here's a screenshot

[IMG]http://i.imgur.com/5Ws8O.jpg[/IMG]

You can get Ubuntu Tweak from here

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")[/CENTER]

---

### Post by Frogs Hair on 2011-05-15
I use Ubuntu Tweak , which has many useful settings . If you install from the instructions at the link just navigate to the window manager settings. 
[http://www.multimediaboom.com/how-to-install-ubuntu-tweak-in-ubuntu-11-04-natty-narwhal/](http://www.multimediaboom.com/how-to-install-ubuntu-tweak-in-ubuntu-11-04-natty-narwhal/)

---

### Post by belltown on 2011-05-15
Ubuntu Tweak worked! Thanks for your help.

---

### Post by belltown on 2011-05-22
Here's how to do it without using UbuntuTweak:

Alt-F2 (run a teminal window)>gconf-editor>apps>metacity>general>change button_layout to menu:maximize,minimize,close

---

### Post by AlmoG on 2011-06-01
> **belltown said:**
> Here's how to do it without using UbuntuTweak:

Alt-F2 (run a teminal window)>gconf-editor>apps>metacity>general>change button_layout to menu:maximize,minimize,close

thanks! that works and does'nt require installation :)

---

### Post by sdpkelkar on 2011-06-09
This method has one problem - for some reason I've seen that whenever I install any updates, the settings  once again revert to the default.

---

### Post by hexpek on 2011-06-25
Thank you very much for this. I've been scratching my head over this one for ages since I upgraded to Natty.

hexpek

---

