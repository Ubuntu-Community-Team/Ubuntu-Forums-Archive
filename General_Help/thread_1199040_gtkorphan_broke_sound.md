---
title: "gtkorphan broke sound"
date: 2009-06-28
forum: General Help
---

### Post by Richardarkless on 2009-06-28
Hello please can you help me

I was removing some orphan packages from gtkorphan and now I have no sound, all I get is constant fuzzing instead of sound

The soundcard i got is a realtek hd audio alc888

Thanks
Richard

---

### Post by ajgreeny on 2009-06-28
So what did gtkorphan actually remove?  I assume there must be a log of some sort which tells you, and you can then install them again.
Having looked at the website I wonder if you did the initialization that is needed to make sure nothing was removed that may be important.  Here is the paragraph that is on that site:-
> At GtkOrphan's first run, you should initialize your system in order to keep track of needed packages, even if they are reported as orphaned.
In the main window, expand the "Options" section and check the "Show all orphan packages, not only those in the libs section" checkbox. Note: with this option, GtkOrphan will report as "orphaned" all those installed packages that are not dependencies for any other. In this way, for instance, packages such as gparted, ubuntu-desktop, wine will be listed too, as they are "top-level" packages and no other package depends on them. Now you can traverse this list and right-click->hibernate each package you want to keep and that you don't want to be reported as orphaned anymore. The hibernation list will keep these files and will not show them anymore. You can access and modify the hibernation list as you want, from the View menu or from the right-click popup menu.

---

### Post by Soul-Sing on 2009-06-28
Indeed synaptic has a "history" of removed/installed software.

---

### Post by ajgreeny on 2009-06-28
I know synaptic has its own history, but never having used gtkorphan I did not know that removals using that would appear in synaptic's history. Thanks for the info!

---

### Post by Richardarkless on 2009-06-28
> **ajgreeny said:**
> So what did gtkorphan actually remove?  I assume there must be a log of some sort which tells you, and you can then install them again.
Having looked at the website I wonder if you did the initialization that is needed to make sure nothing was removed that may be important.  Here is the paragraph that is on that site:-

I dunno what got removed, I have used this tool in previous version and has been very reliable

I didnt tick the box that displays all the orphan packages, I just removed the ones that are displayed in the lib part.

Where is this log file, I checked under synaptic history and it only seems to say the packages that I removed using the package manager and not gtkorphan

please help me, I had to boot into windows which is a nightmare lol

EDIT: I just looked in the sound configuration and 

it had just messed around with my sound level configurations and sound now works

Thanks for everyones suggestions, I feel stupid now that I didnt check it before wasting all of your time

---

### Post by ajgreeny on 2009-06-29
Don't worry,  I know how a panic can set in when you have everything working OK and then some little action you take upsets the status-quo, and something stops doing what it should.  I'm glad all is well again.

---

