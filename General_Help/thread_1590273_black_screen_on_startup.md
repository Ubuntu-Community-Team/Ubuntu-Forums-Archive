---
title: "black screen on startup"
date: 2010-10-07
forum: General Help
---

### Post by killernerd on 2010-10-07
I know there have been quite a few topics about this already but for some reason i just can't get this ****ing thing to ****ing work.
 
So this is the deal.
 
i recently started my studies at the university of Antwerp (going for IT) and they said you needed 1. a laptop and 2. ubuntu on said laptop.
I'm not new to computers so i know what i buy and it happened to be so that i could buy a decent laptop via my school ( a dell vostro 3500). So i download and install ubunty in dualboot with w7. 
 
At first it worked, not always but it worked. So i started looking around and noticed it didn't recognize my wireless adapter, which makes sense because i hadn't installed the drivers yet. So I plugged it in with an ethernet cable and it made connection to the internet, shortly after it said some drivers were available for download, when i looked at what drivers i could download i saw my wireless adapter and some drivers for the nvidia 330m that sits in my laptop in "hybrid" mode with an intel chipset for when i'm running on battery.
 
installation went just fine but now i can no longer get into ubunty.
It goes as far as giving me the option to how i want to boot ubuntu (generic or recovery). Whatever i select it doesn't go further then the white cursor (when i selected generic) or when i select recovery, it does the entire recovery thing, it says done but then goes blank anyway.
 
Now the strange thing is that whenever i push my powerbutton it suddenly descides that it can show ubuntu on my screen but only to shutdown shortly after.
 
I think it has something to do with the graphics card (i googled a bit but i'm kinda new to ubuntu) and i've tried some stuff that i read here and there like:
 
- ctrl+alt+f1 (doesn't work)
- editing the command line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (didn't do anything)
 
 
I know i said i had the problem before but then i could just boot into windows, disable my nvidia chip and it would run just fine (most of the time).
 
As i said, I'm new to ubunty. all help is welcome :)
 
edit: oh yeah i forgot, i'm using the 32 bit ubuntu i downloaded from ubuntu.com (desktop edition) which i believe is version 10.04?

---

### Post by NT4usB on 2010-10-07
Solving video is tough to do without a display. *g*
When you are at the black screen with a cursor can you type anything and it shows on the display? 
If so, we can try some commands...```
cat /var/log/Xorg.0.log | less
```and arrow down looking for lines beginning with (EE) and (WW).

I had an old Dell that would display nothing. I plugged an old LCD into the VGA port on the laptop. That display worked fine and I was able to edit stuff and get the laptop display working.

---

### Post by Awareness on 2010-10-07
use a live usb (sudo apt-get install unetbootin)

mount your drive (usually a click under places) and then access to /var/log in you local hard drive looking for boot.log or system.log. (the path should be something like /media/your-disk-uuid/var/log)

Look for the problem there and google it

---

### Post by killernerd on 2010-10-09
Thanks for all the replies. I managed to undo the driver installation that was causing the problem. Apparently Ubuntu doesn't like to work with an nvidia chip and an intel chip in hybrid mode.
 
So if there's someone using a dell vostro 3500: don't install the nvidia drivers ^^

---

