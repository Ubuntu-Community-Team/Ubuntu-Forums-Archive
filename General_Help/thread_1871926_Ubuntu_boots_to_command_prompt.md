---
title: "Ubuntu boots to command prompt"
date: 2011-10-29
forum: General Help
---

### Post by jmacx81 on 2011-10-29
Not sure what I did but I can't get ubuntu to boot. Is there a way I can format the partition and re do it? I can't see the partition from windows and when I boot to ubuntu it takes me to a script format.

---

### Post by mike555 on 2011-10-29
try typing    startx

---

### Post by jmacx81 on 2011-10-30
startx did not work. after booting it comes up to a script screen that ask for username and password after you log in, nothing it just waits for a command. is there a way to restore factory settings through this script?

---

### Post by pierreyy on 2011-10-30
try ctrl + alt + f7

---

### Post by pierreyy on 2011-10-30
i dont think formatting the partion or restoring the factory settings should be done so soon....lets try to open the gui  before formatting and such...

---

### Post by linuxaddix on 2011-10-30
it sounds like you are at the grub rescue screen.download this and burn it to cd...[http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download](http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download)
heres the directions...[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
basically just boot up with an ethernet connection,then wait till it loads.just click on recommended repair and wait till its done.restart and you should be able to boot back into ubuntu

---

### Post by jmacx81 on 2011-10-30
Ctl+Alt+F7 did nothing except keep my computer on the Ubuntu start screen for over an hour. The only problem with dowloading the stuff from sourceforge is when I go to reboot with an ethernet connection, I'm deployed to Afghanistan and I do have internet that is wireless but it is the kind where you have to log onto the network through a web browser. If there was a way to restore Ubuntu to factory settings I think it would be more helpful because then atleast I'll have Ubuntu working again.

---

### Post by linuxaddix on 2011-10-30
sorry bro thats the only way i know how to recover from grub rescue.

---

### Post by jmacx81 on 2011-10-31
and the only way to do that is rebooting with that disk in and hooked up to ethernet?

---

### Post by jmacx81 on 2011-10-31
Well maybe this will help. I get to the GRUB screen and select ubuntu, then it goes to the ubuntu start up screen, now instead of going to the ubuntu login screen it goes to a script log in screen and after you enter your username and password it goes to another ubuntu prompt and awaits a command.

---

### Post by linuxaddix on 2011-11-06
sounds to me its in a recovery state

---

### Post by linuxaddix on 2011-11-06
try this dont know if it will work
exit
normal boot
in the command line
try each and let me know

---

### Post by haqking on 2011-11-06
is is Server edition as it has no GUI.

It is not grub prompt, it is simply taking you to console mode and not starting gui.

try

```
/etc/init.d/gdm start
```

Was it previously booting to GUI or is this after a fresh install, sounds like you might have installed Server edition.

---

