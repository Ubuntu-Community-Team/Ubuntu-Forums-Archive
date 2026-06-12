---
title: "monitor turns off automatically"
date: 2012-04-13
forum: General Help
---

### Post by MeriMeri on 2012-04-13
hi there,
im running Lubuntu 11.10 and my problem is that monitor turns off automatically every 10 minutes!

its not screensaver. i think it must be from an option in power management. but there isnt any power management in here.

can anyone help me with this issue?:confused:

---

### Post by ankspo71 on 2012-04-13
This is probably DPMS controlling your monitor's power settings. You can find out by typing this command in the terminal:

```
xset -q
```

> DPMS (Energy Star):
  Standby: 600    Suspend: 0    Off: 900
  DPMS is Enabled
  Monitor is On

If it says DPMS is enabled then that is the cause. To temporarily disable DPMS you can type this command in the terminal:

```
xset -dpms
```

and to re-enable it again you could type:

```
xset +dpms
```

You can also temporarily modify the length of time (measured in seconds) for the monitor's standby, suspend, and power off modes:
```
xset dpms 0 0 7200
```
DPMS needs to be eneabled before it will accept the changes.

More info:
[http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)

To make the changes permanent, you could modify ~/.xinitrc or xorg.conf, but neither exist on my system so for now I am using a script to temporarily disable DPMS for 2 hours (long enough for watching movies)...

Create a file named "disable-screenblanking.sh", then paste the following code into it.
```

#!/bin/sh

xset -dpms
sleep 7200
xset +dpms

```
Then right click on the file, then click properties, then click permissions, then check "make the file executable". Now you can run the script whenever needed.

---

### Post by ankspo71 on 2012-04-13
I just realized that DPMS can be controlled by editing ~/.bashrc too.

To alter the length of time before your monitor changes power-modes, open the hidden file ~/.bashrc in your home directory and add this line to the bottom of it:

```
xset dpms 0 0 7200
```


OR To permanently disable DPMS, open the hidden file ~/.bashrc in your home directory and add this line to the bottom of it:

```
xset -dpms
```

Then save the file and restart your system for the changes to take effect.

---

### Post by MeriMeri on 2012-04-14
thank you very much ankspo71
your script solved the problem.:p

by the way

> 
I just realized that DPMS can be controlled by editing ~/.bashrc too.

To alter the length of time before your monitor changes power-modes, open the hidden file ~/.bashrc in your home directory and add this line to the bottom of it:

```

xset dpms 0 0 7200

```

OR To permanently disable DPMS, open the hidden file ~/.bashrc in your home directory and add this line to the bottom of it:

```

xset -dpms

```
Then save the file and restart your system for the changes to take effect.

it doesnt work! it just disable DPMS. (nothing else)


thank you again.
you helped me soooooooooooooo much
:p

---

