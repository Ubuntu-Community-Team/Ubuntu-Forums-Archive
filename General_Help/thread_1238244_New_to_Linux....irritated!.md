---
title: "New to Linux....irritated!"
date: 2009-08-12
forum: General Help
---

### Post by LibbyLou on 2009-08-12
I installed Ubuntu a few months ago (dual boot w/ XP because I was scared, lol) and while I really love the interface, etc.......there are a few things I need help with, or I may have to scrap this whole experiment. :(

I've managed to get Firefox (well, Shiretoko 3.5) to look *okay*, but there are still things about it that are annoying.  The font is not quite right yet and images look horrible.  

Also, I am no longer able to just restart my system.  When I do try it from Ubuntu, I get a message that it's restarting, but it just hangs there on a black screen with the message at the top, until I do a hard shut down.  If I try it from XP, it hangs at a different spot, talking about a GRUB something or other.

Am I beyond help here, or can someone point me in the right direction for some guidance? :redface:

---

### Post by Arup on 2009-08-12
Let me ask, as a newbie, why did you install Shiretoko 3.5 when the default FF 3.12 works fine. First learn all the internals of the OS and then get adventurous. Somehow your GRUB has been modified either by Windows software or on your own and thats the reason the boot process is hanging.

Try booting off the LIVE CD and see if you can restore the GRUB.

---

### Post by racerraul on 2009-08-12
if you can... get on AIM, Google Chat or Yahoo chat... I'm on as racerraul.

I'll help you as much as I can.

---

### Post by LibbyLou on 2009-08-12
> **Arup said:**
> Let me ask, as a newbie, why did you install Shiretoko 3.5 when the default FF 3.12 works fine. First learn all the internals of the OS and then get adventurous. Somehow your GRUB has been modified either by Windows software or on your own and thats the reason the boot process is hanging.

Try booting off the LIVE CD and see if you can restore the GRUB.

Well, yesterday I was desperate to make FF look better, so I updated to Shiretoko 3.5 on the advice of someone at a different board.  

I need to find the CD and I'll try to boot off of it.  Thanks for your help!

---

### Post by cocopuffz on 2009-08-12
The font rendering in Shiretoko is horrible. I downgraded back to 3.0.13 myself just a few moments ago. Shiretoko is fast yes, but it's got too many lil issues such as flash being unable to go fullscreen etc...

I have a custom font.config that renders fonts nice and clean like Mac and Windows. Only firefox 3.5 and up forces their own font rendering over my config.

If you want to  try to force a custom font render try this [Custom font config to render linux fonts like Mac & Win cleartype]("http://ubuntuforums.org/showthread.php?t=1226999")

If you manage to get 3.5 font rendering nicely let us know. Like I said. I gave up and downgraded back to 3.0

---

### Post by nikhilk on 2009-08-12
> **LibbyLou said:**
> Well, yesterday I was desperate to make FF look better, so I updated to Shiretoko 3.5 on the advice of someone at a different board.

Well, you don't HAVE TO use Firefox. That is the beauty of free software, you can try some other browser and see if you like it more. You can try browsers like  Opera, Konqueror (there are many more, these are only the few ones I have presonally tried and liked)

---

### Post by LibbyLou on 2009-08-12
> **cocopuffz said:**
> The font rendering in Shiretoko is horrible. I downgraded back to 3.0.13 myself just a few moments ago. Shiretoko is fast yes, but it's got too many lil issues such as flash being unable to go fullscreen etc...


I was wondering what was up when I tried to fullscreen a movie trailer last night.  

How do I go about going back to FF now?

> **nikhilk said:**
> Well, you don't HAVE TO use Firefox. That is the beauty of free software, you can try some other browser and see if you like it more. You can try browsers like  Opera, Konqueror (there are many more, these are only the few ones I have presonally tried and liked)

I guess that's a thought.  I've just been so happy with FF up until now, that I didn't think of switching.  Thanks for the idea!

---

### Post by oldsoundguy on 2009-08-12
Or you could  go to Softpedia and install Ubuntuzilla and always have the latest updates for everything Mozilla, including Thunderbird as well as FF.  I am using 3.5.2 on 8.4 and it looks and works fine.

---

### Post by nikhilk on 2009-08-12
> **LibbyLou said:**
> How do I go about going back to FF now?
Uninstall the package firefox-3.5 from Synaptic and if not already installed, install package firefox which will give you the latest 3.0.x Firefox.

> **LibbyLou said:**
> I guess that's a thought.  I've just been so happy with FF up until now, that I didn't think of switching.  Thanks for the idea!
Yes, that was from my own experience. At one point, I was in the same state as you I never thought of using anything other than Firefox but I tried some options and have been using Opera as my primary browser since.
Not that I have totally abandoned Firefox, I use it for some sites that are better in Firefox than Opera. So it is not an mutually exclusive choice either.

---

### Post by lovejames on 2009-08-12
I also had issues with FF 3.0.12 initially. The fonts were appearing bad and the page rendering was inappropriate. But after its upgraded to 3.0.13, everything is fine. Also, for the flash to work correctly, we need to install adobe plugin. The one that comes by default is not good.

---

### Post by nanotube on 2009-08-12
> **oldsoundguy said:**
> Or you could  go to Softpedia and install Ubuntuzilla and always have the latest updates for everything Mozilla, including Thunderbird as well as FF.  I am using 3.5.2 on 8.4 and it looks and works fine.

he means, of course, go to the ubuntuzilla homepage, [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) :)

---

### Post by Mi*6d@# on 2009-08-12
OK... So.

1. Shiretoko is a Firefox beta and there should be stable 3.5 version in the repo. So go to terminal and type ```
sudo aptitude update && sudo aptitude dist-upgrade
```in order to upgrade all your packages at your system to the latest version



2. To update your GRUB configuration and ensure its corectness type
```
sudo update-grub
```This will regenerate your /boot/grub.cfg file. Hope this helps...

---

### Post by t0p on 2009-08-12
> **Arup said:**
> Let me ask, as a newbie, why did you install Shiretoko 3.5 when the default FF 3.12 works fine..

Just because firefox 3.1 "works fine", that doesn't mean we can't aspire to something that works *better*.  And a good many people agree that 3.5 works better.  It's much faster than 3.1.  Which is an excellent reason to install it.

Some people agree with the philosophy "If it ain't broke, don't fix it."  But that is an extremely un-Linux-like attitude.  Most people could probably struggle on with Windows, and so never try Linux.  But we aspire to better things.

---

### Post by eldragon on 2009-08-12
fonts looking horrible might be due to the ms ttf fonts missing on your system, search for them with synaptic

---

