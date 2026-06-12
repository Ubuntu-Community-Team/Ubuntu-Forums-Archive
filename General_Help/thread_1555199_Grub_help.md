---
title: "Grub help"
date: 2010-08-17
forum: General Help
---

### Post by kertez on 2010-08-17
I have just installed  ubuntu 10.04 and windows 7, with grub. I would like to boot faster, is it possible to make grub auto choose ubuntu, without a timer, but keep an option to press a key on start up to activate a selection of ubuntu or windows.

Does this make sense?

---

### Post by NiGhtMarEs0nWax on 2010-08-17
> **kertez said:**
> I have just installed  ubuntu 10.04 and windows 7, with grub. I would like to boot faster, is it possible to make grub auto choose ubuntu, without a timer, but keep an option to press a key on start up to activate a selection of ubuntu or windows.

Does this make sense?


```
sudo gedit /boot/grub/grub.cfg

```
```

timeout=3
hiddenmenu
```


add 'hiddenmenu' just below 'timeout', press the Esc key to view it within the 3 second window. this works for older version of grub, i am not sure about the release that is shipped with lucid. should work though.

other versions of the grub config are called grub.conf or menu.lst (can't remember) stored in the same place; /boot/grub.

---

