---
title: "External monitor"
date: 2010-02-15
forum: General Help
---

### Post by slonnnik on 2010-02-15
Hi
I'm using Ubuntu on my laptop HP Compaq nc8430. I have it also connected to external monitor Belinea b.display 22" wide. Graphic card: Ati Mobiliti Radeon X1600.

Here is my problem. I'm using only external monitor, because laptop is always closed. I managed to display it and work correctly. However, sometimes it happens that when I start laptop from sleep it doesn't work. So far, I have managed somehow to correct it. But not today. I woke up today and it doesn't work. Both monitors are now set up like they are next to each other, so you can drag things form one to another. 

Could you please help me to understand and correct why it keeps changing, why it cannot stay as it is?
How do I make it in a way that I can see everything only on my external monitor.

Thanks

---

### Post by slonnnik on 2010-02-21
Hi

Can somebody help me to set my displays correctly so I can switch between monitors (internal and external) without problems?
Thanks

---

### Post by corncob on 2010-02-21
Is there anything in System > Preferences > Display that would help?

---

### Post by MaxIBoy on 2010-02-21
What graphics drivers are you using? Are you using the default stock drivers, or did you install the ATI closed source ones?

---

### Post by corncob on 2010-02-21
Just what came with Karmic Koala.  I haven't tried installing anything else or plugging in an external monitor.  I just thought I'd point out Preferences > Display in case you didn't get any better answers.

---

### Post by corncob on 2010-02-21
Oops!  I thought the above post was from the original poster and was replying to him.  Sorry.

---

### Post by slonnnik on 2010-03-09
Hi,

There is nothing that would help in Display preferences

I'm using Ubuntu open source driver (ATI)

Is there a script for xorg.conf for laptop and external monitor so the system knows which one to use (extrenal if it is plugged in, laptop otherwise)

Thanks for help

---

### Post by asmoore82 on 2010-03-09
run this command in a terminal and post the output back here:
```
xrandr
```

---

### Post by slonnnik on 2010-03-10
[FONT=monospace]Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 297mm
   1680x1050      60.0*+   59.9  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)
[/FONT]

---

### Post by slonnnik on 2010-03-10
and I don't know why the external monitor is weird today. It keeps going black and turning on again and again.

Any advise?
Thanks

---

