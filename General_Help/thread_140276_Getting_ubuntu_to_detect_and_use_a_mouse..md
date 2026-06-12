---
title: "Getting ubuntu to detect and use a mouse."
date: 2006-03-05
forum: General Help
---

### Post by thomas505 on 2006-03-05
Hi i've installed breezy onto a celeron 466 and all has gone well exept when i log on with a mouse (that i know to work as on the exact same computer with windows is usable) i have no movement. I have read that i need to open terminal and type sudo modconf to setup the mouse. Is this right. Another thing is i need to know how to move around and open terminal without mouse use.:twisted: 

Any help would be appreciated.

---

### Post by IYY on 2006-03-05
It depends on which mouse it is (PS/2, Serial, USB). To go to pure command-line mode, Ctrl+Alt+F1.

---

### Post by thomas505 on 2006-03-06
It's a serial mouse.  Modconf doesn't help. Can anyone tell me what command to type after pressing ctrl+alt+F1 to setup the mouse.

---

### Post by IYY on 2006-03-06
I've done this once already... Let me see if I can remember.

I think you'll have to edit /etc/X11/xorg.conf: **sudo nano /etc/X11/xorg.conf**

Under **Section "InputDevice"**, you'll need to change the protocol to **auto** or **microsoft**, and the device to... I think it was **/dev/ttys0**. Then restart the x server by pressing Ctrl+Alt+Backspace. 

I'll check the exact configuration when I get home.

---

### Post by thomas505 on 2006-03-06
Thanks for your help however it didn't work and screwed up xserver. It would be good if you could give me the text i need to change/modify from 'section inputdevice' to 'endsection'. Thanks

---

### Post by IYY on 2006-03-06
Alright, I just checked my computer, and here is what works for me: 

[B]Section "InputDevice"

[INDENT]Identifier "Configured Mouse"
Driver "Mouse"
Option "CorePointer"
Option "Device" "/dev/ttyS0"
Option "Protocol" "Auto"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"[/INDENT]

EndSection[/B]

---

### Post by mr_ed on 2006-03-06
thomas505,

Try the above section that IYY just wrote, except that it should be "CorePointer" instead of "CourePointer"

---

### Post by IYY on 2006-03-06
Oops, typo. \\:D/ 

I'll fix it.

---

### Post by thomas505 on 2006-03-07
That hasn't worked it states:

cannot open device /dev/ttys0
input/output error
configured mouse: cannot open input device
Preinit failed for input device "configured mouse" 
No core pointer.

Any ideas on how to fix this?

---

### Post by IYY on 2006-03-07
First of all, are you sure you typed a capital S in ttyS0? It might make a difference. 

Second, maybe you could try /dev/ttyS1?

---

