---
title: "VLC, Synaptic not working after update"
date: 2011-10-15
forum: General Help
---

### Post by jake.anq on 2011-10-15
Hi

I just installed 11.10, and I have found that neither VLC or Synaptic package manager are working as expected.  VLC crashes when opening the 'effects and filters' window, and Synaptic will not open at all.

When opened from terminal, VLC produces this:
```
VLC media player 1.1.11 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")

(process:2799): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to rand()
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-k1ioRxa4Vw,guid=53d9ec6b944823f0d97282020000001f" 
Registered DEC:  true 
Blocked: call to setlocale(6, "")
Invalid parent:  0x216f430 QVLCApp(0x7f0b4f6d5d10, name = "vlc") 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
not the same:  QObject(0x0)  QWidget(0x23ae910, name = "qt_scrollarea_viewport")  at path:  "/org/a11y/atspi/accessible/37415184/2" 
Requesting child objects for an interface that is a virtual child itself. 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Warning: call to rand()
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x2608120) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x2552080) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x25848b0) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x2502ed0) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x263b500) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x262abf0) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x2589800) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x2549070) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x252b090) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x260d420) QVariant(int, 200) 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x2607540, name = "preampSlider") QVariant(int, 320) 
Requesting child objects for an interface that is a virtual child itself. 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x2666e90) QVariant(int, 2) 
Creating accessible with different object than the original interface! 
Value changed:  QSlider(0x26645b0) QVariant(int, 2) 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
ASSERT: "interface->valueInterface()" in file accessible.cpp, line 280
Aborted

```and Synaptic produces this:
```
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check

```Both programs work fine under KDE and before I updated to 11.10.  They fail under Gnome 3 and Unity.


Thanks for any help.

Edit:

The game Hedgewars also fails with a similar error:
```

Note: Miscellaneous irrelevant text removed here
Invalid parent:  0x4210510 QToolBox(0x133c050) 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x133c050) 1 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x133c050) 2 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x133c050) 3 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x133c050) 4 
ASSERT: "interface->childCount() == children.count()" in file adaptor.cpp, line 200
Aborted

```

---

### Post by damalix92 on 2011-10-16
I've got the same problem here after upgrading from 11.04 to 11.10, any help will appreciated.
I tried to reinstall synaptic using apt-get, but this gave no result. needed to go through command line since I did not found the "reinstall" option in the new "software centre"...

---

### Post by jrtomps on 2011-10-17
I also get this error in 11.10, however, I see it in any application written by me using Qt 4.7. The same code didn't produce any issues in past versions.

---

### Post by skiloop on 2011-10-22
I got the same problem after I upgraded to 11.10 from 11.04. But QTCreator works well when i use standard acount while fails when administrator. The same happen with kdevelop.

---

### Post by ChrisGagnon on 2011-10-31
Try disabling accessibility and then launching the program from the commandline. 

Example:
export QT_ACCESSIBILITY=0 && vlc

---

### Post by trellisjr on 2011-11-26
> **ChrisGagnon said:**
> Try disabling accessibility and then launching the program from the commandline. 

Example:
export QT_ACCESSIBILITY=0 && vlc

 Haha this problem was driving me nuts, but this worked for me :)  Ta very much

---

### Post by NeoReaper on 2011-11-30
is there a way to make this a global change so i dont have to type this command before any application using QT?

---

