---
title: "Docky wrecked my system"
date: 2012-03-05
forum: General Help
---

### Post by kkelly77 on 2012-03-05
I installed Docky yesterday to try it out. Unfortunately it's left me with some big problems.

I uninstalled it as half of my screen was going black with Docky installed. However, since uninstalling it, 

[LIST]
[*]I've lost the ability to manually resize windows
[*]My min, max and close buttons have disappeared.
[*]When I open Firefox, nothing I type is coming up in the address bar, Google search box etc.
[/LIST]
Can anyone help as to how to fix or if there are some settings I need to change? :( Thanks.

K.

---

### Post by MG&amp;TL on 2012-03-05
This sounds suspiciously like something's going wrong with your window manager.

Install *compizconfig-settings-manager* from the software center, and see if the "Ubuntu Unity Plugin" and "Window Decoration" plugins are ticked. If not, tick them.

Althoug why docky messed about with it in the first place...

---

### Post by kkelly77 on 2012-03-05
> **MG&TL said:**
> This sounds suspiciously like something's going wrong with your window manager.

Install *compizconfig-settings-manager* from the software center, and see if the "Ubuntu Unity Plugin" and "Window Decoration" plugins are ticked. If not, tick them.

Althoug why docky messed about with it in the first place...

Have compiz installed already. I couldn't find the Unity Plugin. Wasn't in the plugin list. Window Decoration is already ticked.

I forgot to mention that I enabled the shortcut button on Firefox. It's the one that turns the menu bar off i.e. File, Edit, View etc. When I try to right click on the menu bar to reenable it, Firefox crashes.

Is there a feature in Ubuntu that I can load a previous configuration from a few days ago?

---

### Post by MG&amp;TL on 2012-03-05
No, not really.

What version of ubuntu are you running?

---

### Post by kkelly77 on 2012-03-05
> **mg&tl said:**
> no, not really.

What version of ubuntu are you running?

10.04

---

### Post by HiImTye on 2012-03-05
if docky made half your screen black that means it was using fallback mode (no compositing). this means that Compiz stopped working and you used Metacity (or Mutter) instead. issuing:
```
compiz --replace &
```in a terminal should fix your problems
alternately, you can:
```
unity --replace &
```
if you are using Unity

---

### Post by kkelly77 on 2012-03-05
> **HiImTye said:**
> if docky made half your screen black that means it was using fallback mode (no compositing). this means that Compiz stopped working and you used Metacity (or Mutter) instead. issuing:
```
compiz --replace &
```in a terminal should fix your problems


FIXED!!! Thanks HiImTye
But I did get the error
```
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start

```

Do you know what that error means or why Compiz decided to stop working?

---

### Post by HiImTye on 2012-03-05
it means that you dont have a decorator, if you don't use [Emerald]("apt://emerald") then use [CompizConfigSettingsManager]("apt://compizconfig-settings-manager") and then turn on 'Decorate Windows'

if you use emerald then just issue an:
```
emerald --replace &
```as to why Compiz decided to stop working, it can be anyones' guess, I remember in 10.04 Compiz was kind of finicky (it still is sometimes)

---

### Post by kkelly77 on 2012-03-05
> **HiImTye said:**
> it means that you dont have a decorator, if you don't use [Emerald]("apt://emerald") then use [CompizConfigSettingsManager]("apt://compizconfig-settings-manager") and then turn on 'Decorate Windows'

if you use emerald then just issue an:
```
emerald --replace &
```as to why Compiz decided to stop working, it can be anyones' guess, I remember in 10.04 Compiz was kind of finicky (it still is sometimes)

I have CompizConfigSettingsManager installed and the Window Decorater box was always ticked. :confused:

I'll be upgrading to v12.04 as soon as it's released.

Thanks again for your help. :)

---

### Post by HiImTye on 2012-03-05
no problem :D

---

### Post by kkelly77 on 2012-03-06
Thought this problem was solved :(

Turned on the laptop this evening and again my min, max and close icons were missing from any window I opened.

Using the code to replace compiz fixed it but I'm sure it will happen again when I reboot.

Any ideas as to why this is happening or how to fix permanently?

---

### Post by kkelly77 on 2012-03-07
I've added a screen shot from Ubuntu Tweek.

Should I have both Compiz Settings (menu on the left) as well as Windows Manager Settings (metacity)? Could this be causing a conflict, which in turn is causing my issue?

---

