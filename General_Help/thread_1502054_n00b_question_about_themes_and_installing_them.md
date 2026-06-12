---
title: "n00b question about themes and installing them"
date: 2010-06-05
forum: General Help
---

### Post by VinoFuriaRoja on 2010-06-05
Im a fairly new user and still trying to learn all about Linux and Ubuntu.  I want to mess around with the themes and truly customize my browser using some of the themes from gnome-look.org, but I am not sure what to download...meaning do I download from GTK 1.x? GTK 2.x?  Metacity? GDM Themes? And after Ive downloaded them, what is the best way to install them?  

Learning how to install them from the command line would be ideal as I want to learn that way.

Thanks in advance guys

---

### Post by elliotn on 2010-06-05
Right click on ur desktop then prefferences then the theme tab then drop the theme.tar.gz to the theme tab

---

### Post by Bachstelze on 2010-06-05
> **VinoFuriaRoja said:**
> meaning do I download from GTK 1.x? GTK 2.x?  Metacity? GDM Themes?

All those themes are used to customize different things. GTK 2 is the graphical toolkit used by most of your programs (assuming you're running a default Ubuntu installation). This means that a GTK 2 theme customizes the appearance of all graphical elements (buttons, check boxes, progress bars, etc.) in your programs (GTK 1 is the old version of GTK and is pretty much not used anymore, so you can ignore GTK 1 themes).

Metacity is your window manager, something that manages how your windows look and behave, so a Metacity theme will customize the look and feel of your windows, regardless of their contents.

GDM is your login manager, so a GDM theme will, again, customize its look and feel.

> **VinoFuriaRoja said:**
> And after Ive downloaded them, what is the best way to install them?

For GTK and Metacity themes: System > Preferences > Appearance, Install button. For GDM theme, I have no idea, because the config screen for it doesn't seem to let you install a theme anymore. Try Google.

---

### Post by jrg3 on 2010-06-05
Quickest way to begin installing themes is Ubuntu Software Center.

*Applications > Ubuntu Software Center > Themes & Tweaks*

And if you want to install a really awesome theme pack using the command line, give Bisigi a go: [http://www.bisigi-project.org/?page_id=8&lang=en]("http://www.bisigi-project.org/?page_id=8&lang=en")

As for the larger questions, (Metacity/Compiz/Etc...) this very long walkthrough will help you out: [http://ubuntuforums.org/showthread.php?t=203093]("http://ubuntuforums.org/showthread.php?t=203093")

It hasn't been updated since 2006 but skimming over it quickly it still seems to hold up quite well.

---

### Post by VinoFuriaRoja on 2010-06-05
Thanks guys. I will be checking your suggestions out and moving forward!


EDIT:  Oh by the way jrg3, you werent kidding about the Bisigi project!  WOW!

---

### Post by jrg3 on 2010-06-05
Yeah, I like Bisigi. :)

A couple other very nice theme-related suggestions are "Docky" and "DockbarX". Both can be found in the Ubuntu Software Center.

Docky is an awesome *OSX-esque* Dock, but so much better. Many options and highly integrated with many default Ubuntu applications. The only downside is it can get a bit resource-intensive. Many screenshots via google [here]("http://www.google.com/images?um=1&hl=en&tbs=isch:1&sa=1&q=docky+lucid&aq=f&aqi=&aql=&oq=&gs_rfai=").

DockbarX is a basically a gnome-panel enhancement which makes the default gnome-panel behave *Windows 7-esque*, but only better. After you install it, type this at a command prompt:

```
killall gnome-panel
```

You'll see your panels disappear, then reappear. Right click one of them, choose "add to panel", and select "DockbarX Applet". It's pretty straight forward from there, but if you have questions feel free to PM me. DockbarX is less resource-intensive than Docky. Many screenshots via Google [here]("http://www.google.com/images?um=1&hl=en&tbs=isch:1&sa=1&q=dockbarx&aq=f&aqi=&aql=&oq=&gs_rfai="). 

Both are very awesome products.

---

