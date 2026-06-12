---
title: "left-handed mouse configuration in xubuntu 10.10?"
date: 2012-03-03
forum: General Help
---

### Post by joeyjoejoejunior on 2012-03-03
I have a usb flash drive with a persistent xubuntu 10.10 installed on it.  Some of the computers (laptops/netbooks) the OS is used on have unreliable left-click buttons and are best used with the left and right mouse button outputs switched.  Some of the computers the OS is used on have no mouse problems and do not need their mouse buttons switched.
I've found a few tutorials that help in switching the mouse configuration, though these tutorials are not practical solutions for me as they all seem quite time-consuming and I'd need to switch the configuration daily.
Is there a simpler way?  A configuration editor application perhaps?

Thank you.

---

### Post by TeoBigusGeekus on 2012-03-04
Open a terminal and give
```
xinput list
```
In my case it's
```
$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; ov519                                     id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=9    [slave  keyboard (3)]
```
My mouse is recognised as id=10. So, as I'm left handed, I've put this line in my startup script
```
xinput set-button-map 10 3 2 1 4 5 &
```

---

