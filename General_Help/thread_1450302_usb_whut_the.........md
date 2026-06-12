---
title: "usb? whut the........?"
date: 2010-04-08
forum: General Help
---

### Post by cake nom nom on 2010-04-08
hii ive had ubuntu  9.10  for a long while now and i was wondering...

is anyone else having problems with their Usb drives in 9.10 after a recent system-update??

i'll plug in a little flash drive usb and the leds blink & glow like they use to, but the icon doesnt show up on the desktop now

i move it to another usb slot same thing. i plug in my external drive it turns on like normal but doesnt show up

this never happened before :o 

but a few mins ago I had a system update thats the only thing i can think of that might have changed something

1. how could i maybe open the usb drive through the terminal - can someone give me the the command :D
2.how do i undo any updates lol anybody?

i <3 u Ubuntu community 
thanks in advanced for your help!

sincerely,
-nom nom I <3 cake

---

### Post by SnickerSnack on 2010-04-08
I've had a similar problem with some *usb* drives.

I'm in the middle of something right now, but I'll come back in ~30 minutes to give any insight I can.

Zach

---

### Post by cake nom nom on 2010-04-08
kudos\\:D/

---

### Post by cake nom nom on 2010-04-09
31 views & 1 reply?

---

### Post by MooPi on 2010-04-09
```
sudo fdisk -l
```remember what is listed. You will need to use the drive destination in the third command. It should look something like sdg1, or  sdf1
```
sudo mkdir /media/usb1
``````
 sudo mount /dev/sdf1 /media/usb1
```Your usb drive should now be accessible in the /media/usb1 directory.

---

### Post by cake nom nom on 2010-04-09
thanks man they should give you some more beans

---

### Post by SnickerSnack on 2010-04-09
30 minutes turned into hours.  The response you got looks like it is what you needed.

---

