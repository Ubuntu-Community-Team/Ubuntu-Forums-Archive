---
title: "Can't disable trackpad."
date: 2011-08-23
forum: General Help
---

### Post by Number3124 on 2011-08-23
I can't seem to disable my laptop's trackpad. I use a USB mouse, and would like to turn the track pad off when I have my mouse plugged in. I've installed Gpointing Devices, but it seems to lack some of the settings it was supposed to have. I've attached a screenshot.

---

### Post by loolooyyyy on 2011-08-23
> **Number3124 said:**
> I can't seem to disable my laptop's trackpad. I use a USB mouse, and would like to turn the track pad off when I have my mouse plugged in. I've installed Gpointing Devices, but it seems to lack some of the settings it was supposed to have. I've attached a screenshot.


try                               "synclient TouchpadOff=1" in terminal which probably wont work since it's not a Touchpad
so try 
```
sudo modpobe -r psmouse
```which you might have to replace "psmouse" with the proper one
and to enable
```
sudo modprobe psmouse
```there is also:
```
  xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0 
  xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1
```which again you might have to replace "PS/2 G..............." find it by "xinput list"
both can be assigned keyboard shortcuts or a launcher in panel, if you dont use Unity though

there is also 
```
sudo add-apt-repository ppa:lorenzo-carbonell/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```which i highly recommend, however, again, might not work since you have a trackpad

all these were from [http://ubuntuforums.org/showthread.php?t=1592273](http://ubuntuforums.org/showthread.php?t=1592273)
also have a look at [http://ubuntuforums.org/showthread.php?t=1310844&page=2](http://ubuntuforums.org/showthread.php?t=1310844&page=2) there is a complete guide here

---

### Post by Number3124 on 2011-08-23
Thanks. The "xinput" code worked.

---

### Post by Number3124 on 2011-08-23
Actually the xinput code does not save so every time I reboot or going into sleep mode I have to reenter it.

---

### Post by llamabr on 2011-08-23
Try adding it to your .bashrc or .bash_profile

Those load every time you start bash.

---

### Post by Number3124 on 2011-08-23
> **llamabr said:**
> Try adding it to your .bashrc or .bash_profile

Those load every time you start bash.

Okay... how do you do that. I'm a bit of a newbi.

---

### Post by jfed on 2011-08-24
Alternatively there is a panel applet called "lock mouse" in which you click on and it locks the mouse, I'm not sure if this applies to only trackpads or not, but its worth a shot no?

Also, look at your F# keys, some computers (like my own laptop for example) have different hard ware options as their functions. For example my F7 function is to disable/enable my trackpad. Look on your F# keys and see if there is something written in blue on it, obviously other than F#. Look for one with a cursor or something and then press Function (FN) then the F# key.

Thats all assuming you have the button lol.

---

### Post by Number3124 on 2011-08-24
> **jfed said:**
> Alternatively there is a panel applet called "lock mouse" in which you click on and it locks the mouse, I'm not sure if this applies to only trackpads or not, but its worth a shot no?

Also, look at your F# keys, some computers (like my own laptop for example) have different hard ware options as their functions. For example my F7 function is to disable/enable my trackpad. Look on your F# keys and see if there is something written in blue on it, obviously other than F#. Look for one with a cursor or something and then press Function (FN) then the F# key.

Thats all assuming you have the button lol.

That actually. Worked. I don't know why I hadn't thought of that before. Thanks. That's a lot easier than remembering that xinput code.

---

