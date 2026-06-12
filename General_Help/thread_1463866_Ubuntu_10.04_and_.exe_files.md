---
title: "Ubuntu 10.04 and .exe files?"
date: 2010-04-27
forum: General Help
---

### Post by thisisspeedy on 2010-04-27
Hi every time I try and open an .exe file with "Wine", "Ubuntu" says that the file is not executable? What to do? I can't live without "Grab it" maybe I will just have to wait till Thursday I hope not. 

Thanks

---

### Post by kvarley on 2010-04-27
In 10.04 you need to right click your .exe file & click properties.

In the Properties window select the Permissions tab and then on this tab tick the box for allow executing.

Then load via wine! :guitar:

Have fun!

---

### Post by ingramproductions on 2010-04-27
Change the permissions on the file to make it executable. Right click the exe and open the permissions tab...

---

### Post by thisisspeedy on 2010-04-27
Thanks guys I will give this shot when I get home if all doesn't go well I will be back.

---

### Post by thedevilisbad on 2010-05-13
I have a similar problem.

I tried to fix it via properties, and that works all well and good except when you're trying to install something via CD/DVD. It still won't open things from CD/DVD or even mounted .ISO files. I even tried extracting the iso, and changing the properties on those files and then turning it back into an .iso and it still didn't work.

Any ideas?

---

### Post by surc on 2010-05-21
> **thedevilisbad said:**
> I have a similar problem.

I tried to fix it via properties, and that works all well and good except when you're trying to install something via CD/DVD. It still won't open things from CD/DVD or even mounted .ISO files. I even tried extracting the iso, and changing the properties on those files and then turning it back into an .iso and it still didn't work.

Any ideas?

I ran into a similar issue, where the setup.exe and autorun.exe both HAD executable permissions, and I was still getting errors from ubuntu. I got around it by using the command line.

cd into the directory where your disc or .iso is mounted, and use the command line wine command to run it.

Example:
```
cd /media/mountedDisc.iso/
wine Setup.exe
```Hope that helps you out!

---

