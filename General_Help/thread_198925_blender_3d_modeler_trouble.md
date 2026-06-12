---
title: "blender 3d modeler trouble"
date: 2006-06-17
forum: General Help
---

### Post by killzoneman0 on 2006-06-17
i have installed blender 3d modeler with the add/remove applications.  whenever i try click the icon to run it, it does nothing.  i have uninstalled it and reinstalled it and it still won't work.  how could i get this to work?

---

### Post by Kilz on 2006-06-17
[QUOTE=killzoneman0]i have installed blender 3d modeler with the add/remove applications.  whenever i try click the icon to run it, it does nothing.  how could i get this to work?[/QUOTE]
Do you have a video card with acceleration enabled? Open a terminal and type in glxgears, if a small window opens and you see 3 gears you do. If not you may have to install [a driver for your video card]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards") if its an ATI or nivida one.

---

### Post by killzoneman0 on 2006-06-18
even though i installed the driver, it still doesnt start up.

---

### Post by Kilz on 2006-06-18
[QUOTE=killzoneman0]even though i installed the driver, it still doesnt start up.[/QUOTE] What dosent start? Blender even though glxgears works? What video card do you have?  Also how did you install Blender?

---

### Post by Perfect Storm on 2006-06-18
What output do you get if your write **blender** in the terminal?

---

### Post by caldevil on 2006-06-18
Do you have an ATI card?

---

### Post by killzoneman0 on 2006-06-18
my output for putting blender in terminal is 

Using Python version 2.4
ERROR: Unable to open Blender window

Yes, i have an ATI card in my laptop. the model is 

ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

---

### Post by Kilz on 2006-06-18
[QUOTE=killzoneman0]my output for putting blender in terminal is 

Using Python version 2.4
ERROR: Unable to open Blender window

Yes, i have an ATI card in my laptop. the model is 

ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)[/QUOTE]
What is the output from 
```
fglrxinfo
```

---

### Post by killzoneman0 on 2006-06-18
[QUOTE=Kilz]What is the output from 
```
fglrxinfo
```[/QUOTE]


the output is 


Error: couldn't find RGB GLX visual!

---

### Post by Kilz on 2006-06-18
[QUOTE=killzoneman0]the output is 


Error: couldn't find RGB GLX visual![/QUOTE]
You do not have ati drivers installed. [You need to install the ATI drivers.]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

---

