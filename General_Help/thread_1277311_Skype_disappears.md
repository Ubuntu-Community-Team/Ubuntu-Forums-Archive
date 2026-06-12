---
title: "Skype disappears"
date: 2009-09-28
forum: General Help
---

### Post by DJonsson2008 on 2009-09-28
I start skype and it seems to be running.
Alt-Tab allows me to switch to it, but sometimes
it disappears from both the panel and alt-tab.

Attempting to start the program again I'm told
another instance exists.

Does anybody know how to keep skype visible on
the panel and/or via alt-tab?

---

### Post by Bucky Ball on 2009-09-28
Installed with Synaptic Package Manager?

---

### Post by DJonsson2008 on 2009-09-28
No I installed from the deb file provided by Skype.
Presently using the Linux Beta 2. Previously I 
did load Skype from Synaptic, but had to allow mediubuntu
or some other package repository in order to get it to 
install - Still though had the same problem with earlier
Synaptic Skype 1.* installed with Synaptic.

---

### Post by djwkd on 2009-09-28
Well, i know this isnt much use, and its not a bug fix, its a workaround (sort of).
You can end the process in System Monitor, and switch to processes or something on there. Aplogies if this isnt entirely right, im currently on a school computer running windows.

---

### Post by DJonsson2008 on 2009-09-29
Thanks that certainly works as a workaround.
I'm still wondering though if there some way as well
to prevent it from disappearing.

---

### Post by lesta on 2010-09-24
I'm having the same problem. Time to time skype just dissapears. 

While I was looking for solution I found a simple workaround which fits for me. As I'm using pidgin for messanger client I found that there is skype-pidgin package. After installing this package you can use Pidgin as Skype's frontend.

I also found that you can enable Skype logging [http://developer.skype.com/SkypeGarage/LogFile]("http://developer.skype.com/SkypeGarage/LogFile") by creating folder /Log under .Skype data folder. But the log files are in some kind of random binary format. This is probably due to the reason they are so keen about their intellectual property. You could send some logging output to Skype and hope they will some day fix this bug. But as I'm too lazy I will first try to use my pidgin solution.

---

### Post by DJonsson2008 on 2010-09-24
Thanks lesta for the tip...

I also found a workaround by using the following script,
to start re/start Skype. This script is linked the to
the Skype launcher icon on my desktop I use to start Skype.

*****************************************
#!/bin/bash
killall skype
skype
*****************************************

Your solution, of using Pigdin sounds better though, 
and opens up other chat possibilities as well. 
I'll try it sometime.

Another solution I've found, is to add the notification
panel to the panel. 

This can be done by right clicking on a blank space of
the panel, then click on 'ADD...'. The locate the add-on
In Xubuntu this is called System Tray:Show Notification Icons,
on Ubuntu I think its simply called - Notification Area

---

