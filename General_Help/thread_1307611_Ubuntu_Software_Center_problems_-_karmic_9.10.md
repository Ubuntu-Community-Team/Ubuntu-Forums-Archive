---
title: "Ubuntu Software Center problems - karmic 9.10"
date: 2009-10-31
forum: General Help
---

### Post by dj-toonz on 2009-10-31
Hi all, Ubuntu software center is doing my head in. 

1) why do I have to type my password in & then click on authorize a second time after clicking on authorize once I type my password in?? 

(what i mean is, say I want to install blender for example, I type in blender in the search bar or click on install software, Graphics, scroll down to blender then click on the green arrow next to blender , Wait for the screen shot to show up for blender & the details about the application, then click on install, the box shows up to enter the user password, I do that & click on authorize, Then a couple of seconds after, another box pops up with blah blah blah, then cancel & authorize??? then I click that again then it takes me to another page with 1 single application & a scrolling bar, once that's finished installing takes me back to the blender page with remove or visit homepage)

2) why can't u install more then 1 application at the same time instead of just having to install 1 then re-go though having to do all the same routine with entering your password again & again for every application you want to install 

me thinks I might keep to using sudo apt-get install [name of packages] instead of the software-center as with that way i can install more then 1 application without having to jump though hoops just to install anything

could some kind soul explain how to install things though software-Center properly as I think I might not be using it or understanding it proper, cheers

---

### Post by 3rdalbum on 2009-10-31
That's not how it should be; you should be asked to authorise when you install the first package, and then your install privilege will be retained for a certain period of time or until you click the "Drop privileges" icon in the notification area.

You can line up multiple installations - they will occur one after the other, and shouldn't fire up another Policykit authorisation dialog.

Maybe check Launchpad to see if there's a bug report already for this.

---

### Post by dj-toonz on 2009-10-31
Thanks reported the problem to launchpad bug number is bug-466504 (hope they take a look at it & see if it is a bug or if it should be like that) cheers

---

### Post by 6205 on 2009-10-31
Do yourself a flavor, uninstall that crap.. All you need is Synaptic, or maybe Ubuntu Tweak..
[https://launchpad.net/~tualatrix/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=karmic](https://launchpad.net/~tualatrix/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=karmic)

---

