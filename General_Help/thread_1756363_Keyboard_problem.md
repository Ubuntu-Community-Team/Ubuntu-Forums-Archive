---
title: "Keyboard problem"
date: 2011-05-12
forum: General Help
---

### Post by bach on 2011-05-12
I am running Ubuntu 11.04 on a DELL Latitude E6510 (bios A07). 

I am experiencing an annoying problem: It has this weird keyboard issue where whenever I am typing in an application, the cursor will jump up and over a few lines. 

The problem also happened under Ubuntu 10.04 and 10.10 and under bios A03. 

Tips are welcome. Thanks.

---

### Post by grahammechanical on 2011-05-12
Does this happen when you are using the Number pad/Keypad? If so go to System Settings> Keyboard>Mouse Keys tab and make sure that there is not a tick mark against the box labeled Pointer can be controlled using the keypad.

On my system this box was somehow getting ticked and causing an issue like the one that you describe.

Regards.

---

### Post by bach on 2011-05-12
That happens when I typing (in OpenOffice, gedit, etc.). The cursor suddenly jumps a few lines up. It's quite annoying. It happens both with and without an external mouse. I am sure I am not touching the touchpad while typing. The option "Pointer can be controlled using the keypad" (in keyboard preferences) is unmarked. 

Tips are greatly appreciated.

---

### Post by bach on 2011-05-12
I included 

syndaemon -i 3 -d -t -k

in

System -> Preferences -> Sessions -> Startup Programs

but it did not help. Under Ubuntu 10.04 I ran TouchFreeze, but it did not help either.

---

### Post by bach on 2011-05-18
A correction: the cursor also jumps down a few lines.

---

### Post by bach on 2011-05-26
I don't get any output in response to these two commands:


cribari@darwin:~$ dmesg|grep -i touchpad
cribari@darwin:~$ grep -i touchpad /var/log/Xorg.0.log
cribari@darwin:~$

I also don't have a touchpad tab in the mouse preferences settings panel.

---

### Post by bach on 2011-05-26
More info: 


cribari@darwin:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_3M             	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]

---

