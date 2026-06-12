---
title: "OS's menu at the start , how to let windows first option (Defult) !?"
date: 2009-08-03
forum: General Help
---

### Post by Majd04 on 2009-08-03
OS's menu at the start , how to let windows first option !? 
for my sister , i wont them totching anything until they got inside thir stupid windows ,
i mean when 10 sec done windows go as default ?


i also want to ask for the Ciro Dock last virsion hope anyone could tell me where to found it .


thx majd

---

### Post by Locutus_of_Borg on 2009-08-03
```
sudo nano /boot/grub/menu.lst
```

change "default 0" to whatever line number the windows line is
it counts each "title" as an OS and starts at 0

post your menu.lst here if that makes no sense


latest cairo dock from subversion:
```
svn checkout http://svn.berlios.de/svnroot/repos/cairo-dock/trunk
```

---

### Post by arqbrulo on 2009-08-03
Ok, if I understand you correctly, you want to have windows as your default OS. Well, boot into Ubuntu, once you're in, hit "Alt+F2", which is the RUN dialog. type "gksu gedit /boot/grub/menu.lst" and hit enter. Now somewhere around the top or mid way down, there's a line "default=0" or something like that. "0" is the first entry on the boot menu. So let's say that you have the following on your menu:
[LIST]
[*]Ubuntu 9.04
[*]Ubuntu 9.04 recovery
[*]memtest x86
[*]Windows Vista
[/LIST]

Then you would change the "default=0" to "default=3" Also, you can change the "timeout=10" to something else (just don't change it to 0).

---

### Post by arqbrulo on 2009-08-03
@Locutus_of_Borg: haha, you beat me to it. I took too long to write a reply.

---

### Post by merlinus on 2009-08-03
The easiest way by far is to install startup-manager via synaptic or Applications/Add/Remove.

And if you only change the default number in menu.lst, it will change the next time there is a kernel upgrade.  To avoid this, you will have to move the windows stanzas above the linux ones, and leave the default at 0.

But startup-manager provides a gui to do all this painlessly.

---

### Post by drs305 on 2009-08-03
Here's a link to StartUp-Manager:
[_StartUp=Manager_]("http://ubuntuforums.org/showthread.php?t=818177")

Go to the Boot Options section after you have installed it.

---

