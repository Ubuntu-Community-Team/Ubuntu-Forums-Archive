---
title: "Hardware issues"
date: 2010-09-09
forum: General Help
---

### Post by Leshinsky on 2010-09-09
ok here is a few issues i am having with ubuntu.  the onboard touch pad mouse does not work anymore.  only a external usb one does, my wifi card is not active at all,  can anyone help with these issues.

---

### Post by s.fox on 2010-09-09
Hello,

Can you open a terminal and run the following command. Please post the output back :)

```
xinput list 
```

I would also have a read of [this]("https://help.ubuntu.com/community/SynapticsTouchpad") community docs page on the touchpad :)

-Silver Fox

---

### Post by Leshinsky on 2010-09-09
Here you go

matthew@ubuntu:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Logitech Logitech USB Headset               id=10    [slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer             id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
matthew@ubuntu:~$

---

### Post by Leshinsky on 2010-09-09
Also my headphones and speakers are not controlled by the Ubuntu sound control does anyone have a idea how to fix this as well as the wifi card.  Thanks.

---

