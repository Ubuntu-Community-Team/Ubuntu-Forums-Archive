---
title: "How to Change Font Color? (11.10)"
date: 2011-10-15
forum: General Help
---

### Post by benerickson1 on 2011-10-15
The default font color is gray and the contrast makes it hard for me to read.   How can I keep the theme (Ambiance) but make the font dark?  I knew how  to do this prior to Ubuntu 11.10 but now I can't find it.  Thank you.

---

### Post by DMWill on 2011-10-18
I would LOVE to know who thought not being able to customize the themes was a good idea.  I too am having a hard time dealing with the font colors.  i was really surprised that it was not an option in Gnome-Tweak-Tool like I expected it to be.  Is it just me, or does this also affect the ability to read font on buttons, as the font almost blends in with the button color?

+++++++++++++++++
If you've already found a solution, then great, but I was able to fix my problem by tweaking some colors with GNOME Color Chooser.  you can find it in the Software Center.  works great, but be careful and don't change a lot of colors at once.  change one at a time to see what results you get.

---

### Post by fragos on 2011-10-18
The following 3 files all need to have their colors changed in fields with fg or text in the label. Colors are expressed as in #262626 which is the color I choose to use.

/usr/share/themes/Ambiance/gtk-2.0/gtkrc
/usr/share/themes/Ambiance/gtk-3.0/settings.ini
/usr/share/themes/Ambiance/gtk-3.0/gtk.css

---

### Post by benerickson1 on 2011-10-19
Thanks for the tip about GNOME Color Chooser.  I installed it but I had a hard time finding what I needed.  Specifically, I'm trying to change the color of the font used for the desktop and apps such as Nautilus and LibreOffice.  Do you know where in Color Chooser I might find that setting?
 
Also, yeah I have no idea why anyone would think it wise not to have the option accessible.  The 'beauty of the desktop' is one thing, but a grayed-out font when trying to type in LO Writer is pretty taxing on the eyes (mine at least).

---

### Post by vasa1 on 2011-10-19
> **benerickson1 said:**
> ... but a grayed-out font when trying to type in LO Writer is pretty taxing on the eyes (mine at least).

Speaking specifically about LibreOffice 3.4.3 in Oneiric Ocelot, once you've opened Writer, click on **Tools**, then on **Options**, then ensure that the first item, **LibreOffice**, is **expanded**. Now look for **Appearance**. On the right hand side, make sure you're at the **top**, in the section titled **General**. Click on the drop-down corresponding to **Font Color**. That should allow you to get a nice color.

In the same **General** section, you could also adjust the color of the **Document background**.

---

### Post by vasa1 on 2011-10-19
> **fragos said:**
> The following 3 files all need to have their colors changed in fields with fg or text in the label. Colors are expressed as in #262626 which is the color I choose to use.

/usr/share/themes/Ambiance/gtk-2.0/gtkrc
/usr/share/themes/Ambiance/gtk-3.0/settings.ini
/usr/share/themes/Ambiance/gtk-3.0/gtk.css

I'm fighting my own battles trying to get the hang of things :( but why do you mention **gtk-2.0/gtkrc** assuming we're talking about 11.10 and not 11.04?

---

### Post by vasa1 on 2011-10-19
> **DMWill said:**
> ...
If you've already found a solution, then great, but I was able to fix my problem by tweaking some colors with GNOME Color Chooser.  you can find it in the Software Center.  works great, but be careful and don't change a lot of colors at once.  change one at a time to see what results you get.

Just to be clear, does this GNOME Color Chooser work for 11.10?

---

### Post by fragos on 2011-10-19
> **vasa1 said:**
> I'm fighting my own battles trying to get the hang of things :( but why do you mention **gtk-2.0/gtkrc** assuming we're talking about 11.10 and not 11.04?

Because a total transition to gtk3 hasn't been made and that's what I had to change to get the job done.

---

### Post by vasa1 on 2011-10-19
> **fragos said:**
> Because a total transition to gtk3 hasn't been made and that's what I had to change to the job done.

Okay, I'll have to poke around there as well. If you have some other nuggets to share, please do :D

---

### Post by vasa1 on 2011-10-19
> **fragos said:**
> Because a total transition to gtk3 hasn't been made and that's what I had to change to get the job done.

This ^^^ saved my sanity. Really useful and I'd never have thought of looking there.

---

### Post by DMWill on 2011-10-24
sorry, i've not been paying much attention to my inbox this weekend.  but to clear it up for you vasa1, it most definitely works for 11.10, which is what i'm using too.  
@benerickson1: i don't think there is an option in GNOME Color Chooser to customize the fonts for the desktop and individual apps.

---

