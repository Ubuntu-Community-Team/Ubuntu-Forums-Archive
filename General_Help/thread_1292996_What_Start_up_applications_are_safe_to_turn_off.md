---
title: "What Start up applications are safe to turn off?"
date: 2009-10-16
forum: General Help
---

### Post by ductiletoaster on 2009-10-16
Im try to squeeze ever little bit of performance out of my Ubuntu 9.04 machine. The title says it all however maybe a better question would be what start up apps are not safe to turn off... Also Has any one heard of bum... its supposed to be an app for runtime services..?

THoughts...Thanks

---

### Post by beastrace91 on 2009-10-16
Depending on what you use your system for the following are safe to turn off:

[list][*]Bluetooth Manager
[*]Check for new hardware drivers
[*]Evolution Alarm Notifier
[*]Print Queue Applet
[*]Remote Desktop
[*]Screensaver
[*]Update Notifier
[*]Visual Assistance
[*]Volume Control[/list]

Odds are you might be able to trim out a few others as well but these are ones you can drop for sure with out loosing any large functionality.

~Jeff

---

### Post by nothingspecial on 2009-10-16
The most important ones are not in your system > preferences > start up applications. You can remove anything from there.

For your performance issues have a look at [[COLOR="Magenta"]this[/COLOR]]("http://sites.google.com/site/masonux/").

I don`t use it myself as I prefer to use Ubuntu server edition on my old machine but I have tried it. It`s a nice project.

---

### Post by brookie on 2009-10-16
> **beastrace91 said:**
> Depending on what you use your system for the following are safe to turn off:

[LIST]
[*]Bluetooth Manager
[*]Check for new hardware drivers
[*]Evolution Alarm Notifier
[*]Print Queue Applet
[*]Remote Desktop
[*]Screensaver
[*]Update Notifier
[*]Visual Assistance
[*]Volume Control
[/LIST]
 J, any ideas how to turn these off in intrepid? ;) 

edit...I found some in system services, but also found one called mail agent exim4. i use gmail so can I turn this one off? I turned off brail and bluetooth.

---

### Post by ajgreeny on 2009-10-16
Yes, I know and use bum (**B**oot**U**p **M**anager) and find it very useful for stopping some of the startup utilities and applications or daemons.  I attach a screenshot of the window showing what I have disabled, but your needs may be different.  Note I have a desktop not a laptop, so you may need to keep some things I have removed.

I also removed all the items mentioned in Beastrace91's post from the System ->Startup Applications and everything still works great.  I hope this helps.

---

### Post by scouser73 on 2009-10-16
Check [[COLOR="Red"]**Ubuntu: Speed Up Ubuntu**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491") for seeing which applications you don't need at startup.  Although the post is from 2005 it is still relevant for today's Ubuntu distributions.

---

### Post by beastrace91 on 2009-10-16
> **brookie said:**
> J, any ideas how to turn these off in intrepid? ;)

It's been awhile but I believe in intrepid start up applications are listed under System->Preferences->Sessions

EDIT: Also note these settings are on a laptop - so if you are on a desktop you could also for instance remove power manager :)

~Jeff

---

### Post by oldos2er on 2009-10-16
> **brookie said:**
> J, any ideas how to turn these off in intrepid? ;) 


 I use sysv-rc-conf.

---

### Post by ajgreeny on 2009-10-17
> **oldos2er said:**
> I use sysv-rc-conf.
But use this with care and fully understand what you are doing first, or you could come completely unstuck.  It is a cli utility and not as easy to work with as bum, though actually more powerful.

Scouser73's post contains a link to much more info on that way of doing it so read that carefully.

Oh, and good luck!

---

### Post by ductiletoaster on 2009-10-17
Sorry i was out finally got back online... thanks people for the info. totally will check into some of these

---

### Post by ductiletoaster on 2009-10-17
O and to clarify im not having any issues with performance.... Im just trying to opt. my computer. I have two main machines and this one is running Ubuntu and i use it almost only for programming. Even though this isnt my best machine Its nothing to laugh at. 3.3ghz single core with 2gbs of ram....However it seems like a waste to have services and programs running that i neither use nor want. 

So this kinda brings me to another question.... Ubuntu comes packaged with software i dont use... in fact alot of software! most of which i cant un-install without un-installing ubuntu-desktop package... 

So i have been hearing alot about Arch linux (I know it comes without a GUI but.... has anyone Used it and what Desktop package? Share please... Thanks

---

### Post by brookie on 2009-10-18
thanks J! i looked all over for that. so they were in 'sessions'. sweet! :) i got some of the stuff in the list unchecked. will reboot and check if this old laptop seems faster. sigh...

---

### Post by ajgreeny on 2009-10-18
> **ductiletoaster said:**
> So this kinda brings me to another question.... Ubuntu comes packaged with software i dont use... in fact alot of software! most of which i cant un-install without un-installing ubuntu-desktop package... 

So i have been hearing alot about Arch linux (I know it comes without a GUI but.... has anyone Used it and what Desktop package? Share please... Thanks
You can quite safely uninstall any package, along with the ubuntu-desktop package, if you wish.  ubuntu-desktop is not actually a real package with anything in it, just a "meta-package", meaning it simply ensures all packages for a full ubuntu are installed; it is a dependency list, if you want to equate it to something.  If you don't want all the applications in ubuntu you can safely remove that dependency list, and it only would be needed again if you tried to do an online version upgrade, eg from 9.04 to 9.10.

As for Arch, I don't know, but from what I've read it sounds interesting, but hard work compared to ubuntu.

---

