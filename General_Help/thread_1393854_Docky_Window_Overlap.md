---
title: "Docky Window Overlap?"
date: 2010-01-29
forum: General Help
---

### Post by Cam! on 2010-01-29
I love Docky. I don't like how there's always space reserved for the dock, so it sacrifices the size of the window. How can I make the dock overlap the window, without using the Intellihide feature (Which does nothing, BTW.)

---

### Post by tom.swartz07 on 2010-01-29
> **Cam! said:**
> I love Docky. I don't like how there's always space reserved for the dock, so it sacrifices the size of the window. How can I make the dock overlap the window, without using the Intellihide feature (Which does nothing, BTW.)

Intellihide should make it disappear when you have a window over it. Do you have compositing enabled?

Right click on your desktop and click 'change background' go to the visual effects tab and make sure something besides 'none' is enabled. that should allow you to use all of the cool features of Docky

---

### Post by Cam! on 2010-01-29
I want to be able to see the dock, and have the dock itself overlap the window; not the other way around. The point of Docky is to do the whole Mac OS X thing, but it's not doing it at all.

---

### Post by tom.swartz07 on 2010-01-29
> **Cam! said:**
> I want to be able to see the dock, and have the dock itself overlap the window; not the other way around. The point of Docky is to do the whole Mac OS X thing, but it's not doing it at all.

Docky itself might have crashed. Sometimes after you update it, it gets a little unstable. Try killing it
```
sudo killall docky
``` then relaunch it from the applications menu.


Im kind of confused by what you mean- do you want the dock to auto-hide? In that case, thats what you need compositing for. If not, you could just change it to panel mode and have it stay up all of the time.

---

### Post by Cam! on 2010-01-29
[http://img716.imageshack.us/img716/7960/screenshotj.png](http://img716.imageshack.us/img716/7960/screenshotj.png)

That's what it looks like. I would like to have the FireFox window stretch down to the bottom of the screen, yet I can still see the dock.

---

### Post by Cam! on 2010-01-29
Bump?

---

### Post by tom.swartz07 on 2010-01-29
> **Cam! said:**
> [http://img716.imageshack.us/img716/7960/screenshotj.png](http://img716.imageshack.us/img716/7960/screenshotj.png)

That's what it looks like. I would like to have the FireFox window stretch down to the bottom of the screen, yet I can still see the dock.

I never quite got an answer as to the status of your compositing. Try enabling visual effects and see if it fixes it.

---

### Post by Cam! on 2010-01-29
Yes. I have the visual effects set at max. I have no graphics card drivers as well. This is a common thing (where the window doesn't extend all the way down) in other Dock apps. It's called "Reserve Space for Dock", but I don't see it in the settings menu.

---

### Post by tom.swartz07 on 2010-01-29
> **Cam! said:**
> Yes. I have the visual effects set at max. I have no graphics card drivers as well. This is a common thing (where the window doesn't extend all the way down) in other Dock apps. It's called "Reserve Space for Dock", but I don't see it in the settings menu.

I just fiddled with my settings on my Docky. It seems that your settings are 'stuck' on not hiding at all.

See if you could change the setting in .gconf-editor
hit <alt> F2 and type gconf-editor (it should autocomplete)

navigate to apps-docky2-docky-interface-dock preferences-dock1

the first one in the list on the right is autohide- edit the key to 
Intellihide (capital I)

See if that fixes it.

---

### Post by Cam! on 2010-01-29
You clearly didn't read a word I typed. Intellihide does nothing. I want to be able to SEE THE DOCK. Whenever I put on Intellihide, or the others, the dock CANNOT BE SEEN UNLESS I HOVER OVER THE BOTTOM WITH MY MOUSE.

---

### Post by tom.swartz07 on 2010-01-29
> **Cam! said:**
> You clearly didn't read a word I typed. Intellihide does nothing. I want to be able to SEE THE DOCK. Whenever I put on Intellihide, or the others, the dock CANNOT BE SEEN UNLESS I HOVER OVER THE BOTTOM WITH MY MOUSE.

Im sorry- I didnt quite understand what youre asking for. Ive only ever used a OSX for about 10 minutes.

As far as I know, Docky doesnt have functionality to sit ontop of windows. (wouldnt it also get in the way of things youre doing?)

The only settings that you could have for your dock are on top; and hiding when not in use, or always up; with windows out of the way


Sorry to disappoint! :(

---

### Post by Cam! on 2010-01-30
> **tom.swartz07 said:**
> Im sorry- I didnt quite understand what youre asking for. Ive only ever used a OSX for about 10 minutes.

As far as I know, Docky doesnt have functionality to sit ontop of windows. (wouldnt it also get in the way of things youre doing?)

The only settings that you could have for your dock are on top; and hiding when not in use, or always up; with windows out of the way


Sorry to disappoint! :(

That's incredibly lame. I'm out of options, then. AWN is too basic for my needs, and Cairo Dock won't work with my 64-bit setup.

---

### Post by CausingTraumaZ on 2010-01-30
Im also having a problem with Dock! When I open it it has got a [black image in the back side. ]("http://img215.imageshack.us/img215/2746/screenshotmq.png")

How can I fix this? I know that it is something with enabling compositing so How could I enable it?

---

### Post by tom.swartz07 on 2010-01-30
> **CausingTraumaZ said:**
> Im also having a problem with Dock! When I open it it has got a [black image in the back side. ]("http://img215.imageshack.us/img215/2746/screenshotmq.png")

How can I fix this? I know that it is something with enabling compositing so How could I enable it?

For the future, I would recommend starting your own thread for a problem like this- you would be quicker to get a response.


Its super easy to enable compositing- just click on your background and select 'change background image'

In the window that appears, click the tab that says 'visual effects' and select something higher than none


Thats all!

---

### Post by CausingTraumaZ on 2010-01-31
> **tom.swartz07 said:**
> For the future, I would recommend starting your own thread for a problem like this- you would be quicker to get a response.


Its super easy to enable compositing- just click on your background and select 'change background image'

In the window that appears, click the tab that says 'visual effects' and select something higher than none


Thats all!

I have tried to do that, several times but it said "Couldn't enable the effects"
Is there any other manner to solve this?

---

### Post by hawthornso23 on 2010-01-31
> **CausingTraumaZ said:**
> I have tried to do that, several times but it said "Couldn't enable the effects"
Is there any other manner to solve this?

You probably need to install a proprietary video card driver to get full 3-D fx.

---

### Post by rouge_sheep on 2011-03-03
This is a few months old now, but in case you haven't found a way you can do this with a bit of a tweak in gconf. If you set your dock to autohide then open gconf-editor and navigate to apps/docky-2/Interface/DockPreferences/Dock1 (or whichever dock you want to edit make sure FadeOnHide is ticked and set FadeOpacity to 1. This makes it use the autohide behaviour, but will never actually disappear.

---

