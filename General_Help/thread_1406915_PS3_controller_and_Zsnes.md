---
title: "PS3 controller and Zsnes?"
date: 2010-02-14
forum: General Help
---

### Post by jahgamer189x on 2010-02-14
I've installed the PS3 controller on Ubuntu 9.10 via usb. I try to set the input for Zsnes however when I click one of the boxes to change the button, it automatically records R2 as being pressed when in fact it's not. The button is clean and not sticky. Please help!

---

### Post by justcallmecloud on 2010-04-16
I faced this exact same problem and I just solved it with hours of googling. :)

Edit your "~/.zsnes/zinput.cfg" file with the bellow values.

```
; Player 1 Input
; Input Device: 0 = Unplugged, 1 = KEYBOARD/GAMEPAD
pl1contrl=1
; Keys for Select, Start, Up, Down, Left, Right, X, A, L, Y, B, R
pl1selk=310
pl1startk=313
pl1upk=314
pl1downk=316
pl1leftk=317
pl1rightk=315
pl1Xk=322
pl1Ak=323
pl1Lk=320
pl1Yk=325
pl1Bk=324
pl1Rk=321
```

Where I found out this treasure of information.
[http://blog.brokenfunction.com/2009/07/13/zsnes-and-a-sixaxis-controller/](http://blog.brokenfunction.com/2009/07/13/zsnes-and-a-sixaxis-controller/)

---

### Post by genetik on 2010-05-17
Can anyone help in setting up a second PS3 controller to use as player 2 on ZSNES?

---

### Post by pamanes7 on 2011-06-09
hi, 

I was stuck here for a short period of time,

I have Snow Leopard 10.6.7

I am using 2 PS3 Controllers, It was mere luck that i could set them up smoothly, do not know what I did to make it work , i actually installed it a couple of times and my setup file looks like this (zinput.cfg) under zsnes 1.51-3 that i downloaded from  a link i found on another forum 

I HOPE THIS HELPS !!!!!!!



; Player 1 Input
; Input Device: 0 = Unplugged, 1 = KEYBOARD/GAMEPAD
pl1contrl=1
; Keys for Select, Start, Up, Down, Left, Right, X, A, L, Y, B, R
pl1selk=264
pl1startk=267
pl1upk=268
pl1downk=270
pl1leftk=271
pl1rightk=269
pl1Xk=276
pl1Ak=277
pl1Lk=274
pl1Yk=279
pl1Bk=278
pl1Rk=275
; Turbo Keys for A, B, X, Y, L, R
pl1Atk=0
pl1Btk=0
pl1Xtk=0
pl1Ytk=0
pl1Ltk=0
pl1Rtk=0
; Diagonal Keys for Up-Left, Up-Right, Down-Left, Down-Right
pl1ULk=0
pl1URk=0
pl1DLk=0
pl1DRk=0

; Player 2
; Input Device: 0 = UNPLUGGED, 1 = Keyboard/Gamepad
pl2contrl=1
; Keys for Select, Start, Up, Down, Left, Right, X, A, L, Y, B, R
pl2selk=291
pl2startk=294
pl2upk=295
pl2downk=297
pl2leftk=298
pl2rightk=296
pl2Xk=303
pl2Ak=304
pl2Lk=301
pl2Yk=306
pl2Bk=305
pl2Rk=302
; Turbo Keys for A, B, X, Y, L, R
pl2Atk=0
pl2Btk=0
pl2Xtk=0
pl2Ytk=0
pl2Ltk=0
pl2Rtk=0
; Diagonal Keys for Up-Left, Up-Right, Down-Left, Down-Right
pl2ULk=0
pl2URk=0
pl2DLk=0
pl2DRk=0

---

### Post by Diego318 on 2013-04-21
> **justcallmecloud said:**
> i faced this exact same problem and i just solved it with hours of googling. :)

edit your "~/.zsnes/zinput.cfg" file with the bellow values.

```
; player 1 input
; input device: 0 = unplugged, 1 = keyboard/gamepad
pl1contrl=1
; keys for select, start, up, down, left, right, x, a, l, y, b, r
pl1selk=310
pl1startk=313
pl1upk=314
pl1downk=316
pl1leftk=317
pl1rightk=315
pl1xk=322
pl1ak=323
pl1lk=320
pl1yk=325
pl1bk=324
pl1rk=321
```

where i found out this treasure of information.
[http://blog.brokenfunction.com/2009/07/13/zsnes-and-a-sixaxis-controller/](http://blog.brokenfunction.com/2009/07/13/zsnes-and-a-sixaxis-controller/)


you are a god among men

---

### Post by howefield on 2013-04-21
Old thread closed.

---

