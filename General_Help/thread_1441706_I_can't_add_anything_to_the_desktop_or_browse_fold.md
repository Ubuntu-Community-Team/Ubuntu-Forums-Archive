---
title: "I can't add anything to the desktop or browse folders"
date: 2010-03-29
forum: General Help
---

### Post by cerberez on 2010-03-29
I couldn't find anything like this in the forum. I got rid of the UNR launcher (canceled it in startup icons) and showed the desktop. Oddly, I can't put anything on it! I can't put any program launchers on the desktop, nor a trash icon (which i enabled through conf. editor). There's no error message, but nothing happens.

More troublesome, though, is the fact that when I try to open a folder, all I get is the spinning wheel, and, after a minute or so, the wheel disappears.

Am I missing something basic?

Thanks!

---

### Post by darolu on 2010-03-29
For your first problem, this may work: press ALT+F2 and type "gconf-editor"; then navigate to: *apps->nautilus->preferences* and look for "show desktop" and enable it.

About Nautilus not launching, open a terminal (ALT+F2 -> gnome-terminal) and try launching it from there, see if it prints errors:
```
$ nautilus $HOME
```

---

### Post by cerberez on 2010-03-29
thanks for your help! unfortunately neither fix seemed to help.

When trying to open nautilus I got the following message:


> (nautilus:2806): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2806): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2806): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2806): WARNING **: No marshaller for signature of signal 'ShareCreateError'
**
Eel:ERROR:eel-preferences.c:117:preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)
Abortedwhat does that mean? I couldn't find any settings related to initialization or eel in configuration editor... what is "eel?"

Thanks again!

---

### Post by cerberez on 2010-03-29
Huh. so based on this thread: [http://ubuntuforums.org/archive/index.php/t-1363512.html](http://ubuntuforums.org/archive/index.php/t-1363512.html) I tried gksudo nautilus. This successfully opened nautilus (after I input password), but I would rather have quicker access to my files and folders. 

Nautilus still won't launch from the "places" menu, and I still can't put anything on my desktop!

---

### Post by cerberez on 2010-03-30
Any help? 

Also possibly related: I have 9.1, which comes with ubuntu one installed. But I can't open the client. Do you think that's the same nautilus problem?


Regarding my desktop problem: When I try to put a launcher or something on the desktop, I don't get an error message, it just doesn't work. It's not just a displaying-it problem, I think, because nothing shows up under "desktop" as viewed from nautilus, either.

I can create folders in "desktop" through nautilus, though, and they just don't appear on the desktop.

---

