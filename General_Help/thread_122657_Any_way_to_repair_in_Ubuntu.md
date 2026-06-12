---
title: "Any way to repair in Ubuntu?"
date: 2006-01-28
forum: General Help
---

### Post by Wolfbite on 2006-01-28
Windows XP always have that repair option when something goes awry, but I'm wondering if Ubuntu has any other option than to merely format and install? For example, if your graphics options are ruined, and you can't load your GUI at all (yes, this is related to my other thread), is there any way to make Ubuntu reinstall those files, y'know, without deleting mp3's and such that I have there? Some of the files I now have in Ubuntu are very precious to me, and I REALLY don't want to format anything.

---

### Post by era86 on 2006-01-28
I doubt it has a repair option, but if there is one, I'd like to know it too! Usually if the GUI is broken, it might be your xorg settings. Make sure everything is set up correctly.

-ERA

---

### Post by Wolfbite on 2006-01-28
How can I check that in terminal?

---

### Post by GeneralZod on 2006-01-28
[QUOTE=Wolfbite]Windows XP always have that repair option when something goes awry, but I'm wondering if Ubuntu has any other option than to merely format and install? For example, if your graphics options are ruined, and you can't load your GUI at all (yes, this is related to my other thread),[/QUOTE]

Firstly, you should always have your system drive on a separate partition to your /home and any other storage - this way, if things go wrong, you can easily just re-install the system part.  You should also *regularly* backup anything precious you have regardless of the OS you use - you never know when one of your harddrives is just going to give up and die!

For the GUI, give:

```

 sudo dpkg-reconfigure xserver-xorg 

```

a try.  This crops up quite frequently in the forums, so searching for dpkg-reconfigure should give you more info.

Good luck! :)

---

### Post by Wolfbite on 2006-01-28
You give some good advice, GeneralZod, and I would've followed them if I had the additional space. ^^^I'm gonna try that command of yours. In the meantime, however, I got some more info:

Everything loads fine when Ubuntu is starting up. All is "OK", but when it is done loading, and is about to go to the login screen, that's when it fails. However I got a message about what was wrong. I had to write this to paper, and then to this board, so I have focused on things that didn't work as opposed to things that did. Meaning this isn't the complete message I got:

```
Failed to start the X server (your graphical interface)

(==) Log file "/var/log/Xorg.0.log"
(== Using config file: "/etc/X11/Xorg.conf"
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
(EE) Failed to load module "bitmap" (module does not exist, 0)
(EE)Failed to load module "pcidata" (module does not exist, 0)

Fatal server error:
Unable to load required base modules, exiting
```

And here's the more detailed I got when asked if I wanted the more detailed one. The ???'s here and there is because I write too ugly even for me. ^^

```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist
Entry deleted from font path
(WW) The directory "/usr/share/X11/fonts/CID" does not exist
Entry deleted from font path
(WW) 'fonts.dir' not found (or not valid) in
"var/lib/defoma???/x-ttaidfront-conf.d???/dirs/CID'
Entry deleted from font path
(Run 'mkfontdir' on
"var/lib/defoma/x-Haidfront-conf.d???/dirs/CID'

(WW)Open APM failed (dev/apm_bios) (no such file or directory)
Couldn't open RGB_DB 'usr/X11R6/lib/X11/rgb'

(WW) Warning, couldn't open module bitmap

(EE) Failed to load module "bitmap" (module does not exist, 0)
(EE) Failed to load module "pcidata" (module does not exist, 0)
```

I only messed about in X11R6, but obviously other directories has been affected by my stupidity.

---

### Post by Wolfbite on 2006-01-28
Sadly, the reconfiguring did nothing to ail me. :(

---

### Post by GeneralZod on 2006-01-28
[QUOTE=Wolfbite]

Everything loads fine when Ubuntu is starting up. All is "OK", but when it is done loading, and is about to go to the login screen, that's when it fails. However I got a message about what was wrong. I had to write this to paper, and then to this board, so I have focused on things that didn't work as opposed to things that did. Meaning this isn't the complete message I got:

I only messed about in X11R6, but obviously other directories has been affected by my stupidity.[/QUOTE]

That's pretty impressive breakage, there! :) Try:

```

sudo apt-get --reinstall install xserver-xorg-core

```

This should address the errors you mentioned, but there may be more.  You may need your Ubuntu install CD handy.

---

### Post by Wolfbite on 2006-01-28
[QUOTE=GeneralZod]That's pretty impressive breakage, there! :) Try:

```

sudo apt-get --reinstall install xserver-xorg-core

```

This should address the errors you mentioned, but there may be more.  You may need your Ubuntu install CD handy.[/QUOTE]

Haha, that is what you get when you show a noob how to work as superuser. ^^

Thanks for the reply, I'm gonna try it now. :)

---

### Post by Wolfbite on 2006-01-28
I didn't work. It fixed some, I'm sure, but couldn't get into my graphical interface. :(

More errors to chew on ^^ :

```
skipping

"usr/X11R6/modules/extentions/libGLcore, a:m_debug_clip.o": No symbols found
"usr/X11R6/modules/extentions/libGLcore, a:m_debug_norm.o": No symbols found
"usr/X11R6/modules/extentions/libGLcore, a:m_debug_x-form": No symbols found

(EE) Failed to load module "ati" (module does not exist)
(EE) Failed to load module "kbd" (module does not exist)
(EE) Failed to load module "mouse" (module does not exist)

Fatal screen error:
No screens found

(WW) Ignoring request to load module GLcore
```

So. Things fixed, and new things to fix. I'm this |--| close to format and reinstall, even if I have to rename the tags of all those 200+ Beatles songs one by one again. ^^

---

### Post by Wolfbite on 2006-01-28
BTW, if all else fails, is it possible to burn files I need to a CD via the terminal?

---

### Post by GeneralZod on 2006-01-28
[QUOTE=Wolfbite]I didn't work. It fixed some, I'm sure, but couldn't get into my graphical interface. :(

So. Things fixed, and new things to fix. I'm this |--| close to format and reinstall, even if I have to rename the tags of all those 200+ Beatles songs one by one again. ^^[/QUOTE]

Don't you have a means of backing everything up?

Anyway, give this a shot:

```

sudo apt-get --reinstall install xserver-xorg-input-kbd xserver-xorg-driver-ati xserver-xorg-input-mouse

```

[QUOTE=Wolfbite]BTW, if all else fails, is it possible to burn files I need to a CD via the terminal?[/QUOTE]

It definitely is possible, but I'm afraid I don't know how; sorry :/ I'm sure plenty of people on these forums do know how, though! :)

---

### Post by Wolfbite on 2006-01-28
Yeah, I usually back things up. But 1) I don't have any DVD-R left 2) I only have 1 partition for Linux, everything else is full, so here I am. 

Ok, gonna try your nifty little code. :)

---

### Post by Wolfbite on 2006-01-28
You are definetily my new hero, General! I'm writing this in Ubuntu! Thanks a lot, man! 


Woot woot woot! :D

---

### Post by GeneralZod on 2006-01-28
[QUOTE=Wolfbite]You are definetily my new hero, General! I'm writing this in Ubuntu! Thanks a lot, man! 


Woot woot woot! :D[/QUOTE]

Glad to hear it :) NOW DON'T GO FIDDLING WITH ANYTHING ELSE! ;)

---

### Post by Wolfbite on 2006-01-28
I sure as hell won't, haha. The only difference from before is that the mouse cursor is black instead of white, but I should be able to fix that, unless of course you know how? ^^

---

