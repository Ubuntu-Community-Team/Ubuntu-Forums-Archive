---
title: "I want a way to remove Flash Drive safely"
date: 2010-01-01
forum: General Help
---

### Post by 0863829 on 2010-01-01
:confused::confused:
I want a way to remove Flash Drive safely in ubuntu   ??
[SIZE=5][/SIZE] 
[SIZE=5][/SIZE] 
[SIZE=5][/SIZE] 
[SIZE=5][/SIZE] 
[SIZE=5][/SIZE] 
((   I want to share the steps in a manner  ))

---

### Post by s.fox on 2010-01-01
Hello, 			 		   		 		 		Right-click the drive and unmount it. That's safely removing it.

-Silver Fox

---

### Post by warfacegod on 2010-01-01
Sorry for jumping in. In my right click menu in 9.10, there are two options; Unmount and Safely Remove Drive. So far as I've been able to tell, they do the same thing. What is the difference? And why have both?

---

### Post by spiky001 on 2010-01-01
unmount  unmounts it from file system, safley remove dose what it sayes

---

### Post by Leppie on 2010-01-01
> **warfacegod said:**
> Sorry for jumping in. In my right click menu in 9.10, there are two options; Unmount and Safely Remove Drive. So far as I've been able to tell, they do the same thing. What is the difference? And why have both?

funny, the safely remove option is not present in thunar, nautilus does have it though (but requires admin rights).

---

### Post by warfacegod on 2010-01-01
> unmount unmounts it from file system, safley remove dose what it sayes
 
I'm sorry, but that's not much of an explanation.

> 
funny, the safely remove option is not present in thunar, nautilus does have it though (but requires admin rights).

I've never needed admin rights to do it, it just does what it does whatever that is.

What is thunar?

---

### Post by Leppie on 2010-01-01
> **warfacegod said:**
> I've never needed admin rights to do it, it just does what it does whatever that is.
ok, the difference is that nautilus is deeply integrated with gnome. i'm using xfce, so nautilus is only an optional. when mount a usb pen with nautilus open, i don't need admin rights to remove safely otherwise i do.

> **warfacegod said:**
> What is thunar?
thunar is another file manager, very similar to nautilus but a lightweight version (so missing some of the goodies as well).

---

### Post by 0863829 on 2010-01-01
How do I get the flash to be directed safely as in Windows go to Start, and then to the computer and then to the flash and press the button and Aloimin out how I want in detail

---

### Post by sgosnell on 2010-01-01
In detail, right-click on the drive and select unmount.  That's it.

---

### Post by todak on 2010-01-01
Right-click on the drive icon. Select **Safely Remove Drive**. Unmounting merely makes the drive inaccessible to the system, but leaves it powered on. Safely removing the drive removes power from the device so that it can be physically removed from the system. See the screenshot for the right-click menu option.

---

### Post by Tumblweed on 2010-01-01
Just curious what damage if any can result in just unplugging the device? in windows and or ubuntu I have never went to safely remove device before unplugging one and have as of yet not had a problem.

---

### Post by bkratz on 2010-01-01
> **Tumblweed said:**
> Just curious what damage if any can result in just unplugging the device? in windows and or ubuntu I have never went to safely remove device before unplugging one and have as of yet not had a problem.



It really only causes you problems if you are actually writing to it at the time you remove it. Better to do it correctly.

---

### Post by todak on 2010-01-01
Safely removing ensures that any information that may be writing to disk (or thumb drive) or any disk activity is completed before powering down, reducing the chance of data corruption. The physical device itself will not be harmed as it is made to be hot-swappable.

---

### Post by pluto4ps on 2010-01-02
Todak is right, simple answer to a simple question, anyone can understand.

---

