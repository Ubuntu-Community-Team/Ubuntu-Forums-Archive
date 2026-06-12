---
title: "Make Apps Start up at Boot Time"
date: 2011-07-31
forum: General Help
---

### Post by JoshuaBranson on 2011-07-31
I've got a couple of lofty goals for my fresh Xubuntu install. Is it possible to do any of the following? And I'd LOVE to know how to any of the following using scripts!

        1) Create a hot key that will open a Terminal? (preferably Control + Alt + T)

        2) Automatically start Firefox at start up. (preferably minimized.) 

        3) Only allow my computer to connect to the internet when
            1) using Firefox or Evolution
            2) briefly at start up to allow Update Manager to check for Xubuntu updates

        4) TURN OFF STUPID mouse clicks with the Touchpad taps. (There's a command that does that: "synclient TapButton1=0". Is it possible to write a script that will run that command at start up?)

---

### Post by Toz on 2011-08-01
> **JoshuaBranson said:**
> I've got a couple of lofty goals for my fresh Xubuntu install. Is it possible to do any of the following? And I'd LOVE to know how to any of the following using scripts!

        1) Create a hot key that will open a Terminal? (preferably Control + Alt + T)
Go to Settings->Settings Manager->Keyboard (or run **xfce4-keyboard-settings** from the command line). Click on the "Application Shortcuts" tab, then:
[LIST]
[*]Click the "Add" button
[*]Enter (without quotes) "xfce4-terminal"
[*]On the next screen, type in your keyboard shortcut (in your case, Ctrl+Alt+T)
[/LIST]

>         2) Automatically start Firefox at start up. (preferably minimized.) 
Settings->Settings Manager->Session and Startup (or run **xfce4-session-settings** from the command line). Click on the "Application Autostart" tab, then:
[LIST]
[*]Click the "Add" button
[*]Set the Name to "Firefox"
[*]Set the Description to "Firefox"
[*]Set the command to (no quotes) "firefox"
[/LIST]
Firefox will now start automatically when you log in. To make it start minimized, you will need to use an application like **devilspie**. For more information, have a look at: [http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html]("http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html")

>         3) Only allow my computer to connect to the internet when
            1) using Firefox or Evolution
            2) briefly at start up to allow Update Manager to check for Xubuntu updates
Not sure, may involve something like: ifconfig up -> run app -> ifconfig down

        4) TURN OFF STUPID mouse clicks with the Touchpad taps. (There's a command that does that: "synclient TapButton1=0". Is it possible to write a script that will run that command at start up?)[/QUOTE]

[LIST=1]
[*]Create a script called ~/syncl
```
mousepad ~/syncl
```
with the following contents
```
#!/bin/bash
bash -c "synclient TapButton1=0"
```
[*]Make it executable
```
chmod +x ~syncl
```
[*]Add it to your startup like the firefox example above.
[/LIST]

---

### Post by JoshuaBranson on 2011-08-01
THANK YOU SOOO MUCH! If Ubuntu forums had a Like button. I would have totally liked your response!

---

### Post by Toz on 2011-08-01
Too funny. And oh by the way, welcome to the forums.

---

