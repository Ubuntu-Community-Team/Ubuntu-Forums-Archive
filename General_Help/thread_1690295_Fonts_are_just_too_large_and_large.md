---
title: "Fonts are just too large and large"
date: 2011-02-18
forum: General Help
---

### Post by me4oslav on 2011-02-18
Two days ago some fonts on my system become too widespaced, like this:
[[IMG]http://img715.imageshack.us/img715/5372/73540464.th.png[/IMG]](http://imageshack.us/photo/my-images/715/73540464.png/)
See how big and widespaced the fonts on Clementine playlist are and how good they look on the appmenu (where my mouse pointer is). This is not because Clementine is QT4, I've got the same problem with Chrome, Opera etc...
I've been messing with system-settings (KDE settings tool) a day before the fonts become that widespaced in order to make my KDE apps look more native on my GNOME, but I haven't touched the fonts settings there.
Any ideas, solutions?

---

### Post by ivanovnegro on 2011-02-19
Maybe there is an inconsistency with your theme as I see you are not using the default one and with some of the themes you can go into problems if they are somehow buggy.
Maybe you could ask or look what the theme creator says about bugs with that what you are using especially Clementine has some problems with some themes because of Qt4.
Another thing, the large and wide font described from the screenshot with Clementine is by design, that indicates the current playing track but you can disable it from the settings (behavior).

---

### Post by Krytarik on 2011-02-19
I suppose you did already check the font settings in "System -> Preferences -> Appearance -> Fonts"?! I guess the "Document font" is the one of concern.

---

### Post by me4oslav on 2011-02-20
@ivanovnegro, it has nothing to do with the fact that Clementine is QT4, because as I have said above I experience the same problems on Chrome, Opera etc.. (Nautilus, Firefox ...)
And it isn't because of the GTK theme, because I have been using atolm since a lot of time and the font screwed out of the blue, plus I have tried quite a lot GTK themes and I still have the same problem (including Ambiance and Radiance).
@Krytarik Yes, I did. The default was Sans 10 and now I have tried changing it to Ubuntu, DejaVu, DroidSans etc.. but no luck - it changes to the one I choose, but it is still way too wide.

---

### Post by cottfcfan on 2011-02-20
The fonts in your image look fine to me.
Not sure about your taste in Music though!::lolflag:

---

### Post by Krytarik on 2011-02-20
Ok, then I also have to say, that the font you have in the screenshot (Ubuntu) looks like it should, it looks the same at my system. I wasn't sure if you just don't like the font.

---

### Post by me4oslav on 2011-02-20
Ok, this is getting plain weird - I have two more machines in which I also use Ubntu font at looks way different and not so wide.
Plus I have a second user account on this laptop and the same Ubuntu fonts doesn't look that wide on Clementine, Gedit, Firefox etc..
*getting confsed*
P.S. What is wrong with my music taste :P Ubuntu + Metal is great :) :guitar:

---

### Post by Krytarik on 2011-02-20
> **me4oslav said:**
> Ok, this is getting plain weird - I have two more machines in which I also use Ubntu font at looks way different and not so wide.
Plus I have a second user account on thsi laptop and the same Ubuntu fonts doesn't look that wide on Clementine, Gedit, Firefox etc..
*getting confsed*

Could you then also provide a screenshot from within your other user account, to compare?

Did you already check the DPI setting?
In "Appearance -> Fonts" click at "Details" at the bottom. Default is 96dpi.

---

### Post by me4oslav on 2011-02-20
Yes, it is 96 dpi.
Here are the screenshots:
Normal fonts:
[[IMG]http://img829.imageshack.us/img829/2330/201102201504551366x768s.th.png[/IMG]](http://img829.imageshack.us/i/201102201504551366x768s.png/)
Wide fonts:
[[IMG]http://img248.imageshack.us/img248/3710/201102201511441366x768s.th.png[/IMG]](http://img248.imageshack.us/i/201102201511441366x768s.png/)
Both users use one and the same fonts settings.
See has much less wide and better the fonts on KDE user look.
P.S. I've given one and the same applications for example - Skype and Clementine.

---

### Post by Krytarik on 2011-02-20
I did see your screenshots right after your post, and the font sizes are indeed much different, but I do not even now have an idea what may be causing this.

I just made a short web search and no obvious solution came up. But try changing the DPI up and down again, or the other way.

---

### Post by me4oslav on 2011-02-21
Tried this, but didn't helped.
Noticed that under the Gnome user KDE control center (system settings) is set to 'Use my KDE fonts for my gnome apps)
And there is no DPI enabled, should I mess with that too?
I only ask, because I don't wanna make things worse.

---

### Post by Krytarik on 2011-02-21
> **me4oslav said:**
> Tried this, but didn't helped.
Noticed that under the Gnome user KDE control center (system settings) is set to 'Use my KDE fonts for my gnome apps)
And there is no DPI enabled, should I mess with that too?
I only ask, because I don't wanna make things worse.
Sure, fiddle around with those settings, there is always a way to unset the settings you change.

---

### Post by me4oslav on 2011-02-22
Ok, checked all possible permutations and no luck ;(
Is there a way to return the fonts to their default settings?

---

### Post by Krytarik on 2011-02-22
Those are the usual settings you find in the "Appearance -> Fonts" dialog, specified in Gconf, accessible via "gconf-editor":

/desktop/gnome/interface/document_font_name
/desktop/gnome/interface/font_name
/desktop/gnome/interface/monospace_font_name
/apps/nautilus/preferences/desktop_font
/apps/metacity/general/titlebar_font
/desktop/gnome/font_rendering/antialiasing
/desktop/gnome/font_rendering/dpi
/desktop/gnome/font_rendering/hinting
/desktop/gnome/font_rendering/rgba_order

To "unset" them all at once enter the following command, though I doubt it would change anything, just copy&paste it into the terminal:
```
gconftool-2 --unset /desktop/gnome/interface/document_font_name /desktop/gnome/interface/font_name /desktop/gnome/interface/monospace_font_name /apps/nautilus/preferences/desktop_font /apps/metacity/general/titlebar_font /desktop/gnome/font_rendering/antialiasing /desktop/gnome/font_rendering/dpi /desktop/gnome/font_rendering/hinting
```The settings you mentioned just before apparently affects the fonts of Gnome apps when run within KDE, I didn't check that before. So that doesn't have any effect on you.
Unfortunately I didn't find a way to "hard-reset" those settings, and since I don't have KDE installed, I cannot even test it. Just set the settings the way they where before. 

But upon searching for it I found some other options to try/check:

You may try to run the following command, but since it is not user-specific it may not help:
```
sudo dpkg-reconfigure fontconfig
```Also, do you have one of those files in your home directory?:
- ".font"
- ".font.conf" 
- ".gtkrc-2.0"

---

### Post by me4oslav on 2011-02-23
The first two commands did nothing, but then I got really angry and decided to find and delete the files:
- "~/.font"
- "~/.font.conf" 
- "~/.gtkrc-2.0"
I had no file "~/.font", I had no file "~/.gtkrc-2.0", but I had "~/.gtkrc-2.0-kde4", deleted it, rebooted, but no luck.
That I deleted "~/.font.conf" rebooted and then 'Hell Yeah!' everything was looking how it should be, with normal non-wide fonts here and there.
I guess I should tag this [SOLVED].
TYVM for the help.
Here is a screenshot:
[[IMG]http://img268.imageshack.us/img268/6679/201102231340111366x768s.th.png[/IMG]](http://img268.imageshack.us/i/201102231340111366x768s.png/)
Edit it is now marked as [SOLVED]

---

### Post by Krytarik on 2011-02-23
Great that it worked! Although there really isn't that much of a difference, but compared side-by-side there is a remarkable one. I wonder by how many people this would go unnoticed, or is?! Man, you are like me!:) But AC/DC?;) I'm (currently) more of a fan of the "Rhythmic Noise" genre.

---

### Post by me4oslav on 2011-02-23
//enormous offtopic:
That was just for a warm up, now I am one Anthrax - Fistful Of Metal, Spreading The Disease, Among The Living, State of Euphoria and Presence Of Time.
Mr. Joey Belladona is the man, although Neil Turbin is great also ;)

---

