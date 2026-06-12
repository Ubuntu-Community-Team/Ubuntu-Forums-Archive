---
title: "virtualbox"
date: 2009-08-02
forum: General Help
---

### Post by amyst on 2009-08-02
I want to use several windows applications that don't run on Jaunty. Would they run on virtualbox? My impression is that I need to install windows in virtualbox, then install these applications in windows. Does anyone with experience know if this will work?

---

### Post by aesis05401 on 2009-08-03
I run VirtualBox with windows.  It works fine for regular graphics.  There is experimental 3d acceleration in the latest version, but I don't know how well it allows one to play Windows games.

What sort of apps do you want to run, and how much hardware do you have to dedicate for the VM?

---

### Post by jocampo on 2009-08-03
> **amyst said:**
> I want to use several windows applications that don't run on Jaunty. Would they run on virtualbox? My impression is that I need to install windows in virtualbox, then install these applications in windows. Does anyone with experience know if this will work?

It depends of the aplication. Yes, you can install VirtualBox on top of Ubuntu Linux and then, create a Windows XP or VISTA virtual machine. Once installed, you just put the application you want inside the Windows machine (the virtual one) Now, not all Windows applications work well inside a virtual machine. If the program or software requires certain hardware access, probably won't work, like some games or Video Editing software.

If you have the time and the software give it a try and setup a virtual machine and see what happen. You can also ask directly in the Virtualization sub-forum; most people have try their software on VMs so chances are high that someone already tested it and can provide additional feedback.

---

### Post by amyst on 2009-08-03
I have WinXP installed in Virtualbox an hour ago. The application I'm using requires fair amount of CPU. It doesn't require special hardware and seems running well so far. Thanks for the suggestions!

---

### Post by wirate on 2009-08-03
Did you try Wine. It will save you some resource that virtualization eats up

---

