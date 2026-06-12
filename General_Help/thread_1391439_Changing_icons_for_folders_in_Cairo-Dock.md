---
title: "Changing icons for folders in Cairo-Dock"
date: 2010-01-26
forum: General Help
---

### Post by El Pinguino on 2010-01-26
Does anyone know how to add a folder to the dock (not monitored) and then change the icon so that it is something other than the ordinary folder icon?

Or to rephrase.  I've dragged/dropped a folder onto the dock.  It works nicely.  I'd like to change the icon so that it doesn't look like the generic paper folder icon.

---

### Post by hemimaniac on 2010-01-27
right click on the icon in question and in that pop-up box you can click on the picture of the icon, navigate to its replacement icon and select it

---

### Post by El Pinguino on 2010-01-27
This works of course for a regular folder, but within Cairo-Dock the 'properties' option doesn't present an icon to change.  Also, the 'modify this launcher' option only has a field saying 'uri of the file' ... and no icon to modify.

And changing the folder icon before dragging it onto cairo-dock doesn't seem to make a difference (i.e., the generic folder icon is used in the dock).

I've got cairo-dock version 2.1.1-2 if that helps.

---

### Post by fabounet on 2010-01-27
this has been fixed in the 2.1.3 ;-)
by the way, if you don't monitor the folder's content, you can just make a nautilus launcher, and modify the command to 
nautilus /path/to/folder
(nautilus or whatever file navigator you use)

---

### Post by El Pinguino on 2010-01-27
Ha, fixed in the next version.  Now to decide if I wait for the official repositories to update or ...

And using nautilus didn't work quite the same as dragging a regular folder because with a folder on the dock each time you click it opens a new window.  With a call to nautilus it just refocuses/minimizes on the nautilus window (if you've opened it once before).

Thanks for the suggestion and the info about the fix though.

How exactly is it fixed? Is the image carried over from the folder or symbolic link to the folder if you've changed the icon there?

---

### Post by El Pinguino on 2010-01-27
Ah, I see.

I got installed the launchpad repo as here:
[https://launchpad.net/~cairo-dock-team/+archive/ppa](https://launchpad.net/~cairo-dock-team/+archive/ppa)

And then when you drag a folder and choose 'modify launcher' it gives the option to change the icon.

Problem solved.

Thanks all.

---

### Post by fabounet on 2010-01-28
you're welcome :)

> And using nautilus didn't work quite the same as dragging a regular folder because with a folder on the dock each time you click it opens a new window. With a call to nautilus it just refocuses/minimizes on the nautilus window (if you've opened it once before).

about that point, that's true since launchers and apps icons are mixed, but you can bypass this behavior for launcher individually.
open the launcher's config, and in "extra parameter"s tick the option "Prevent this launcher from stealing appli from taskbar" ;-)

---

### Post by El Pinguino on 2010-01-29
> **fabounet said:**
> you're welcome :)



about that point, that's true since launchers and apps icons are mixed, but you can bypass this behavior for launcher individually.
open the launcher's config, and in "extra parameter"s tick the option "Prevent this launcher from stealing appli from taskbar" ;-)

Cool!  Wish I'd known that earlier.  Would have saved me a bunch of googling ... and starting this thread.
:)

Thanks again.

---

