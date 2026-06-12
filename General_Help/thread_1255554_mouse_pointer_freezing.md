---
title: "mouse pointer freezing"
date: 2009-09-01
forum: General Help
---

### Post by 1bumnote on 2009-09-01
i recently installed ubuntu via wubi after years of deliberating over trying the 'un-userfriendly' linux. wubi seemed to give me some insurance against installing a new os and it going belly up and me being left up **** creek.
my usb mouse will freeze sporadically with no rhyme or reason. the only way to remedy the situation is to reboot the pc. trawling through many forums suggests many people have experienced this problem but they dont seem to bring up any concrete answer to the problem. some forums suggest using a ps/2 mouse but i dont have those ports on this pc. 

system - dell dimension dime521, amd athlon 64 x2 dual core 3800 2ghz, 1 gig ram, nvidia geforce 7300 LE.

---

### Post by 1bumnote on 2009-09-03
bump! any help would really be appreciated.

---

### Post by P4man on 2009-09-03
is it just the mouse pointer freezing, or the entire system?

---

### Post by 1bumnote on 2009-09-03
its just the pointer, but the only way to remedy is a reboot. well, the only remedy a noob like me can do :p

---

### Post by P4man on 2009-09-03
seems a few ppl are being plagued by this. Strange..

When your mouse freezes, try this. press Alt+F2 to get the run application window, then type:

```
gnome-terminal
```

In the terminal type:

```
sudo rmmod usbhid
```

to unload the USB driver, then:

```
sudo modprobe usbhid
```

to reload. Actually, im not sure if unloading it will also render your (USB?) keyboard disfunctional, perhaps you should combine them in one command. Not entire sure about this, but give it a shot if you got a USB keyboard:

```
sudo modprobe usbhid & sudo modprobe usbhid
```

---

### Post by 1bumnote on 2009-09-03
sorry, to combine the two shouldnt it be

sudo rmmod usbhid & sudo modprobe usbhid

not

sudo modprobe usbhid & sudo modprobe usbhid

?

thanks for the help by the way, much appreciated

---

### Post by P4man on 2009-09-03
yes of course, you're right. I made a typo there.
Im not sure about the "&" though, I often see two "&&" used, and Im honestly clueless about bash. maybe someone else can chime in here. But I tried that command and it seemed to work here.

If you dont have an USB keyboard, then just use both commands separately :)

---

### Post by 1bumnote on 2009-09-03
sadly i do have a usb keyboard. those commands didnt help in the slightest im sorry to say. thanks for the suggestion though :)
im a bit miffed, i really wanted this foray into the world of linux to work. seems im going to have to stick with microsoft and XP

---

### Post by 1bumnote on 2009-09-04
there seems more to this than just the mouse problem. i thought sod it, i'll carry on using just the keyboard once the mouse inevitably gives up. after a while of just using the keyboard the keyboard gives up too. only way to reboot then is via the power button. any suggestions? the usb devices giving up is sporadic, doesnt even seem to occur if a certain app is opened or a certain task is performed. can happen 2 seconds from logging or 45.

---

### Post by P4man on 2009-09-04
can you check your logfiles for messages that could relate to this ?
System > administration > log file viewer

---

