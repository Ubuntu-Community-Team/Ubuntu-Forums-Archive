---
title: "running custom commands at start up"
date: 2010-04-27
forum: General Help
---

### Post by Ceiber Boy on 2010-04-27
Hi

I resently took the rash decision and purchased a web cam without refering to the Ubuntu documentation about which ones work and which ones do not. However i did manage to get it working but i have to start skype from a terminal to make the web cam work, with the command below.

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

Question:
Is it possible to lodge this command in the start up process so that when i click the button on the application menu the web cam will work and not have to start it through a separate shell command line?

Thanks

---

### Post by demuxer on 2010-04-27
yeah, System-- Preferences-- Startup Applications -- Add
there you type i.e. NAME = Load webcam
Command = bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
try it

---

### Post by colorlessprism on 2010-04-27
is it possible to add this to the "startup programs"? i know i have a couple of custom apps started this way

---

### Post by bodhi.zazen on 2010-04-27
You may also edit you may edit you menu , add the syntax to the command to start skype.

You might be able to add the command to .bashrc

[quote]export LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so[/code]

---

### Post by Ceiber Boy on 2010-04-28
> **demuxer said:**
> yeah, System-- Preferences-- Startup Applications -- Add
there you type i.e. NAME = Load webcam
Command = bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
try it
Yep

This dose not work for this of command!

---

### Post by Ceiber Boy on 2010-04-28
[quote]You might be able to add the command to .bashrc

This idea means when i open the terminal skype starts and allows my web cam to work correctly but the terminal then becomes locked into that function and will not allow me to use it for anythink else. Also, i still have to start the terminal and am not able to use the applications menu :-(

---

### Post by demuxer on 2010-04-28
I wonder if you can start skype with another script:
 running that line first 
and then loading skype-bin

in that way, you dont need it as startup, just when skype is started

---

### Post by gadolinio on 2010-04-28
> **demuxer said:**
> I wonder if you can start skype with another script:
 running that line first 
and then loading skype-bin

in that way, you dont need it as startup, just when skype is started

+1 !!
I think it would be better. Create a new empty file, and open it with gedit text editor. Make the file's content something like:
```

#!/bin/bash

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
skype

```

and save it.

Then create a launcher or main menu item that executes the command
```

sh /home/<path to the text file>/<filename>

```

Hope that helps...

---

### Post by Ceiber Boy on 2010-04-30
> **gadolinio said:**
> +1 !!
I think it would be better. Create a new empty file, and open it with gedit text editor. Make the file's content something like:
```

#!/bin/bash

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
skype

```and save it.

Then create a launcher or main menu item that executes the command
```

sh /home/<path to the text file>/<filename>

```Hope that helps...

Brilliant that works perfectly.

Thank you.

---

