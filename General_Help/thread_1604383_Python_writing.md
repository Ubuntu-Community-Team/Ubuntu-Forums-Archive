---
title: "Python writing"
date: 2010-10-24
forum: General Help
---

### Post by tomlagrinch on 2010-10-24
Hello!
As usual I'm posting absolute beginner questions.
Every time I want to connect to the internet I have to use the terminal to enter a bunch of commands, I wandered is there a way of writing a python script to execute the commands automatically? Just to speed up the process a bit, the commands are;

[B]sudo ifconfig wlan0 down
sudo modprobe -r rt2800usb
sudo modprobe -r rt2870sta
sudo modprobe rt2870sta
sudo ifconfig wlan0 up[/B]

Is this possible? Any feedback would be appreciated!
Cheers!
Tom

---

### Post by Vaphell on 2010-10-24
you don't need python to do that
just create a shell script from these commands

```

#!/bin/bash

sudo ifconfig wlan0 down
sudo modprobe -r rt2800usb
sudo modprobe -r rt2870sta
sudo modprobe rt2870sta
sudo ifconfig wlan0 up

```

name it as you please, make it executable and run it with sudo
```
chmod +x myscript
sudo ./myscript
```
if you want you can create a launcher and tie the script to it

---

