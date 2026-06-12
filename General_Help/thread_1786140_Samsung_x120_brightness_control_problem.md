---
title: "Samsung x120 brightness control problem"
date: 2011-06-19
forum: General Help
---

### Post by Thor Andersen on 2011-06-19
Hi. 
I just installed Ubuntu 11.04 on my samsung x120 laptop. 
It works fine but the brightness control doesn't work, it shows change in the bar but nothing happens to the brightness...
When the laptop is plug in it's on full brightness and when on battery it's no brightness..

Any good solutions? I have search the web and found alot of solutions to other laptops bout samsung and non samsung laptops but non of it seems to work...

Is there anyone out there with a x120 that got the problem fixed? or maybe general fix?

---

### Post by rdmcall on 2011-10-02
Also just loaded on a Samsung X120 qnd the same problem (no brightness)... any solution yet????

Hate to have to go back to Microsoft ///

---

### Post by Matt__ on 2011-10-02
does the x120 have a bios entry 
"Brightness mode control" (under the boot menu section)
If it does then set this to manual and see if enables FN key control.

This has also been said to work;- a script to change brightness from console
```

#!/bin/bash
echo &#8220;Input brightness level (0-99)&#8221;
read i
sudo setpci -s 00:02.0 F4.B=$i
exit 1
```[COLOR=Silver]#I also have a brightness/FN key solution for the n145, but cant find the ppa atm...will get back to you if those solutions are no good.

[/COLOR]#/edit
this worked on a friends N145 ([this ppa](https://launchpad.net/~voria/+archive/ppa) contains several tools to improve user experience on samsung netbooks)
 
[FONT=arial][SIZE=2][COLOR=black]Tr[SIZE=2][FONT=Arial, Helvetica, sans-serif]y the following (from French Ubuntu forum)[/FONT][/SIZE]:[/COLOR][/SIZE][/FONT]```
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install samsung-tools samsung-backlight
sudo reboot  
```[FONT=arial][SIZE=2][COLOR=black] 
   **[SIZE=2][FONT=Arial, Helvetica, sans-serif]I[/FONT][/SIZE]**t  appears on some systems the function keys  begin working but the  brightness does not change. In this case, try  appending  &#8220;acpi_backlight=vendor&#8221; to the GRUB_CMDLINE_LINUX line in  Suspend /  Resume below.[INDENT] ```
[SIZE=3]GRUB_CMDLINE_LINUX=&#8221;acpi_sleep=nonvs acpi_backlight=vendor&#8221;[/SIZE]
``` [/INDENT][/COLOR][/SIZE][/FONT]

---

### Post by kolinab on 2011-10-17
Or try the solution I found here: [http://ubuntuforums.org/showthread.php?t=1861411](http://ubuntuforums.org/showthread.php?t=1861411)

---

