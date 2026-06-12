---
title: "How do I create a &quot;Show Desktop&quot; &amp; &quot;Main Menu Bar&quot; launcher on Ubuntu"
date: 2010-03-09
forum: General Help
---

### Post by Nightstrike2009 on 2010-03-09
Hiya

I want to know how to create a "Show Desktop" & "Main Menu Bar" launcher on my desktop so i can drag & drop it into my dock bar.

Does anyone know the commands for these?

---

### Post by mapltux on 2010-03-09
On the panel when you right click on an empty space and choose Add to Panel. Show Desktop should be there in 'Add to Panel' 

For more launchers you can select Custom Application Launcher. Create Launcher dialog box is displayed

Fill in the Properties like Type, Name, Command etc

Name is whatever you'd call it
Command is what you'd like it to do for you
Then the No Icon, can help you choose an icon for the launcher.

Hope this helps.

---

### Post by Revolutionary101 on 2010-03-09
To create a launcher to show your desktop install the package "wmctrl". Install it by typing this into terminal:
```
sudo apt-get install wmctrl
```
After doing that create a launcher and insert the command
```
wmctrl -k on
```
Into the command line of the launcher.

Although, I don't know how to create a launcher for the Main Menu Bar.

---

