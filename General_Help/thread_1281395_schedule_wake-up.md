---
title: "schedule wake-up"
date: 2009-10-03
forum: General Help
---

### Post by kalug on 2009-10-03
Hi all out there,

I have a MS-1221 mobo and in BIOS there is no entry like APM. Still, I want my notebook to wake up on certain days at 3 o'clock (automatically). Is there any way to do this? I've tried nvram-wakeup but I get the following .conf file (genereted by guess-helper):

################################################
##  Mainboard autodetection information:
##
##    - Mainboard vendor:   "MSI"
##    - Mainboard type:     "MS-1221"
##    - Mainboard revision: "Ver 1.000"
##    - BIOS vendor:        "American Megatrends Inc."
##    - BIOS version:       "A1221IG6 V1.1"
##    - BIOS release:       "05/28/2007"

And when I just write in the terminal:
sudo nvram-wakeup -s $((`date +%s` + 20 * 60))
I get the following errormsg:
/dev/mem: Operation not permitted

I have read somewhere that not all mobos are able to wake up automatically from a soft-off state... how can I find out whether mine is one of those?

I appreciate any critical question or help.

Thanks

---

### Post by kalug on 2009-10-04
Hi all,

I finally managed to make my notebook boot automatically ;) 
A big thank goes to Mr Tarnay Kálmán, too, who provided me a very usefull link
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

If you want to see my solution read the following thread (started by myself on a nice german portal):
[http://www.vdr-portal.de/board/thread.php?postid=845670#post845670](http://www.vdr-portal.de/board/thread.php?postid=845670#post845670)

Should you have any question related to my solution than just ask.

G

---

