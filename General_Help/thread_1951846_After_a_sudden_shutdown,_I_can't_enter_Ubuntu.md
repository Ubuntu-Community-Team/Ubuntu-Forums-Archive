---
title: "After a sudden shutdown, I can't enter Ubuntu"
date: 2012-04-03
forum: General Help
---

### Post by Jayhawker on 2012-04-03
I have Ubuntu 11/10 through Windows, by wubi. After some odd behaviours, (windows getting stuck in the main upper bar, and the like), and after a forced shut down because the system was stuck this time, I cannot open Ubuntu anymore. 

When I have to choose between Windows and Ubuntu, and after choosing this last one, the following lines shows up  


GNU GRUB version 1.99-12ubuntu5

Minimal Bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

Grub>

Possible commands are

. [ authenticate background_color background_image badram boot break clear configfile continue cutmem echo export extract_entries_configfile extract_entries_source initrd insmod linux loadfont loopback ls lsfonts menuentry normal normal_exit probe return search search.file search.fs_label search.fs_uuid set setparams shift source submenu terminal_input terminal_output test unset

Please, is any way to solve the problem, in order to keep all the information and files, and mail?

Grateful in advance.

---

### Post by raja.genupula on 2012-04-03
its look like you have to restore GRUB . 
[https://help.ubuntu.com/community/Grub2#A.27.27grub.3E.27.27_Prompt_Booting](https://help.ubuntu.com/community/Grub2#A.27.27grub.3E.27.27_Prompt_Booting)

look at that .

---

### Post by Jayhawker on 2012-04-08
Thank You for your concern. But I'm not quite an expert on Linux. I've tried to apply the orders from the chapter you indicate but there has not been any positive result at all. The prompt GRUB> remains.

Any more suggestions, please?

> **raja.genupula said:**
> its look like you have to restore GRUB . 
[https://help.ubuntu.com/community/Grub2#A.27.27grub.3E.27.27_Prompt_Booting](https://help.ubuntu.com/community/Grub2#A.27.27grub.3E.27.27_Prompt_Booting)

look at that .

---

### Post by Bucky Ball on 2012-04-08
Can't help with your problem but just a tip: Wubi is not really intended as a permanent solution. It is intended to try Ubuntu for awhile and see how you like it before doing a hard drive install (which is a better, faster experience generally) or getting rid of it.

---

### Post by bcbc on 2012-04-08
Review this to recover the root.disk: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

Don't force shutdown for any reason. Use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") instead.

---

### Post by roelforg on 2012-04-08
Do NOT try to recover grub!
It'll erase the windows bootloader, scrapping windows.
Just boot in windows, the wubi page says that you need a clean shutdown of either os before you can boot ubuntu, so boot to win, and reboot, and boot to ubuntu

---

### Post by coldjeanz on 2012-04-08
> **bcbc said:**
> Review this to recover the root.disk: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

Don't force shutdown for any reason. Use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") instead.

REISUB has had maybe a 10% success rate for me, more often than not when I encounter a system freeze where I can't even move the mouse cursor, a hard reboot is all I can do.

---

### Post by bcbc on 2012-04-08
> **coldjeanz said:**
> REISUB has had maybe a 10% success rate for me, more often than not when I encounter a system freeze where I can't even move the mouse cursor, a hard reboot is all I can do.

I've also had some cases where it didn't work. The problem is you can't tell what sort of freeze it is. So you should always play it safe and try REISUB first; then if that doesn't work, shutdown. But if this is happening frequently then you might have some hardware compatibility issue - review your system logs and see if you can figure out what's going on.

---

