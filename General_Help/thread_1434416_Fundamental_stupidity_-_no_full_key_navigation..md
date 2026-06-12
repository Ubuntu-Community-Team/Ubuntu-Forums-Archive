---
title: "Fundamental stupidity - no full key navigation."
date: 2010-03-20
forum: General Help
---

### Post by Poodle Doodle on 2010-03-20
I like the idea of multiple redundancies.

Like for instance, where I live it's about 40Km between towns... I ride a pushbike everywhere.

So I have multiple redundancies for the system. I carry enough water to give me 500 ml every 10Km. I have a taped up bike pump - free of dirt and dust, locked to the frame. I always use another pump to do the tyres up. I carry a tool kit with one of every tool, for the bike, a spare tube and a patch kit with a tube of glue in a sealed crush resistant container. I also carry a cigarette lighter, in case of strandings overnight, and a chain breaker and 2 joining links.

I am never stuck.

With HOW Ubuntu is set up however, it's riddled with fundamental faults, that with the activation of that ONE single fault, the whole operating system crashes and or becomes unuseable.

One of these long standing faults is the complete LACK or inability to totally navigate through the entire system via keyboard short cuts and to thicken that up a bit more; there is no easy to call up list of short cuts for the ENTIRE system.

Today I "autohid" one of the two panels, partly while downloading a heap of new programs, and moved what I was doing to a new screen.

What then happened was that the panels locked up with the auto-hid under the other (both up top) - and the desktop navigation, and all the software and the machine controls went with it.

Neither panel would respond, no controls and the Alt + F2 would not appear...

Nothing.

A complete and total lock up.

The weak point being that if the panels are inoperative - and depending upon the state of ones mouse or not, and a few other things., the lack of being able to navigate past that weak point, via any other means - does not exist.

It's pathetic.

So I opened a gif file on the desk top, with Firefox and then accessed the web via that, and looked up - for an hour or two to find this solution:

 Re: panel (not responding)
When you manage to start ubuntu hit ctrl+alt+f4 to go to a shell. Login using your details, and then to delete the panel configurations:

Code:

cd ~/.gnome2
rm -fr panel2.d
cd ~/.gconf/apps
rm -fr panel

then to restart the system:
Code:

sudo shutdown -r now

and I believe you'll be OK when you log back in.



Although the directions were very poor for a newbie, they were understandable to me and I was able to execute them and get all functions via the PANELS restored.

OK so I was only saved by being able to back door my way onto the web, lots of hard research, some one leaving a solution to the problem, and me being able to "fill in the gaps" enough to execute them.

But the fundamental point still exists of ONLY being able access all functions through the panel/s via a mouse.

This is bad. There is no parallel routing via keyboard short cuts, either through this ONE fundamental weak point, or through the entire operating system, settings, controls and software.

There is not even a list of the shortcuts through the "Ubuntu help" either.

This whole situation of the lack of dual operation and navigation through the entire operating system is crap - and it has to change.

I have raised this issue a few years back and nothing was done with it.

I want to see everything within Ubuntu become operable via full keyboard navigation, as well as the mouse operation.

---

### Post by efflandt on 2010-03-20
If X or something else locks up, any X or window manager shortcuts from there may be inoperative anyway.

But you can take steps to try to avoid a corrupt filesystem using Alt + SysRq + key combinations, especially Alt + SysRq + S to sync the file system.

One example found in a web search:
[http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html](http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html)

---

### Post by Poodle Doodle on 2010-03-20
Yeah thanks.. that's a good contribution but it's a fundamental flaw in the operating of Ubuntu.....

One ought to be able to navigate through the entire operating system and use all of the software, by the keyboard alone.

Ubuntu / Linux should have been built like that from the ground up - but the trend setters of pretty interfaces, now impose an operating system without the "ground level" reality checks - and there is NO list of keyboard short cuts - to back up the list of mostly non existant functions...

Time to implement Alt + A for Applications, Alt + P for Places and Alt + S for Systems - etc., from then on; as formal systems control.

And we NEED a printable shortcut key stroke list to go with it.

All software for Linux must now begin to implement this program of being able to run fully via the keyboard too.

This "click only" control has to go.

---

