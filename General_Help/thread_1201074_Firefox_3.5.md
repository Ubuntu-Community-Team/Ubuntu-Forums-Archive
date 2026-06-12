---
title: "Firefox 3.5"
date: 2009-06-30
forum: General Help
---

### Post by malel on 2009-06-30
I have just loaded in Firefox 3.5 but the font (Verdana) is terrible. It shows up very 'thin' not like Verdana in the older version of Firefox. Can anyone offer a solution to this because I cannot use this newer version as it is ..









System: Sempron AMD 1.8Ghz 1Gb Ram 80Gb HDD

---

### Post by Meow27 on 2009-06-30
how did you install it?

---

### Post by earthpigg on 2009-06-30
edit -> preferences -> content -> pick a font you like??

---

### Post by malel on 2009-06-30
Installed using apt-get after installing the appropriate 'source'

edit> preferences.> content > font    does not fix it.

It still looks very 'thin' and hurts the eyes. As it is it certainly is not a good upgrade compared to Firefox 3.0.11

---

### Post by VastOne on 2009-06-30
> **Meow27 said:**
> how did you install it?

I have just done both an apt-get install and and a Synaptic and cannot get 3.5 to run from anywhere including terminal


Found it as Shiretoko

Needed to read everything....

---

### Post by zeroseven0183 on 2009-06-30
I don't like the new icon. I can't seem to find the "fiery fox". It's all blue

---

### Post by VastOne on 2009-06-30
I am not seeing any changes on mine....Same font and look, only a couple of add-ons that are not compatible..

But I had already been into edit> preferences.> content > font  and made my preferred fonts eons ago

---

### Post by eznet on 2009-06-30
People running "Shiretoko" and seeing the Blue Globe Icon instead of the traditional Firefox logo - I think you are running 3.5 RC4 (Release Candidate).  That has been available - what you are most likely "wanting" (what reddit, digg, HN, etc,. have all been talking about today) is the Final Release of 3.5.

Read here for the specifics:
[http://ubuntuforums.org/showthread.php?t=1200717](http://ubuntuforums.org/showthread.php?t=1200717)

Sorry if I am off point... I initially made this mistake.

---

### Post by Fabio K on 2009-06-30
Here:
[http://br.mozdev.org/firefox/download.html](http://br.mozdev.org/firefox/download.html)

Read the right side of the page, it has instructions to install on ubuntu.

I used the step by step to add AND remove firefox 3.5. Worked perfectly; but I'll wait until it hits the ubuntu repos.

Fabio K

EDIT: If you don't have the /opt directory yet, you'll have to create it, or it wont work.
EDIT2: English link in the next post (step by step link)

---

### Post by VastOne on 2009-06-30
> **Fabio K said:**
> Here:
[http://br.mozdev.org/firefox/download.html](http://br.mozdev.org/firefox/download.html)

Read the right side of the page, it has instructions to install on ubuntu.

I used the step by step to add AND remove firefox 3.5. Worked perfectly; but I'll wait until it hits the ubuntu repos.

Fabio K

EDIT: If you don't have the /opt directory yet, you'll have to create it, or it wont work.

Any one know the English link to this suggestion?

---

### Post by Fabio K on 2009-06-30
sorry, i gave out the brazillian link

here is the step by step (english):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by steveneddy on 2009-06-30
New Icon

What about sub pixel smoothing? Will that fix the font issue?

---

### Post by ~sHyLoCk~ on 2009-06-30
> **steveneddy said:**
> New Icon

What about sub pixel smoothing? Will that fix the font issue?

Looks cool :D Btw, the font issue can also be solved someimes by changing the fonts in appearance. Not sure if this will work for firefox though.

---

### Post by djuliette on 2009-06-30
Edit - Prefs - content - fonts  doesn't do anything for me.  I change the selection and restart and nothing changes.

Also it shows up as shiretoko so I'm not sure I have it installed properly.

The 'about' window shows this:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.1pre) Gecko/20090701 Ubuntu/9.04 (jaunty) Shiretoko/3.5.1pre

So I'm guessing shiretoko is the daily dev build, does that sound right?

---

### Post by Fabio K on 2009-06-30
> **djuliette said:**
> Edit - Prefs - content - fonts  doesn't do anything for me.  I change the selection and restart and nothing changes.

Also it shows up as shiretoko so I'm not sure I have it installed properly.

The 'about' window shows this:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.1pre) Gecko/20090701 Ubuntu/9.04 (jaunty) Shiretoko/3.5.1pre

So I'm guessing shiretoko is the daily dev build, does that sound right?

it says 3.5.1pre in the version, it's not the final release.
Read my previous post to install the 3.5 final.

Fabio K

EDIT: you're using a 64 bit version of ubuntu right? then I don't know if the instructions will apply to you.... (using 32 bit here)

---

### Post by ertayone on 2009-07-01
I'm using 64 bit Ubuntu and Firefox 3.5, installed using [this guide](http://coffeecokeandcode.blogspot.com/2009/06/firefox-35-on-ubuntu-904.html). The font rendering is really awful, which appears to be because Firefox 3.5 lacks the Ubuntu Firefox Modification addon at this point and thus does not synchronize with GNOME's font settings. The advice in [this thread](http://ubuntuforums.org/showthread.php?p=7094387) helped others, but did nothing for me -- perhaps because it came before the final release, or perhaps it refers to a 32 bit version of Ubuntu.

Does anyone know when the Ubuntu Firefox Modification addon for 3.5 is coming out?

---

### Post by michaelzap on 2009-07-01
> **ertayone said:**
> I'm using 64 bit Ubuntu and Firefox 3.5, installed using [this guide](http://coffeecokeandcode.blogspot.com/2009/06/firefox-35-on-ubuntu-904.html). The font rendering is really awful, which appears to be because Firefox 3.5 lacks the Ubuntu Firefox Modification addon at this point and thus does not synchronize with GNOME's font settings. The advice in [this thread](http://ubuntuforums.org/showthread.php?p=7094387) helped others, but did nothing for me -- perhaps because it came before the final release, or perhaps it refers to a 32 bit version of Ubuntu.

Does anyone know when the Ubuntu Firefox Modification addon for 3.5 is coming out?

Same thing here, although I installed 3.5 using the Mozilla daily build PPA and just changed the firefox symbolic link. I expect that the 64-bit packages are just lagging behind a bit. 3.5 is using less than half of the RAM that 3.0 was using on my machine, and that's more important than hinted fonts to me.

---

### Post by unimatrix on 2009-07-01
Is there a 3.5 final release 64bit deb for Jaunty? The beta4 in repository doesn't really work too well.

---

### Post by merlin666 on 2009-07-10
I also got the shiretoko 3.5.1pre in 64-bit. The fonts and display look ok. I installed using:

apt-get install firefox-3.5 firefox-3.5-gnome-support latex-xft-fonts

---

### Post by hwttdz on 2009-07-20
It's possible that this will solve the font problems that some here seem to be reporting:

[http://ubuntuforums.org/showthread.php?p=7094387](http://ubuntuforums.org/showthread.php?p=7094387)

Second until firefox 3.5 becomes default for ubuntu it will be labeled shiretoko (which I'm not terribly fond of).  This has something to do with ubuntu not wanting to confuse people with two types of firefox floating about.

---

