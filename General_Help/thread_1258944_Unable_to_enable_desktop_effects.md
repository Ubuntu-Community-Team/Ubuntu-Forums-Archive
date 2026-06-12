---
title: "Unable to enable desktop effects"
date: 2009-09-05
forum: General Help
---

### Post by rmcellig on 2009-09-05
For some reason I am unable to enable desktop effects. Any ideas what to do?

---

### Post by CrusaderAD on 2009-09-05
This is usually because you're graphics card is not capable of doing so.

---

### Post by oldos2er on 2009-09-05
> **rmcellig said:**
> For some reason I am unable to enable desktop effects. Any ideas what to do?

 Which make/model video card do you have? Have you checked System, Administration, Hardware Drivers to see if there're restricted drivers for it?

---

### Post by rmcellig on 2009-09-05
I had everything working fine before. Could it be because I installed something that might be conflicting?



Is there a way to post all of the installed software on my Ubuntu PC?

I'm just curious, is there a way to put Ubuntu back to it's vanilla state? I installed quite a bit of software today in all the excitement of using Ubuntu.

Video card info attached.

---

### Post by oldos2er on 2009-09-05
** gksu nvidia-settings** should show you your Nvidia card info. 

 To see a history of installed packages, open Synaptic, File, History.

---

### Post by rmcellig on 2009-09-05
Thanks. I posted a screen shot of my video card settings in my previous post. I think that is where I got the screen shot from. Thanks for the Synaptic info as well.

---

### Post by rmcellig on 2009-09-05
I uninstalled the nvidia driver from System/Administration Hardware Drivers, restarted the machine and reinstalled the driver again with the same result. Could there be something that I installed that is conflicting with the Nvidia driver?

Maybe I should uninstall some of the apps that I installed today?

---

### Post by Johnny B on 2009-09-05
could you post what driver version you're using please?

---

### Post by rmcellig on 2009-09-05
Nvidia 180

---

### Post by rmcellig on 2009-09-06
Is there maybe a log file in Ubuntu that I can post here that might shed some light as to why I am having problems getting Visual Effects to work in the Appearance Preferences?

---

### Post by P4man on 2009-09-06
A quick guess: you accidentally turned on metacity's compositing.  turn it off by typing this in a terminal:

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

(or run gconf-editor and browse to that key to check its state, and set it to false if it is now set to true)

If that doesn't help, run this script:

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by rmcellig on 2009-09-06
Bingo! That worked. Can you explain why metacity caused this problem? What is metacity.

A problem I am having since doing this is that I am unable to click/drag any window around. I will restart my PC and see if that fixes it. If not, what could be causing this to happen?

---

### Post by rmcellig on 2009-09-06
I am unable to drag windows around. I have to alt-drag them instead. How do I fix this. Also the windows look like they are mussing something.

---

### Post by 3rdalbum on 2009-09-06
> **rmcellig said:**
> Bingo! That worked. Can you explain why metacity caused this problem? What is metacity.

A problem I am having since doing this is that I am unable to click/drag any window around. I will restart my PC and see if that fixes it. If not, what could be causing this to happen?

If you have CompizConfig Settings Manager installed, you might have turned off the "move" plugin.

---

### Post by rmcellig on 2009-09-06
attached is a screenshot.

---

### Post by rmcellig on 2009-09-06
Move is enabled in Compiz. I uninstalled Metacity. Could that be causing this?

---

### Post by rmcellig on 2009-09-06
OK. Here is a screenshot of my Compiz installation. Am I missing something? I still can't move my windows around without always resorting to Alt-click drag. When I set the Visual Affects to Normal or Extra.

---

### Post by rmcellig on 2009-09-06
I just got back from doing my radio show and was wondering if anyone has any ideas as to how I can move windows around using the mouse to click and drag instead of using Alt-click drag. I would love to set the Appearance Preference/Visual effects to either normal or extra, but at the moment I have it set to none because this is the only way I can move my windows around properly as see the buttons that go along with them. See attached.

---

### Post by P4man on 2009-09-06
you dont have a window decorator. In compiz, enable the "windows decoration" plugin, and check if the command is set to "/usr/bin/compiz-decorator"

---

### Post by rmcellig on 2009-09-06
Thanks but how the heck would I have ever figured that out. Is there a video out there or tutorial on how to use Compiz and what exactly Compiz is?

The Command section in the settings said Emerald, instead of the path you mentioned above. All is well now. Thanks again!

---

### Post by P4man on 2009-09-07
well its the default setting for compiz; im not sure what enabled the metacity compositing, but that probably also unset the windows decoration.
Anyway, a window decorator is the program responsible for drawing windows borders (and close/minimize etc buttons). Its not that had to guess or figure out once you've worked with linux a bit and you're more familiar with metacity vs compiz.  But I agree, it would be good if compiz checked there was a window decorator.

---

### Post by rmcellig on 2009-09-07
Thanks P4Man. What is metacity? Is it similar to Compiz?

---

### Post by P4man on 2009-09-07
metacity is the default **window manager **in ubuntu (and other gnome based distributions). Its what you had before you enabled "desktop effects", which uses compiz instead of metacity. 

[http://en.wikipedia.org/wiki/Compositing_window_manager](http://en.wikipedia.org/wiki/Compositing_window_manager)

To confuse you a bit more, both compiz and metacity have their  window decorators. Compiz can use metacity's window decorator (default) or Emerald.

The important thing is that you need a window manager and you need a decorator, otherwise you get the effect you had: no window borders.

---

### Post by rmcellig on 2009-09-07
I love being confused. Thanks for the clarification. One thing that REALLY upsets me to no end about using Ubuntu is that it is keeping me up late a night when I should be sleeping. I am using Ubuntu more than my Snow Leopard Mac. I'm pretty new to Ubuntu. It looks like it has endless config possibilities which can get really confusing at times.

Is there documentation of sites that describe how to migrate from a Mac to Ubuntu? Common similarities etc... I would prefer looking at videos. I love the business case section on the Ubuntu site because it shows that Ubuntu can be used in a corporate setting.

---

### Post by P4man on 2009-09-07
much of these are dated, but perhaps worth a look anyway:
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

Im not aware of (m)any good general "visual" introductions in to ubuntu (or even textual for that matter), I prefer ways to get specific answers to specific questions, and thats more abundant, but a friend of mine, also a recent ubuntu convert asks me the same question as you, so i guess there is a "market" for it.

---

### Post by rmcellig on 2009-09-07
And that's a good thing :)

---

