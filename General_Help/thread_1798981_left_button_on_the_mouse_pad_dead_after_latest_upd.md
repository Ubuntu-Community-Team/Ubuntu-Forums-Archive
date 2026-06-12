---
title: "left button on the mouse pad dead after latest update"
date: 2011-07-06
forum: General Help
---

### Post by Noob2011 on 2011-07-06
Hello, 

since the last update (that was yesterday) my trackpad left key has stopped functioning.:(.. i have to use an external mouse for now... :( 

Help me with this pls.

Thanks

Ubuntu 10.04 Lucid
Dell Inspiron Mini netbook. 2 GB RAM, 260GB HDD

---

### Post by enimeizoo on 2011-07-06
Did you try to run xev to see if it still sends an event?
if not, run "xev" in a terminal, a (little white, probably) window will appear. Place your mouse in that window (you will get a bunch of useless output in the terminal at this point), then make sure you are not touching anything and press your button. If no event appears, I don't know what to do. 
You can check what is the normal mouse button event with the mouse you are using. It should look like :
```

ButtonPress event, serial 34, synthetic NO, window 0x6000001,
    root 0xa8, subw 0x0, time 27992907, (51,78), root:(773,101),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x6000001,
    root 0xa8, subw 0x0, time 27992947, (51,78), root:(773,101),
    state 0x110, button 1, same_screen YES

```

---

### Post by Noob2011 on 2011-07-06
Hi,

Thank you very much for your reply.. 

i tried it...  the "Button Press Event"  does not show up when the buttons on the track pad is pressed (left or right).  however all other events are listed when the pointer is moved on the white screen. When i double tap on the track pad i see the " Button Press Event " list on the terminal window... its as if the button is dead... :( 

i used an external usb mouse and all the keys and the tracking is just fine... its only on the track pad that is  messed since the last update.

---

### Post by enimeizoo on 2011-07-07
Your right trackpad button works, but there is no event in xev? 

Did the lastest update change the kernel?

---

### Post by Noob2011 on 2011-07-07
hello enimeizoo

the left button does not seem to work... the last automatic update happened the day before and since then this problem has showed up . 

There was no kernel update as the last update, as it was only a few MBs 

Thanks

---

### Post by Noob2011 on 2011-07-07
Hello enimeizoo, 

sorry for the second post... 

yes the track pad works ... i can move the mouse just fine. and it shows up on xev... but when i click the left and the right buttons , it does not list on xev.. 

however here is a strange thing..... the right button works on the track pad on the desktop,only the left button simply does not do anything.... this is on the desktop and not on xev... 

so in other words only the right button on the track pad seems to work .. the left is dead ... on xev both the buttons dont work / does not register any event on  xev 

sorry for the double post.. 

cheers

---

### Post by enimeizoo on 2011-07-07
I don't think updates change configs, but just in case, did you check the options available in the system settings (or whatever it is called in you desktop environement, it is "system settings > input devices > touchpad" in kde). 
I have various information there, hardware information especially, and some config options. It tells me both right and left buttons are supported. 
Unfortunatly, I don't know how to access synaptics information outside of this. I'm looking for it.

(edit) Well, it is weird that it works on the desktop and not in xev... The only input (keyboard/mouse) I know not sending an event but working fine is th fn key. It actually modify scancodes from the keys you press while it is pressed. So you actually recieve an event, but only when the other button is pressed. Just like that was another physical button on the keyboard.
Well, if the config thing fails, I don't know what to do. Your desktop environment is supposed to use events from the X server. The exact same events you can see in xev. If one is seen by the desktop, but not xev, something strange is going on, and I have no clue what it can be

---

### Post by Noob2011 on 2011-07-07
Hello enimeizoo, 

I rebooted the system 4 times and then it seems to be working... in the mean time i cleared all cache from firefox, booted without usb wireless CDMA modem, booted without my usb addon keyboard and mouse. etc. 4th time lucky.. :)

I am a noob to ubuntu.(over 25 years with dos and windows :() . I got this netbook just for my net needs about 6 months ago, i am very happy with it.. here is the thing.. should i just set my updates to Important security updates and un tick Recommended updates?. I have had few other issues, [http://ubuntuforums.org/showthread.php?t=1798189](http://ubuntuforums.org/showthread.php?t=1798189)   


Thanks for all the help mate. Cheers .

---

### Post by Noob2011 on 2011-07-07
its dead again... :( .. i rebooted and now i dont have my left mouse key... :(

---

### Post by Noob2011 on 2011-07-07
Its back up again, this time no reboot , nothing... it came back on its own, i am really confused now... :( .. LOL

---

