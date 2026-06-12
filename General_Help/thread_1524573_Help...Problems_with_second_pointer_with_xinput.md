---
title: "Help...Problems with second pointer with xinput"
date: 2010-07-05
forum: General Help
---

### Post by smokyink on 2010-07-05
As the title says I have problems after defining a second mouse pointer.   here is how it all looks like : 

```

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; LITEON Technology USB Multimedia Keyboard    id=12    [slave  keyboard (3)]
&#9121; new pointer                                 id=15    [master pointer  (16)]
&#9116;   &#8627; Logitech G9 Laser Mouse                     id=8    [slave  pointer  (15)]
&#9116;   &#8627; Logitech G9 Laser Mouse                     id=9    [slave  pointer  (15)]
&#9116;   &#8627; Microsoft Natural® Ergonomic Keyboard 4000    id=11    [slave  pointer  (15)]
&#9116;   &#8627; new XTEST pointer                           id=17    [slave  pointer  (15)]
&#9123; new keyboard                                id=16    [master keyboard (15)]
    &#8627; Microsoft Natural® Ergonomic Keyboard 4000    id=10    [slave  keyboard (16)]
    &#8627; new XTEST keyboard                          id=18    [slave  keyboard (16)]


```So one person uses the 1st set and another (in this case I ) use the "new" set of keyboard and mouse..

I have 2 separate X sessions running (the nvidia option)

The problems :

-my mouse leaves a trail on the second screen
-my mouse scroll does not work when another person uses the other set and has focused another window
-numerous menus loose focus and I have to use the keyboard to pick my choise...
-custom keyboard shortcuts do not work.. (for ex. I have set up to close window with Alt + q
and it does not work... Alt + t = terminal and it doesn't work..) 

Does anyone have a solution to any of these ? Please help :)

---

### Post by smokyink on 2010-07-07
bump ?

---

