---
title: "left+right=middle click also for mouse?"
date: 2009-11-18
forum: General Help
---

### Post by Andreas1 on 2009-11-18
Hi there,

When using the touchpad, you can click the left and the right button at the same time to make a middle click, but when using a mouse, this does not work. I would like this to work also with my mouse (since the middle button is way too hard and loud to click). Is there a way?

---

### Post by Giblet5 on 2009-11-18
You need to add an option to your /etc/X11/xorg.conf:

```
Section "InputDevice"
    Identifier     "MyMouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
**    Option         "Emulate3Buttons" "true"**
EndSection
```

Of course, you may not even have a /etc/X11/xorg.conf file.

To create one, flip to the text console via Ctrl+Alt+F1 and log in.

Enter the following commands:

```
sudo /etc/init.d/gdm stop
sudo X -configure
sudo cp xorg.conf.new /etc/X11/xorg.conf
/etc/init.d/gdm start ; exit
```

You're back to the graphic login. Log in.

Open a terminal window and run ```
sudo gedit /etc/X11/xorg.conf
```

Add that highlighted line to the mouse config. Save the file. Exit gedit. Then run this command in the terminal window:

```
sudo /etc/init.d/gdm restart
```

You're back to the graphic login screen. Log in. Your mouse should now treat left+right as a middle-click.

---

### Post by Andreas1 on 2009-11-18
> **Giblet5 said:**
> You need to add an option to your /etc/X11/xorg.conf:

```
Section "InputDevice"
    Identifier     "MyMouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
**    Option         "Emulate3Buttons" "true"**
EndSection
```

Of course, you may not even have a /etc/X11/xorg.conf file.

To create one, flip to the text console via Ctrl+Alt+F1 and log in.

Enter the following commands:

```
sudo /etc/init.d/gdm stop
sudo X -configure
sudo cp xorg.conf.new /etc/X11/xorg.conf
/etc/init.d/gdm start ; exit
```

You're back to the graphic login. Log in.

Open a terminal window and run ```
sudo gedit /etc/X11/xorg.conf
```

Add that highlighted line to the mouse config. Save the file. Exit gedit. Then run this command in the terminal window:

```
sudo /etc/init.d/gdm restart
```

You're back to the graphic login screen. Log in. Your mouse should now treat left+right as a middle-click.



that was quick. thank you!

---

### Post by Giblet5 on 2009-11-18
Remember, only create a new xorg.conf if you don't already have one...

If you DO have one, edit it via ```
sudo gedit /etc/X11/xorg.conf
```

Add the first code block I posted above and restart the X server via ```
sudo /etc/init.d/gdm restart
```

---

### Post by Andreas1 on 2009-11-23
hey, sorry to bring this up again, when i started this thread i tried the solution in debian, but now i just noticed that the same does *not* work in ubuntu. any ideas?

xorg.conf:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option "Emulate3Buttons" "true" #left+right=middle-click
EndSection

```

---

