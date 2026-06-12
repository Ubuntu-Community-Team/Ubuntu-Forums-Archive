---
title: "mousekeys - Wont disable in Oneiric with Gnome 3"
date: 2012-01-25
forum: General Help
---

### Post by morcomm on 2012-01-25
Hi, after the last update - I can't seem to disble mousekeys. This was magicly turned on. I need my Numpad seriously!!!!

I have tried the following solutions:

Ctrl + Shift + Numlock (unseccesful)
Alt + Shift + Numlock (unseccesful)
Superkey + Shift + Numlock (unseccesful)

And

I did the following
```
~$ sudo gedit /home/mark/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml
```

I then changed the following line of code:

```
<entry name="mousekeys_enable" mtime="1327473736" type="bool" value="true"/>
```

to

```
<entry name="mousekeys_enable" mtime="1327473736" type="bool" value="false"/>
```

I save the file and closed Gedit. I then reopened the file to make sure the change was made, and it was. Yet the mousekeys was still enabled. I then rebooted and the problem persisted. Also the Bool above reverted to true.

I have now run out of options - Please help!

---

