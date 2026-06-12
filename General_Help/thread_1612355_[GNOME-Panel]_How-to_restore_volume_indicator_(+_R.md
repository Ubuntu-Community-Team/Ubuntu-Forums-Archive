---
title: "[GNOME-Panel] How-to restore volume indicator (+ Remove Universal Access Preferences)"
date: 2010-11-03
forum: General Help
---

### Post by WG- on 2010-11-03
Hello

About a week ago I removed a program from ubuntu by accident. Which one I can't remember but I'm positive it had something to do with volume/sound. Since that day my volume indicator in the notification area is gone. 

I searched for the internet for a solution to solve this but all the results indicate the same... "add the notification area to your panel". Since this is already the case I don't really know what to do or to solve this. 

Because I still was using 10.04 I thought that maybe upgrading to 10.10 would help. Sadly for me this wasn't the case.

So to clearify what I want to restore:
[img]http://www.imgdumper.nl/uploads3/4cd1199193753/4cd119918ba53-ubuntu10.10overview.png[/img]


Another question for which I want to use this thread for is how do I remove the "Universal Access Preferences" icon from the panel?
[img]http://www.imgdumper.nl/uploads3/4cd119a5d178d/4cd119a5ce0dd-Screenshot-1.png[/img]

---

### Post by Elfy on 2010-11-03
Possibly you removed indicator-sound. Check in synaptic that it is installed - if nto install it.

You might have removed the applet itself - sort of appears to be so - right click the panel - add to panel - Indicator Applet

Not sure about the universal access thing - check sys- preferences - assissitive tech - see if they have been enabled

---

### Post by IIC0RRUPT10NII on 2010-11-03
Thank you! This worked for me!

---

### Post by WG- on 2010-11-03
@forestpiskie

Thank you very much! I indeed removed the sound indicator at synaptic by accident. 

About universal access icon in the panel I checked but nothing was turned on. I also noticted that it was located in the startup programs (wasn't turned on however, but now just removed it from the startup program list). I'm now gonne check if it helped by a reboot. See in a bit.

---

### Post by WG- on 2010-11-03
Ah fixed the universal access icon also. I had enabled a option in the "System->Preferences->Keyboard->Accessibility" tab.

---

