---
title: "Huge screen resolution"
date: 2010-07-11
forum: General Help
---

### Post by billyss on 2010-07-11
Hello, I need your help with my laptop. I just installed Lubuntu, everything's ok exept one problem: When I open my pc, the logon screen is set to 1600x1200, while native resolution is 1024x768. Even if I change the setting from Monitor settings, after restart it is the same huge screensize again. 

It's not comfortable to continiusly change the monitor settings... Is there any setting to set 1024x768 as default resolution??

---

### Post by Seeked on 2010-07-11
Check out this thread.  Looks like this has been discussed.

[http://ubuntuforums.org/showthread.php?p=129379#post129379](http://ubuntuforums.org/showthread.php?p=129379#post129379)

---

### Post by realzippy on 2010-07-11
Wait a moment,before editing xorg.conf file,open
nautilus and search for a file "monitors.xml" and **delete** this file **if** exists,then reboot.(Or log out/in)...
(file is in /home/yourusername/.config)
Then set resolution to desired and hope ..   ;-)

---

### Post by kerry_s on 2010-07-11
> **realzippy said:**
> Wait a moment,before editing xorg.conf file,open
nautilus and search for a file "monitors.xml" and **delete** this file **if** exists,then reboot.(Or log out/in)...
(file is in /home/yourusername/.config)
Then set resolution to desired and hope ..   ;-)

you must of missed the lubuntu part. ;)

nautilus = pcmanfm
to show hidden folders/files, press ctrl+h

not sure if that files there in lubuntu though.

---

### Post by realzippy on 2010-07-11
Okay,missed the "L".

Easy way (should work even on [COLOR="Lime"]L[/COLOR]ubuntu)

```
rm ~/.config/monitors.xml
```

and restart X or reboot.

---

### Post by billyss on 2010-07-11
Thank you, but none of *monitors.xml* or *xorg.conf* seem to exist; Terminal reports:
```
rm: cannot remove `/home/billyss/.config/monitors.xml': No such file or directory
```
I guess it's the result of a bad installation? (Sometimes I think it didn't go well after 95%.)

---

### Post by billyss on 2010-07-11
Is there any other way to set 1024x768 as default resolution? My lubuntu boots in 1600x1200 at the moment and I have to set it up every time. I can't find any help in google... :(

---

### Post by billyss on 2010-07-11
You have my thanks cavalier911!! It did the trick:D:D

---

### Post by dodle on 2010-08-02
Just so everyone can find it, billy is referring to this thread: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9624598](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9624598)

---

