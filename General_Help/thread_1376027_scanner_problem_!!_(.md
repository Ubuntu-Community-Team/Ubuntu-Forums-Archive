---
title: "scanner problem !! :("
date: 2010-01-08
forum: General Help
---

### Post by Amgad elsaiegh on 2010-01-08
my scanner is Benq 5000 ,the default scanning software (xsane) give me the following message whenever i plug the scanner to the pc :
[IMG]http://i48.tinypic.com/33dglew.jpg[/IMG]
what should i do ???

i tried the gnome image scanning software too but it didn't recognize the scanner at all :(

the only software that worked is vuescan but unfortunately it is non-free software !!!!
have you got any clues???

---

### Post by Amgad elsaiegh on 2010-01-09
bump
no one got a clue ??! :(

---

### Post by plucky on 2010-01-09
This [link](http://snapscan.sourceforge.net/) might help.

Post output of terminal commands  ```
scanimage -L
lsusb
```

---

### Post by Amgad elsaiegh on 2010-01-09
this is the output of the first command:
[COLOR="Red"]WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `snapscan:libusb:005:002' is a Acer FlatbedScanner22 flatbed scanner[/COLOR]

& this is the output of the second:
[COLOR="Red"]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 04a5:20f8 Acer Peripherals Inc. (now BenQ Corp.) Benq 5000
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]

the link you gave me , i entered it yesterday but i couldn,t understand that stuff ,it is a little bit complicated terminal commands & i hate it

---

### Post by Amgad elsaiegh on 2010-01-09
no answers yet ?? :(

---

