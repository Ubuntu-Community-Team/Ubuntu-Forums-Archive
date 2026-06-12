---
title: "ubuntu stops during boot, where can I find info?"
date: 2010-01-01
forum: General Help
---

### Post by Infil on 2010-01-01
Hi,

Sometimes, during the white logo segment of the boot of 9.10 my laptop freezes/stops. I get the impression that it doesn't freeze, only stops because when I press Ctrl+Alt+F1 I get some artifacts, and I can turn on and off the numlock.

Anyway, to get out of it I have to shut down my laptop by holding the power button down. After this there is nothing written to syslog, messages nor kern.log. I've deleted those files, reproduced the hang, and then used a live CD to access the harddrive, but the file simply weren't there. 

So my question is, where can I find information from the system about what actually happened? :confused:

---

### Post by Groundswell on 2010-01-01
i don't know about how ubuntu 9.10 boots, it's rather funky and i only used it for about a day due to regressions. i'm assuming it's freezing on that white ubuntu logo "pre"-splash that slows down the whole boot process? haha, you can try enabling "text during boot" via startup-manager which is available via synaptic, but i don't know if they will effect anything other than the usplash.

---

### Post by Infil on 2010-01-01
Thanks for the quick answer!

Yep, it is white logo. Thanks for the tip. Maybe it shows where it suddenly stops.

---

### Post by Infil on 2010-01-02
For some reason "text during boot" is already checked. "Show boot splash" is unchecked :confused:

---

### Post by Groundswell on 2010-01-02
i really have no idea, someone else with experience with 9.10 needs to chime in. for the time being you could.... try booting to terminal (failsafe) with each boot, doing so should constrict to text based loading.

once loaded and logged in, start gnome (i'm assuming thats what you're using) manually using
```
sudo etc/init.d/gdm start
```

but i really really don't know karmic, that white ubuntu splash might be part of grub? i really didn't understand it when i saw it.

---

### Post by Groundswell on 2010-01-02
took a gander around the web, you should have a look at
[HTML]https://help.ubuntu.com/community/Grub2[/HTML]

specifically "Configuring GRUB 2" and the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. [COLOR="Red"]For a black screen with boot processes displayed in text, remove "quiet splash".[/COLOR] To see the grub splash image plus a condensed text output, use "splash". The entry "acpi=off", if required, would also be an option entered on this line. 

apparently i'm rusty, i had it backwards

---

### Post by Infil on 2010-03-02
Whenever I remove the "splash" part, it boots up perfectly without exceptions. It is apparently the splash command itself which stops the system. I've used my laptop like that since.

It has been a while now but I still have the problem. No updates have remedied it. Is there anyone else who experiences the same issue and knows anything more about it?

---

