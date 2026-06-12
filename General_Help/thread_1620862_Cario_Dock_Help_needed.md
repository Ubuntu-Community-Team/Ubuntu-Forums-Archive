---
title: "Cario Dock Help needed"
date: 2010-11-13
forum: General Help
---

### Post by joelw135 on 2010-11-13
I have Cario Dock installed on Ubuntu 10.10.  I have chosen a theme in configuration and the icon set I want to use. The icons show just fine until I reboot, then some are no longer visible. The app is still on the dock but missing an icon. I have tried different icon sets same result. How do I get my icons to stay after reboot? Thanks.

---

### Post by Frogs Hair on 2010-11-13
The custom icons that you use must be saved to a folder or they will not reappear on the dock after reboot . If you have done this I'm not sure what the next move would be.

---

### Post by joelw135 on 2010-11-13
> **Frogs Hair said:**
> The custom icons that you use must be saved to a folder or they will not reappear on the dock after reboot . If you have done this I'm not sure what the next move would be.

Can you give me some details as how and where I save them to?

---

### Post by matt_symes on 2010-11-13
Hi

Does this help?

[http://ubuntuforums.org/showthread.php?t=1423974](http://ubuntuforums.org/showthread.php?t=1423974)

Kind regards

---

### Post by joelw135 on 2010-11-13
> **matt_symes said:**
> Hi

Does this help?

[http://ubuntuforums.org/showthread.php?t=1423974](http://ubuntuforums.org/showthread.php?t=1423974)

Kind regards

Not really as the applets loose the icon and there is no option in the applets config to assign a icon.

---

### Post by Frogs Hair on 2010-11-13
> **joelw135 said:**
> Can you give me some details as how and where I save them to?

I created a folder in documents because I use custom icons in AWN and I used to make my own themes for Cairo / GLX Dock . Pick any place you like where you can make a new folder. The icons I found on the web I save to down loads and drag them to my icon folder . I would often download a whole icon set but only 6 to 10 out of the set.

---

### Post by matt_symes on 2010-11-13
Hi 

What about this?

[http://ubuntuforums.org/showthread.php?t=1381931](http://ubuntuforums.org/showthread.php?t=1381931)

Kind regards

---

### Post by joelw135 on 2010-11-13
> **Frogs Hair said:**
> I created a folder in documents because I use custom icons in AWN and I used to make my own themes for Cairo / GLX Dock . Pick any place you like .

The problem is only with the applets loosing the icon and there is no way to direct the applet to my icon folder.

---

### Post by joelw135 on 2010-11-13
> **matt_symes said:**
> Hi 

What about this?

[http://ubuntuforums.org/showthread.php?t=1381931](http://ubuntuforums.org/showthread.php?t=1381931)

Kind regards

Figured out the problem. It seems like Cario dock with open GL was loading at the same time as Cario Dock without open GL. Removed the with open GL and all loads fine now. Thanks for bearing with me.

---

### Post by Frogs Hair on 2010-11-13
> **joelw135 said:**
> The problem is only with the applets loosing the icon and there is no way to direct the applet to my icon folder.

There is a way to customize applets in GLX but I am not using it currently I will have to install it so I can remember. ( Thread Solved before this reply )

---

### Post by joelw135 on 2010-11-13
> **Frogs Hair said:**
> There is a way to customize applets in GLX but I am not using it currently 
I will have to install it so I can remember.

Thanks, I just got it working. Open GL and non open GL were loading at the same time causing the problem. But it would be nice to customize the applets.

---

