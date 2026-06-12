---
title: "Open programs minimized"
date: 2010-11-12
forum: General Help
---

### Post by slwx on 2010-11-12
Hi, 
I've got a question, it's a bit of a luxury problem but still..

When i start my computer i want some applications to open: skype, amarok, pidgin and lifeograph. I can do this in System -> Preferences -> startup applications and add the programs i want with a terminal command. 
But when my computer starts, i get 4 programs who open on my dekstop, so what i would like to do,is open them minimized as icons in the panel. 

Anyone have an idea? Can I adjust terminal command in a way?

Thanks, 
Mathias

---

### Post by TeoBigusGeekus on 2010-11-12
You can't minimize them separately, but you can use wmctrl to show the desktop after they are loaded.
```
sudo apt-get install wmctrl
```
to install wmctrl
and
```
#!/bin/bash
sleep 5
wmctrl -k on
```
to show the desktop.
Add this script to your startup apps. I added the sleep 5 command to give some time for your apps to load before the show desktop takes place.

---

### Post by slwx on 2010-11-14
Hi, 
Thanks for reply!
How can I parse 3 lines in 1 command? because on startup application manager I can only give one command..
Thanks, Mathias

---

### Post by TeoBigusGeekus on 2010-11-14
Create a file called mystartupscript (or whatever you want).
Add these lines in it:
```
#!/bin/bash
skype &
amarok &
pidgin &
lifeograph &
sleep 5
wmctrl -k on
```
Save it in your home folder.
Open terminal and give
```
chmod +x ~/mystartupscript
```
to make it executable.
Go to Start Up Apps manager and add a start up command with a name of your preference and give its command as:
```
sh /home/yourusername/mystartupscript
```

Adjust the 
```
sleep 5 
```
command accordingly, to allow the programs to load during startup.

---

### Post by slwx on 2010-11-14
Thanks, worked fine! 

Now the programs are minimized in panel below, I'm happy. Still, you think its possible to "close applications" with script, so they get minimized as an icon below?
(I'm having a bit difficulty expressing the question :p but do you understand what i mean?)

---

### Post by TeoBigusGeekus on 2010-11-14
No, I don't think you can do that. If someone knows a way, speak now or forever hold your silence.

---

### Post by SeijiSensei on 2010-11-14
Skype and amarok have configuration options to make them minimize themselves to the system tray at startup.  In Skype, though, I think that may only work if you have it save your password.  I've not run the other programs so I don't know if they offer the same option as well.

---

### Post by slwx on 2010-11-15
ok, 
thanks guys!

---

