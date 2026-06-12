---
title: "creating launcher for wine application"
date: 2012-08-15
forum: General Help
---

### Post by LLCoolJeff on 2012-08-15
I wanted to create a custom launcher for a wine application on unity, but I ran into a problem.. I was following the basic tutorial here : [http://www.hamaluik.com/?p=283](http://www.hamaluik.com/?p=283)

The icon and shortcut was created fine but it did not launch when it was clicked. So I figured I would try launching from terminal to see if I got the command right and this is what I got:

```
$ /home/jeff/.wine/dosdevices/c:/Program Files (x86)/OANDA - MetaTrader/terminal.exe
bash: syntax error near unexpected token `('

```

So I figure that is where the problem lies, how do I get around this? and is there an easier way to create a launcher than what I am doing? I tried dragging the .exe from the program files to the launcher but it did not work..

Thanks

---

### Post by Zvlwab on 2012-08-15
Try this:
```
wine "/home/jeff/.wine/dosdevices/c:/Program Files (x86)/OANDA - MetaTrader/terminal.exe"
```

---

### Post by LLCoolJeff on 2012-08-15
Thanks buddy that worked, althought I do have another issue now...

The icon shows as a question mark instead of showing the icon I selected? I have converted the .ico into a .png and provided the appropriate path to it in the gedit file but it is showing as a question mark...any ideas?

---

### Post by evilsoup on 2012-08-15
I've had that problem with a few custom launchers, logging out and in again fixed it for me.

---

### Post by LLCoolJeff on 2012-08-15
> **evilsoup said:**
> I've had that problem with a few custom launchers, logging out and in again fixed it for me.

hmm.. did not work for me. how would I go about editing the file from the terminal? I saved it to "usr/share/applications" using "gksudo gedit "filepath" but I cannot figure out how to open it back up and edit it without first deleting it and making a new one.

---

### Post by LLCoolJeff on 2012-08-15
la bumpa

---

### Post by evilsoup on 2012-08-15
Hmm. Double-check the path to the icon within the text file, bearing in mind it's case-sensitive... also put double-quotes around the path, in case there are any spaces in any of the directories.

---

### Post by LLCoolJeff on 2012-08-15
I double double checked the path, and everything is correct, here is my code for the gedit file, tell me if I have the syntax and everything right...

```
[Desktop Entry]
Version=4.0
Type=Application
Terminal=false
StartupNotify=true
Icon="/home/jeff/Pictures/Icons/Oanda.png" # fill in path to logo
Name=OandaMT4
Comment=Forex Trading # any description
Exec=env UBUNTU_MENUPROXY=0 wine "/home/jeff/.wine/dosdevices/c:/Program Files (x86)/OANDA - MetaTrader/terminal.exe" # fill in path to the executable
Categories=Application;Oanda;Forex # add as many categories as you see fit
```

One thing I thought about after doing some reading...Does it matter that the icon is an absolute path that is outside of the normal /usr/share/icons path? is your icon in that folder?

---

### Post by LLCoolJeff on 2012-08-15
To get the icon to show I actually had to try a few different things, I'll list them..

first - I thought I would try to copy how some of the other applications had them setup, so I looked at gimp and then changed "Icon=" to "gimp" which is the way it was setup in the gimp.desktop. this worked and made my program icon the gimp icon

second- so then I figured I just had to move my icon to the same folder and do the same thing and everything would be fine, so I made sure that the dimensions were the same as the gimp icon and changed moved it there from the terminal using sudo mv. Then changed the gedit file. STILL NO DICE

third - I went and copied the gimp file and my icon file to the desktop, I figured something must be wrong with my file, I opened both of them, deleted the gimp picture, copied and pasted my icon picture into it. Renamed and moved it back to the folder where gimp icon was stored. NOPE

fourth - I tried changing the "Icon=" to a direct path which was "/usr/share/icons/hicolor/64x64/apps/oanda.png". NOPE

fifth - I tried moving it to another directory within the icon folder because there are a lot of different places you can move it in there, I moved it out to "/usr/share/icons". FINALLY IT WORKED.

of course I had to logout and log back in to see it but it was finally there. It seems you have to move it into that specific folder if you are making it custom, at least I cannot figure out any other way....

---

