---
title: "help!!! automatic right clicking!!! and windows disappear when minimized!!!"
date: 2010-01-30
forum: General Help
---

### Post by smartsmokey on 2010-01-30
i don't know what happened, I was doing the ctrl+alt+fn thing to pan around my desktops, and i think i somehow assigned the mouse to automatically right click on its own whenever i move it or anything. This is really messed up. It's like a virus. Just writing this the right click window has come up about 20 times and there's now a dozen new folders on my desktop. How do I fix this? How do I go into controls and stuff? Thanks in advance

---

### Post by smartsmokey on 2010-01-30
it's still doing it...;t understand what it is

---

### Post by smartsmokey on 2010-01-30
killing me here

---

### Post by warfacegod on 2010-01-30
Sounds like you've got something in Assistive Technologies enabled.

---

### Post by smartsmokey on 2010-02-01
assistive technologies...that's something with the fn key right? Like perhaps I hit fn and right clicked or something and now it does it all the time on its own? this is weird. I'll keep you posted

---

### Post by warfacegod on 2010-02-01
System> Prefs.> Assistive Technologies> uncheck enable assistive...> click Keyboard Accessabilty> uncheck everything.

---

### Post by smartsmokey on 2010-02-04
"warfacegod" - apologies for the delay. It seems that if I keep "keyboard preferences" open (system>preferences>keyboard preferences), the bug stops...it no longer automatically right clicks whenever the mouse becomes stationary. 
Really weird man. I think it's a virus. Think?

---

### Post by warfacegod on 2010-02-04
The likely hood of a virus is extrardinarily remote. I would use your install disc to go into the Live environment (Try Ubuntu without making changes). Install ClamAV:

```
sudo apt-get install clamav
```

Update it and tell it to scan your entire filesystem. If you can't update it, open it in a Terminal with:

```
gksudo clamav
```

---

### Post by smartsmokey on 2010-04-05
Okay this has just blown up...it seems it must be in the computer's manufacturer BIOS, because I have disabled/enabled just about everything that has to do with the mouse or keyboard. With nobody at the computer, the mouse right clicks on anything and everything - it opens new folders one after the other, when trying to click something in the task ar like system>, it will fight me - I will be trying to click on something, and the mouse is just fluttering away and before you know it I'm using 75% of my resources and there's 100 new folders, stuff deleted from the menu, etc . Assistive technogirs is turned off. Mouse properties look good as well. I just booted the live environment - and boom, automatic right-clicking while booted in live cd. What the heck is going on??  The computer is not usable, obviously. Imnow using my iPhone for everything Internet. This could be the single most crappy thing that has ever happened to me computer-wise

---

### Post by smartsmokey on 2010-04-05
Please anyone, if you can help me...please!!! I'm in Ubuntu purgatory

---

### Post by mechro on 2010-04-05
Sounds like a hardware fault... change your mouse?

---

### Post by smartsmokey on 2010-04-06
Yeah I've tried without the USB mouse, disabling and adjusting things in assistive technologies, keyboard, and mouse, and I can't fix it. It DID first show up with Windows install in virtualbox - maybe it worked it's way into linux...I ran that clam app..it found something once but like froze, and things have been downhill from there

---

### Post by mechro on 2010-04-06
Forget the concern over a virus. I doubt that's the cause.

Have you tried running the LiveCD without a mouse plugged in? Does it still do it then?

If it's also doing it from a LiveCD then that still suggests a hardware fault. It could be hard drive, motherboard, memory etc. If you've got spares you could try swapping stuff to try and pin it down.

---

### Post by conradin on 2010-04-06
Sounds like 2 issues to me, a mouse issue, and a panel issue. 
how to verify this would be to open an program, and note its operation with the ps -e command. then, minimize the program where it "disappears". Then see if the process is still running.  if it is still running try:
```


sudo apt-get install gnome-panel


```
or if you have kde, what ever it is. 

the right clicking, might be a left handed set up thing, some mice have a switch for that in them someplace, but there is software that changes mouse properties too. How ever, it may also be a faulty mouse.

---

### Post by smartsmokey on 2010-04-06
I'm going to try livecd boot without the mouse in 2 minutes. I will also try the ps-e thing..i'll google that. I THINK this had something to do with compiz fusion cube thing...you hit ctrl+alt and left or right to change desktops - and I think perhaps I inadvertantly hit the fn key or something and assigned some random/conflicting duties or behaviors to the mouse? I also don't see how to disable the thinkpad's trackpoint eraser thing. That could also be the culprit? I'll report back momentarily

---

### Post by smartsmokey on 2010-04-06
Okay I booted intothe live environment without the mouse connected and the automatic clicking is still horrible - i already have about 50 copies of terminal open. Can't even type. I tried ps -e command in terminal, got it in there by typing one letter and moving the mouse and typing another before it automatically clicked open more terminal windows.

---

### Post by smartsmokey on 2010-04-06
Alright succesfuly entered "ps -e" in terminal, gives me list of processes or programs? What should I look for? Man I need a beer

---

### Post by smartsmokey on 2010-04-06
How do I manipulate or use the data ps -e gives me in terminal?

---

### Post by mechro on 2010-04-07
Please note that when you run a LiveCD environment it's completely separate from your Ubuntu installation; it's a self-contained operating system and knows nothing about any Compiz you have enabled in your Ubuntu installation. Also if you did happen to have a virus it wouldn't affect the LivecD environment. So if you have the same problems in the LiveCD and the Ubuntu installation it points to a hardware problem... for example if you've got a bad solder joint on your motherboard, Ubuntu can't fix it and you need a soldering iron.

Can you disable the thinkpad trackpoint in the BIOS? If you know nothing about your BIOS you'll need a manual or give us some more information about your computer.

---

### Post by mechro on 2010-04-07
> **smartsmokey said:**
> Okay I booted intothe live environment without the mouse connected...
...typing one letter and moving the mouse...

Eh??  :?

---

