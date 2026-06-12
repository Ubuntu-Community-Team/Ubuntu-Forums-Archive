---
title: "dapper screensaver preferences"
date: 2006-06-08
forum: General Help
---

### Post by u-blunt-2 on 2006-06-08
What happened to Breezy's gnome-screensaver-preferences GUI ? I had my screensavers all setup like I wanted before the upgrade to Dapper. Now my config is lost and I don't know how to modify their options ](*,) 

Must I go through console ?

---

### Post by 23meg on 2006-06-08
xscreensaver was replaced with gnome-screensaver in Dapper. It was briefly introduced towards the end of the Breezy release process as well, and was taken back on popular demand.

More info, with some technical justification here: 

[http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions](http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions)

---

### Post by u-blunt-2 on 2006-06-08
muchas gracias !
However, I still don't know how to modify gnome-screensaver options... Can I resort to my .xscreensaver file ?

---

### Post by 23meg on 2006-06-13
Refer to [this guide]("http://ubuntuforums.org/showthread.php?t=195557") if you'd like to replace gnome-screensaver with xscreensaver.

---

### Post by jejones3141 on 2006-06-13
[QUOTE=u-blunt-2]muchas gracias !
However, I still don't know how to modify gnome-screensaver options... Can I resort to my .xscreensaver file ?[/QUOTE]

No. gnome-screensaver **by design** takes essentially all control from the user and gives it to the system administrator. In the opinion of the program's developer, that's not a bug, it's a feature.

If your system has two users whose taste in screensavers differ, then if you're using gnome-screensaver, too bad--they're out of luck.

The only way to give the user back control is to use xscreensaver instead of gnome-screensaver. Fortunately, [a very good HOWTO]("http://ubuntuforums.org/showthread.php?t=195557&highlight=gnome-screensaver") exists that tells you how to do that. Come to think of it, I think I'll go suggest to the authors of AUTOMATIX and Easy Ubuntu that dumping gnome-screensaver in favor of xscreensaver be added as an option to those programs.

---

### Post by mlind on 2006-06-13
This was one of the hot topics on Dapper devel forums, and on Gnome bugzilla too.. 

Some gnome devs think that Average Joe user wouldn't ever need 'preferences' 
dialogs.. too bad.

---

### Post by etitor on 2006-06-14
[QUOTE=jejones3141]No. gnome-screensaver **by design** takes essentially all control from the user and gives it to the system administrator[/QUOTE]
I understand the policy. But suppose I am the system administrator (and unique user). Where do I look for a place to change preferences as deeply as a system administrator would want to do? (I mean, without replacing gnome-screensaver by anything else.)

---

### Post by Turin Turambar on 2006-06-14
Etitor, that's what I would like to know too.

---

### Post by twopeak on 2006-06-15
[quote=Turin Turambar]Etitor, that's what I would like to know too.[/quote]That makes 3 of us already.

How to change the preferences (like where the pictures folder is located) of screensavers?
And additionally: can I get back old screensavers? I don't like the ones that exist now and I did like several "old" ones.

And this removing preferences is a sad choice, I love linux because it has so many choices.

---

### Post by u-blunt-2 on 2006-06-15
The only way is to replace gnome-screensaver with xscreensaver. I understand why gnome-screensaver comes default, but their should be some way to choose  X over gnome. 
I switched back to X to get the cool 3D structures of some custom genetic molecules spinning on my screen again, and to make my collegues wonder at my screen while I'm taking a dump :KS

23meg : Thanks for the link, worked great!

---

### Post by mlind on 2006-06-15
[QUOTE=twopeak]How to change the preferences (like where the pictures folder is located) of screensavers?[/QUOTE]

```

grep -i ^exec /usr/share/gnome-screensaver/themes/personal-slideshow.desktop

```

---

### Post by kjkrum on 2006-06-16
[QUOTE=mlind]Some gnome devs think that Average Joe user wouldn't ever need 'preferences' dialogs.. too bad.[/QUOTE]

Then some GNOME developers are idiots.  I remember when removing end-user functionality and calling it an improvement was one of the biggest things OSS developers criticized Microsoft for.

---

### Post by Stroganoff on 2006-06-18
FULL ACK
gnome is gonna be linux' downfall!

---

### Post by twopeak on 2006-06-19
Meanwhile I've removed gnome screensaver and reinstalled the other one (with the cool juggling guy and a decent photo slideshow)
But now the updater wants to make me install gnome screensaver...
I suppose that if I do so, i will have to change screensaver again?
Is there a way to ignore that?

---

### Post by droazen on 2006-06-19
[QUOTE=u-blunt-2]The only way is to replace gnome-screensaver with xscreensaver.[/QUOTE]

This is not quite true - it **is** possible to change screensaver settings in gnome-screensaver, it's just a pain. Read the man page for your screensaver(s), and figure out the command-line options needed to get the behavior you want. Then cd into /usr/share/gnome-screensaver/themes, find the .desktop file for your screensaver, add your command-line options to the "Exec=" line, and reboot (or manually kill/restart gnome-screensaver).

Hopefully the developer will eventually come around & add a GUI way to do this...

---

### Post by IbeeX on 2006-06-19
Since this is realy anoying thing that GNOME develepers did I would like to give my wote that anybody who thinked that users dont need to change setting is screen saver should at least take five more seconds to think about it and put it back !!!

---

### Post by pchr on 2006-06-19
[QUOTE=IbeeX] should at least take five more seconds to think about it and put it back !!![/QUOTE]

If 90% of people don't need it then leave it in for the 10% on an "Advanced" tab or something like that, don't alienate the odd 10% (Although I'd have thought the proportion of people who want control of their screen savers is higher than 10%)

---

### Post by twopeak on 2006-06-19
[quote=pchr]If 90% of people don't need it then leave it in for the 10% on an "Advanced" tab or something like that, don't alienate the odd 10% (Although I'd have thought the proportion of people who want control of their screen savers is higher than 10%)[/quote]I wouldn't go check who need it, but rather who has been looking for it. Personally I can't believe it's only 10% as both Microsoft and Apple have deemed customisation important enough.
Anyway, as I suppose no developpers are reading this, it doesn't really matter discussing it here.

*a solution to my problem of the auto updater would still be nice ;) *

---

### Post by bruce89 on 2006-06-19
I hear that Linus will be along to flame Gnome on this thread soon.

---

### Post by pchr on 2006-06-19
[QUOTE=bruce89]I hear that Linus will be along to flame Gnome on this thread soon.[/QUOTE]

LOL!  Yeah, lets get things into perspective, Gnome has it's plus points, in my eyes mainly that it's the native home to Gimp, Inkscape and lots of over apps I love.

---

### Post by IbeeX on 2006-06-19
[QUOTE=pchr]LOL!  Yeah, lets get things into perspective, Gnome has it's plus points, in my eyes mainly that it's the native home to Gimp, Inkscape and lots of over apps I love.[/QUOTE]

But sometimes it looks like Gnome developers think that users are idiots and that any option that even remotely looks like advance should be hidden from them.

Any why is there some petition going aroud to fix this bug?

---

