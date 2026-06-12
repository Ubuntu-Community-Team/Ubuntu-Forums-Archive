---
title: "Unable to stop gdm/X"
date: 2010-07-27
forum: General Help
---

### Post by letharion on 2010-07-27
I'm need to drop to a terminal without X running to do some Cuda-related work. I need exclusive GPU usage.

When I do

sudo service gdm stop

I get:
Warning: Fake initctl called, doing nothing.
When I do

sudo /etc/init.d/gdm stop

I'm told to use "service gdm stop" instead. Thanks
Recent clean install, so I should have all rights.

Any idea what I could do?

---

### Post by TheStroj on 2010-07-27
How about: 
(that's not really recommended)
```
killall Xorg
```


or using shortcut like Ctrl + Alt + F6 (I think that leaves X running in background then you can try to stop it)

---

### Post by stlsaint on 2010-07-27
Im not to familiar with cuda but if you hit Ctrl+Alt+F1 or F4 that should take you to a ttyl. Now hitting ctrl+alt+f7 (default) should bring you back to your desktop meaning gdm will still be running. You can also boot to restore mode from grub and choose to enter command line.

---

