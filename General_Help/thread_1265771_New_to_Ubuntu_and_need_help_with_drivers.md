---
title: "New to Ubuntu and need help with drivers"
date: 2009-09-13
forum: General Help
---

### Post by lazytitan on 2009-09-13
Need help loading drivers on Ubuntu that i just installed. im new to any OS outside of windows but i cant install any drivers for my laptop. 

Laptop is GT735 MSI and i gone to their site and got it using the cd that came with laptop but both only have windows drivers. dont see any for linix OS so not sure how the hell im suppose to. any help would be good. trying to install all drivers, but mainly just my wirless drivers so i can get going.

---

### Post by synapsys on 2009-09-13
Ubuntu is unlike windows because most of the driver support you need is built into the kernel already. Usually the only drivers you need to install are wireless and graphics drivers. Basically when you install a fresh copy of Ubuntu, whatever doesn't work need some configuring or a driver. 

What else is not working on your laptop besides wireless?

The way to install wireless drivers varies depending on the type of card you have. To determine what type of card you have, open up a terminal:
**(Applications >> Accessories >> Terminal)**

And type:

```
lspci | grep Wireless
```

hit enter.

Paste the results here, so we can help you get your wireless card installed.

---

### Post by gordintoronto on 2009-09-13
> **lazytitan said:**
> Need help loading drivers on Ubuntu that i just installed. im new to any OS outside of windows but i cant install any drivers for my laptop. 

Laptop is GT735 MSI and i gone to their site and got it using the cd that came with laptop but both only have windows drivers. dont see any for linix OS so not sure how the hell im suppose to. any help would be good. trying to install all drivers, but mainly just my wirless drivers so i can get going.

Drivers are normally handled very differently in Linux from what you are used to.  Mostly, they are built-in.  When I put a Dlink DWL-G510 wireless adapter into my computer, "it just worked," I did not install any software of any kind for it.

Oh shucks, I see someone beat me to the punch on giving you instructions.

---

### Post by Bucky Ball on 2009-09-13
Plug in an ethernet cable and get your updates. You may well be offered whatever restricted drivers you need.

Also, System->Admin->Hardware Drivers

Is there a wireless driver in there that is disabled? As mentioned, if your machine is working apart from this then all other drivers you need are present.

When it comes to Ubuntu, Windows driver disks are usually good as coasters to put your drink on while you're learning about your new OS.

---

### Post by lazytitan on 2009-09-13
ok thx guys ill try that right now let u know if it works. only two i know is video and wireless i guess. though i would heve to install others thats good that i dont.

---

### Post by lazytitan on 2009-09-13
> **synapsys said:**
> 

```
lspci | grep Wireless
```hit enter.


well i have little linix usage with what i do at work and i no what grep is and and know that its a pipe symbol your doing their and it found nothing i even went back to root dir to tried grep there and found nothing.


> **Bucky Ball said:**
> Plug in an ethernet cable and get your updates. You may well be offered whatever restricted drivers you need.

Also, System->Admin->Hardware Drivers

Is there a wireless driver in there that is disabled? As mentioned, if your machine is working apart from this then all other drivers you need are present.

When it comes to Ubuntu, Windows driver disks are usually good as coasters to put your drink on while you're learning about your new OS.

i went to hardware drivers and lol there is nothing there at all...so what the hell does that mean? i will try to do ethernet cable here later tonight, cant right now but is there something wrong?

---

### Post by synapsys on 2009-09-14
try just 

```
lspci
```

---

### Post by Bucky Ball on 2009-09-14
> **lazytitan said:**
> i went to hardware drivers and lol there is nothing there at all...so what the hell does that mean? i will try to do ethernet cable here later tonight, cant right now but is there something wrong?

Nope, nothing wrong. Hopefully when you get an ethernet cable in there it will pick up what you need.

---

### Post by P4man on 2009-09-14
a little googling suggests your laptop might have a  "AW-GE780" wireless card, and should work out of the box. Are you sure its not working? there is a little network icon in the top right, if you click it, don't you get a list of access points to connect to? If not, perhaps try turning the wifi on if your computer has a key for it.

If its not working, like others said, run "lspci". To do so, open a terminal (Applications > accessories > terminal) type in "lspci" and copy/paste the result here.

---

### Post by lazytitan on 2009-09-14
lol well i was making that ALOT harder then it should have been thx guys, didnt have to do a damn thing then other then put in my security key to network. lol i didnt know....

---

### Post by synapsys on 2009-09-17
............ I feel dirty ....................

---

### Post by Bucky Ball on 2009-09-18
> **synapsys said:**
> ............ I feel dirty ....................

?

---

