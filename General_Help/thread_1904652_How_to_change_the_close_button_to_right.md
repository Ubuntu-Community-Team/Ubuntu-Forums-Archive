---
title: "How to change the close button to right"
date: 2012-01-05
forum: General Help
---

### Post by meetdilip on 2012-01-05
Got used to it being on right. Is there any way to move close, minimize, maximize buttons to right ? Also can we get aero in 11.10 ? I have 6 GB RAM and AMD graphics card.

---

### Post by sj1410 on 2012-01-05
open gconf-editor

The key that we want to edit is in apps/metacity/general. Click on the + button next to the &#8220;apps&#8221; folder, then beside &#8220;metacity&#8221; in the list of folders expanded for apps, and then click on the &#8220;general&#8221; folder. 

The button layout can be changed by changing the &#8220;button_layout&#8221; key. Double-click button_layout to edit it.

Change the text in the Value text field to:

menu:maximize,minimize,close

Click OK and the change will occur immediately, changing the location of the window buttons in the Configuration Editor.

---

### Post by meetdilip on 2012-01-05
Thanks sj.

Where can I find " gconf-editor " in 11.10 ? Sorry, very new to Ubuntu.

---

### Post by sj1410 on 2012-01-05
> **meetdilip said:**
> Thanks sj.

Where can I find " gconf-editor " in 11.10 ? Sorry, very new to Ubuntu.

Press Alt+F2 to bring up the Run Application dialog box, enter “gconf-editor” in the text field, and click on Run.

---

### Post by meetdilip on 2012-01-05
It shows gconf-editor icon. But when I click, the whole screen vanishes and I am back to my work space. :(

---

### Post by ajgreeny on 2012-01-05
I think you may have to install gconf-editor first in 11.10, as I don't think it's installed by default now.

See also [http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961) which gives some clues on how to get the classic gnome desktop (or nearly so) in 11.10.

---

### Post by meetdilip on 2012-01-05
Thanks for the help. I had to install gconf-editor editor using Synaptic Package Manager and changed the button location. It did move to right side but only when we resize the window. Normally, on maximize condition, it stays on left side as right side is occupied by shutdown and other options. 

The classic looks seems to be better in terms of usability. I did installed Gnome shell using
> 
sudo apt-get install gnome-shell

Does it give a different interface ?

---

### Post by Frogs Hair on 2012-01-05
Yes , the Gnome Shell has a very different interface . See the link for information and screen shots . [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

Another option to move buttons is the window manager settings in Ubuntu Tweak .  You can install the application with the following commands .
```
sudo add-apt-repository ppa:tualatrix/ppa

``````
sudo apt-get update && sudo apt-get install ubuntu-tweak
```

---

### Post by oxf on 2012-01-05
Scroll down to button placement

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by meetdilip on 2012-01-05
Thanks. How to activate it, try and go back if not good ?

Any other similar interfaces in Ubuntu ? Aero is not available in Ubuntu ? 

Forgive my ignorance, very new to Ubuntu. :)

---

### Post by ajgreeny on 2012-01-05
You could always try Xubuntu, which is more like the classic gnome desktop.  Some of the default applications are different to the gnome defaults, but everything is available in the repos so you can use whatever application you want, eg nautilus instead of thunar for file management, etc etc.

---

### Post by meetdilip on 2012-01-05
Thanks [ajgreeny]("http://ubuntuforums.org/member.php?u=27747").

---

