---
title: "Help a newb get wine to work?"
date: 2011-12-23
forum: General Help
---

### Post by maccollie on 2011-12-23
I successfully installed wine on ubuntu but I can't get any exe files to work due to the ubuntu blocking dangerous exe bit thing
I can't change file permissions for files on my C drive for some reason. I think this problem is due to the way how I installed ubuntu and/or the slave/master settings. Whenever I try to check the "allow executable file" box under file permissions, the check disappears after a second if the exe file is on my C drive. However it works perfectly fine if the exe file is located on my H drive. 

My main OS windows 7 is located on my C drive. Ubuntu was installed in windows 7, so that I can only boot to ubuntu if I first boot windows 7 from the C drive, and then select Ubuntu from the windows 7 boot menu. The actual ubuntu installation files are located on my H drive. 
The C drive is master and H drive is slave. I forget how to change the master/slave settings in BIOS...

Any idea what I should do to allow me to change file permissions on the C drive? 

I'm going through all of this trouble because I screwed over the task scheduler in windows 7 and maybe the registry so that the internet never works on wifi. But wifi still works on ubuntu.

---

### Post by c5wagner on 2011-12-23
first open terminal and paste
```
sudo gedit /usr/share/applications/wine.desktop
```

then change this
```
Exec=cautious-launcher %f wine start /unix
```

to this
```
Exec=wine start /unix %f
```

after this wine will open any file without question so be careful, also no need to change permission on files.

---

### Post by maccollie on 2011-12-24
worked!
thanks a bunch sir

---

