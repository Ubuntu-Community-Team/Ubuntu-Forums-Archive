---
title: "The following plug-in has crashed: /user/lib/plugins/libflashplayer.so"
date: 2010-08-30
forum: General Help
---

### Post by niceguy123 on 2010-08-30
Flash had been working fine in Google Chrome webbrowser but now I am getting this message The following plug-in has crashed: /user/lib/plugins/libflashplayer.so

How can I reinstall the corrupted file?

---

### Post by ajgreeny on 2010-08-30
How did you install flash in the first place, because you could just re-install it the same way, perhaps ```
sudo apt-get install adobe-flashplugin
``` or ```
sudo apt=get install flashplugin-installer
```

It may be worth completely removing it first in case there is a configuration problem, so do a search in synaptic for flash (name only, not name and description) and completely remove whatever you already have installed.

Also check that you don't have either gnash or any of the swfdec packages installed as they can conflict with adobe flash.

---

### Post by DarkStorm_ on 2010-08-30
This is usual if you are running a lot of flash applications in your browser at the same time, but if it happens often it might be corrupted or out-of-date. In that case, do what ajgreeny says.

---

### Post by niceguy123 on 2010-08-31
I seems that reinstalling Flash on Synaptic package manager did the trick. Thank you all for your help.

I take that back. It is still not working.

---

### Post by niceguy123 on 2010-08-31
> **ajgreeny said:**
> How did you install flash in the first place, because you could just re-install it the same way, perhaps ```
sudo apt-get install adobe-flashplugin
``` or ```
sudo apt=get install flashplugin-installer
```


This is what I get:

```
:~$ sudo apt=get install flashplugin-installer
install: missing destination file operand after `flashplugin-installer'
Try `install --help' for more information.

```

---

### Post by ajgreeny on 2010-08-31
Sorry, I didn't notice the typo I put in there!

It should be "sudo **apt-get** install flashplugin-installer", not "apt=get"  not = but -.

My mistake; apologies.

---

### Post by niceguy123 on 2010-09-03
> **ajgreeny said:**
> How did you install flash in the first place, because you could just re-install it the same way, perhaps ```
sudo apt-get install adobe-flashplugin
``` or ```
sudo apt=get install flashplugin-installer
```

It may be worth completely removing it first in case there is a configuration problem, so do a search in synaptic for flash (name only, not name and description) and completely remove whatever you already have installed.

Also check that you don't have either gnash or any of the swfdec packages installed as they can conflict with adobe flash.

OK, This time it actually did work. Completely removed via synaptic all of the swfdec and flash files and then via terminal ran ```
sudo apt-get install adobe-flashplugin
```
And now the flash seems to be working fine on my Chrome browser. I just hope that I didn't remove something I will need for another application. 

Thanks.

---

