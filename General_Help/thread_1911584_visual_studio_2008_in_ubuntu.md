---
title: "visual studio 2008 in ubuntu"
date: 2012-01-19
forum: General Help
---

### Post by cvkr on 2012-01-19
hi , i have created addins in msword using visual studio 2008 in windows platform.But now i want to convert it into ubuntu .So how can i install visual studio 2008 in ubuntu ...

---

### Post by nipunshakya on 2012-01-19
Hi. First off all, welcome to the forums. 
Sadly, u don't have visual studio in ubuntu. Even if u try to load it via virtual machine, nothing will work.
In short, you don't have visual studio in ubuntu. 
But, you can use a software called Mono or ellipse for your work in ubuntu. Any of the both can be downloaded from the software centre. Goodluck

Regards,WinuxUser

---

### Post by lechien73 on 2012-01-19
Seconded the welcome :)

In addition, if you check out [http://appdb.winehq.org/objectManager.php?sClass=application&iId=892](http://appdb.winehq.org/objectManager.php?sClass=application&iId=892) you can see that basically no versions of Visual Studio work properly with Wine.

When you said that you developed add-ins for Microsoft Word - are you planning on installing Microsoft Word under Ubuntu as well? If so, I'd strongly recommend that you use LibreOffice instead. You can check how well Word works under Wine here: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10)

---

### Post by cvkr on 2012-01-19
we need to develop addin for microsoft word. we have installed MSOffice in linux.But We donot know how to create addin in monodevelop..We have already created the addin in visual studio...
Please suggest me the procedure.

---

### Post by directhex on 2012-01-20
> **cvkr said:**
> we need to develop addin for microsoft word. we have installed MSOffice in linux.But We donot know how to create addin in monodevelop..We have already created the addin in visual studio...
Please suggest me the procedure.

Give up.

Ubuntu is *not* an appropriate platform for developing addins for Microsoft Office. It's not going to work for you.

---

### Post by Mark Phelps on 2012-01-21
> **directhex said:**
> Give up.

Ubuntu is *not* an appropriate platform for developing addins for Microsoft Office. It's not going to work for you.

+1 ... furthermore, lets say that your plugin does not work.

Then what?  Is it a problem with the MS Word kludge in Wine? Is it a problem with Wine using an older DLL than Word needs? Is it a problem with your plugin?

Basically, since you can't run Word without Wine, there's no way to diagnose the cause of the problem.

Windows apps-based development needs a Windows-native environment.

---

