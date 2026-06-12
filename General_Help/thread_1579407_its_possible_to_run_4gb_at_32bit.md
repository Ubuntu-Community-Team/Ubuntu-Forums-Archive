---
title: "its possible to run 4gb at 32bit?"
date: 2010-09-21
forum: General Help
---

### Post by coco592 on 2010-09-21
how can i run 4gb? because i got to ram 2gb each and its only running with 1.9gb what should i do to get both running with 32bits

---

### Post by Mr_VeRiTy on 2010-09-21
You could try pae mode, just install the pae kernels in synaptic, but I'm not sure they would increase your performance much. 

Open synaptic and install
```
linux-image-(kernel version)-generic-pae
```
Note: you need to restart for changes to take affect.

---

### Post by coco592 on 2010-09-21
im a noobie how that code works?

---

### Post by Mr_VeRiTy on 2010-09-21
> **coco592 said:**
> im a noobie how that code works?
Got to system (at the top of screen) then administration then click on synaptic package manager. Once it asks for your password put it in. then once synaptic loads up, click the search bar at the top, type "pae" there should be some results similar to "linux-image-(number)-generic-pae" but where i've written "(number)" there will be a number like "2.6.32-24" when you see that result right click it and click mark for installation. Then click on "mark" if it asks you to mark any other packages. Then click apply (at the top) and then install the packages.

If you are still unclear about anything just say what you are unclear about and i'll explain it my best.

---

### Post by coco592 on 2010-09-21
just installed 2 pae going to restart and see if its works

---

### Post by coco592 on 2010-09-21
nothings happends still 1.9gb

---

### Post by coco592 on 2010-09-21
its have the last version but still :\ check the picture

---

### Post by Mr_VeRiTy on 2010-09-21
> **coco592 said:**
> nothings happends still 1.9gb
Are you sure the other RAM module is fitted correctly? If it is in correctly then maybe the RAM is popped (that's when it has taken damage due to static) to test if all your RAM is working hold "shift" at bootup until you see the grub menu (that's the menu that lets you choose between kernels) at the bottom of the grub menu, there should be something similar to "memtest" select it and press enter to boot it it will test your memory.

EDIT: after looking at the screenshot, it looks like you haven't installed the pae kernels correctly, if you had it would say "kernel linux 2.6.32-24-generic-pae" (or similar) instead of "kernel linux 2.6.32-24-generic"

Could you tell me the steps you took to install the pae kernels?

---

### Post by coco592 on 2010-09-21
**** buddy after testing ram second time i came out with a 2gb ram died and computer died too i think was becausw to many forces whut down pressing power button :/ every lights go on but screen do nothing :( **** now i got no computer

---

### Post by Mr_VeRiTy on 2010-09-21
Memtest shouldn't do that, it just tests your memory to see if it works right, what exactly happened?

---

### Post by coco592 on 2010-09-21
ok whats going on is that she turn on but black screen then beeps 4 times and power button flash :( same as my other laptop (toshiba) im so screwed up cause i ***** up my laptop first and now this HP of my cousin omfg

---

### Post by Mr_VeRiTy on 2010-09-21
> **coco592 said:**
> ok whats going on is that she turn on but black screen then beeps 4 times and power button flash :( same as my other laptop (toshiba) im so screwed up cause i ***** up my laptop first and now this HP of my cousin omfg
Is this a laptop or a desktop that you are having this problem with?

---

### Post by coco592 on 2010-09-21
laptop :( i was swapin ram to check if they where damage and shutting the laptop of forced

---

### Post by Mr_VeRiTy on 2010-09-21
> **coco592 said:**
> laptop :( i was swapin ram to check if they where damage and shutting the laptop of forced
Do you mean that you took the ram out and put it into another machine to test it? And if you did, Did you make sure not to touch the black parts of the ram with your fingers?

---

### Post by coco592 on 2010-09-21
yes i touched the chips :(

---

### Post by Mr_VeRiTy on 2010-09-21
> **coco592 said:**
> yes i touched the chips :(

You *might* have "Popped" them, popping ram is where static electricity (from fingers or clothes) fries the ram chips, this would only have happened if you touched the black chips on the RAM module, as far as I know this cannot be reversed.

Sorry but you may have to buy some new RAM, luckily RAM is the cheapest part of a computer, To find out what type of ram you'll need to buy (size, model, ect) look at the label on the RAM it should say somehing like "DDR3" or something similar, just google the model of the ram and order a replacement RAM, this can cost as little as £15GBP depending on your model.

---

### Post by PRC09 on 2010-09-21
If you can,remove the battery and power cords from each machine.Then put the ram back in the machines that they came from.Then re-install the batteries and the power cords in each machine and then try a reboot.Sometimes the ram doesnt match the machine either by the amount (to much for the slot) or in the case of older machine the speed. Give that a try.......

---

### Post by techunit on 2010-09-22
The simple answer is no. There is no reasonable way for a new user to get much more performance out of there machine. Nor should you care. 3gbs is alot in Ubuntu at this time and you should really be fine. Now as for your problem. I have been there where everyone says I am wrong about what I think happened, but they are almost always right. It isn't mem test. Did you do anything else, try anything that you didn't mention? One thing you may have to do is reseat the ram. I find it highly unlikely that your ram went bad. I think that it may have gotten loosened or you did something in the BIOS because you thought that would let you get more power. In any case we need to know everything you have tryed.

---

### Post by coco592 on 2010-10-11
got both laptop running... problem was ram were not completely inserted... lol how noob thats sound?

---

### Post by AldenIsZen on 2010-10-11
Everyone has done this at least once I would say... if they have ever inserted ram, unless they have only done it a few times and/or were very lucky to have someone who knows how easy it is to happen.

---

