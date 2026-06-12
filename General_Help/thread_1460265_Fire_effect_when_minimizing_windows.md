---
title: "Fire effect when minimizing windows??"
date: 2010-04-22
forum: General Help
---

### Post by oleink on 2010-04-22
I've seen people use the fire effect when minimizing windows and even saw someone setting up the fire effect to fit their needs in compiz but I do not have the fire effect in my compiz effects manager.  Where can i get it??

---

### Post by chriskin on 2010-04-22
the one you mean is probably the "burn" effect of the "animations add-on" plugin 
do you have "animations add-on" on compiz? if not, try installing some plugins from synaptic (probably compiz-fusion-plugins-extra ?)
----------
by the way i'm pretty sure we are already using open office, no need to advertise it here :)

---

### Post by schwabdale on 2010-04-22
First install CCSM through package manager. This is also called Compiz Settings manager. 
Install Compiz Fusion Plugins...it may be called extra. Then open System/Pref/Compiz settings manager. 
Look for animations extra

---

### Post by Sef on 2010-04-22
> the one you mean is probably the "burn" effect of the "animations  add-on" plugin 
do you have "animations add-on" on compiz? if not, try installing some  plugins from synaptic (probably compiz-fusion-plugins-extra ?)

That will install the burn option.

---

### Post by tgalati4 on 2010-04-22
In a terminal:

apt-cache search compiz

That will give you list of compiz-related stuff.

---

### Post by oleink on 2010-04-22
> **schwabdale said:**
> First install CCSM through package manager. This is also called Compiz Settings manager. 
Install Compiz Fusion Plugins...it may be called extra. Then open System/Pref/Compiz settings manager. 
Look for animations extra

I've got that stuff.  The fire effect isn't there.

PS it is called "fire" take a look:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64719&d=1207163498[/IMG]

---

### Post by chriskin on 2010-04-22
mine is named burn (!)
[IMG]http://dl.dropbox.com/u/452182/burn.png[/IMG]

have you installed the extra plugins from synaptic?

---

### Post by oleink on 2010-04-22
There were no "extras" all the compiz-plugins are installed...

---

### Post by chriskin on 2010-04-22
> **oleink said:**
> There were no "extras" all the compiz-plugins are installed...

you might need compiz's repository
i have it through ubuntu tweak


i don't know if it's stable or testing though

you can also install the plugin itself , there are instructions over at compiz's forums

---

### Post by schwabdale on 2010-04-23
You may be able to do an update to get it. 
Try apt-get update in a terminal... 
Try System/administration/update manager....

Then check for the "extra" plugin

---

### Post by ssj6akshat on 2010-04-23
> **chriskin said:**
> mine is named burn (!)
[IMG]http://dl.dropbox.com/u/452182/burn.png[/IMG]

have you installed the extra plugins from synaptic?

what font is that?Can you give it to me?

---

### Post by warfacegod on 2010-04-23
You should already have it. Select the tab that wish the effect to function for.

Example: Close Animation tab. Then highlight the effect that is enabled and select edit. In the new window that opens, there should be a drag down menu with all of the effects listed. Select Burn or Fire.

Interestingly oleink and chriskin, you both seem to have the ability to modify the "Burn" settings, whereas I do not. I find that to be rather irksome. Any idea how you guys got it? I would have thought it would install automatically with Compiz.

---

### Post by chriskin on 2010-04-23
> **ssj6akshat said:**
> what font is that?Can you give it to me?

wow, seems that this font gained a fan club, another user sent me a message
it's the rufscript font , made by  Hiran Venugopalan from actual handwriting. as he said "It is created using only free software tools (Fontforge, Inkscape, gedit and GIMP)."


well, to the download place :
[http://hiran.in/blog/rufscript-font](http://hiran.in/blog/rufscript-font)

> **warfacegod said:**
> 
Interestingly oleink and chriskin, you both seem to have the ability to modify the "Burn" settings, whereas I do not.


can you sent me a screenshot on what appears at your settings? i can't see why you wouldn't be able to modify the settings (default ones are...well, defaults :) noone keeps them :))

---

### Post by warfacegod on 2010-04-23
See? No Burn. Irksome.

---

### Post by chriskin on 2010-04-23
> **warfacegod said:**
> See? No Burn. Irksome.

you are on the animations menu
i was on the animations add-on menu

if you don't have one, you can install it through the extras from synaptic (full name on a previous post)
if burn effect isn't in there, you can always install it by itself using instructions from the compiz forums

---

### Post by warfacegod on 2010-04-23
Yep. You're right. Feel like a newb all over again. Doh!:P

---

### Post by schwabdale on 2010-04-23
What does the +Font Exception in  "The font is licensed under [GNU GPL version 3]("http://www.fsf.org/licensing/licenses/gpl.html")  +[  Font Exception]("http://www.fsf.org/licensing/licenses/gpl-faq.html#FontException")." 
mean? Does that mean I can't sell a system with this font on it?

---

### Post by chriskin on 2010-04-23
> **schwabdale said:**
> What does the +Font Exception in  "The font is licensed under [GNU GPL version 3]("http://www.fsf.org/licensing/licenses/gpl.html")  +[  Font Exception]("http://www.fsf.org/licensing/licenses/gpl-faq.html#FontException")." 
mean? Does that mean I can't sell a system with this font on it?

i am a happy font user, not a lawyer
wouldn't it be useful to you to read the font exception link?

---

### Post by oleink on 2010-04-24
> **warfacegod said:**
> You should already have it. Select the tab that wish the effect to function for.

Example: Close Animation tab. Then highlight the effect that is enabled and select edit. In the new window that opens, there should be a drag down menu with all of the effects listed. Select Burn or Fire.

Interestingly oleink and chriskin, you both seem to have the ability to modify the "Burn" settings, whereas I do not. I find that to be rather irksome. Any idea how you guys got it? I would have thought it would install automatically with Compiz.

Its not in there

PS:  I am up to date i update my computer pretty much daily

---

### Post by warfacegod on 2010-04-24
Okay. I'm totally baffled. You have Fire effect settings in Animations. Mine (Burn) is in Animations Add-ons. I'd venture a guess and say chriskin's is like mine as in not in Animations but Anima. Add-ons.

Have you been messing with installing and uninstalling plugins? That's the only thing I can think of. That you've removed your Burn effect.

---

### Post by oleink on 2010-04-26
Nevermind I FOUND IT YAY!! Thanks guys haha

---

### Post by warfacegod on 2010-04-26
Cool. Where was it?

---

