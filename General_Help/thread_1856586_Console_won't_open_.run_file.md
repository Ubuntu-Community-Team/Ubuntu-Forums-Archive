---
title: "Console won't open .run file"
date: 2011-10-08
forum: General Help
---

### Post by funildodeus on 2011-10-08
Trying to install Nvidia drivers and can't get the console to open it either by putting in sh ./filename (it gives me an error: "can't open 'filename') or by double clicking it in the file browser and trying to open from console there (it says it won't run without being in root, despite me logging on as such on a separate console window).

I'm running 10.04 LTS

Any help would be appreciated, as Google has given me nothing

Edit: Just to make this easier, yes, I did make the file executable.

---

### Post by speedwlk on 2011-10-08
Just to clarify : did you try 'sudo sh filename.run' or 'sudo ./filename.run' in the terminal?

---

### Post by WasMeHere on 2011-10-08
Did you try
```
sudo sh ./filename
```
from a terminal window and in the same directory as 'filename'?

By the way, if it is a graphics driver, have you tried the nvidia driver that comes with the repositories. You can select that one via
System -- Administration -- Proprietary Hardware Drivers (or something similar (I'm on a machine with non-English language)).

Good luck
Olle

---

### Post by funildodeus on 2011-10-08
> **Olle Wiklund said:**
> Did you try
```
sudo sh ./filename
```
from a terminal window and in the same directory as 'filename'?

By the way, if it is a graphics driver, have you tried the nvidia driver that comes with the repositories. You can select that one via
System -- Administration -- Proprietary Hardware Drivers (or something similar (I'm on a machine with non-English language)).

Good luck
Olle

Yeah, I'm in the directory I have the file saved in.

For some reason, there are no proprietary drivers for this graphics card (GT440), which is confusing to me, as my old one (Geforce 8900) always did.

---

### Post by WasMeHere on 2011-10-08
I have a GT 430 card, which runs out of the box, and after a couple of minutes the system suggests the built in proprietary driver.

- But I run it with Ubuntu Studio 11.04. Maybe lucid is too old to support it. *Try running 11.04 live*!

- Have you looked at the file you try to run?
'less filename'
Is there any readme file that might explain what to do? Can you check if the file 'filename' itself is not found or if it runs partially and then cannot find some (other) file?

- Let's call for help from someone with experience of GT 440.

Have fun
Olle

---

### Post by funildodeus on 2011-10-08
Alright, I'm an idiot for a lot of different reasons on this one.  For one, can't install graphics drivers with the X server open.

I'm still highly shocked there weren't proprietary drivers, though, seems like something that should have been there on the LTS.

Oh well, thanks for trying to help me, I'm just an idiot and beyond help until I bang my head into the right spot.

---

### Post by WasMeHere on 2011-10-08
We are many people around, that are happy to help with questions and answers, so that you will be able to solve your problem.

Have fun
Olle

---

