---
title: "Sound volume keys not working in 9.10 on IBM T42"
date: 2009-10-31
forum: General Help
---

### Post by Tacsi on 2009-10-31
Hi,

I have upgraded from Ubuntu 9.04 to Ubuntu 9.10 and the volume keys on my IBM T42 are not working. They have not been working under 9.04 either. However, I was hoping that the issue would be fixed in 9.10, but it isn't the case.

The issue might be only specific to T42 or similar models and as I stated above, only started with the release of 9.04. Until then the keys worked all fine from 7.04 through 8.10. Also, on my Lenovo X200 this issue is not found, namely the keys are working fine.

Any suggestions?

Thanks.

---

### Post by dependancyhell on 2009-10-31
I had a similar problem with a HP DV5.  It got no answers.

Obviously, entirely different manufacturers, and therefore, entirely different hardware, but pre-empting the lack of replies to the thread it might be worth a shot.

I have no idea how or why it did the trick, but installing Yiff, then restarting got the keys working with Kmix for me (though they still don't work in Gnome with other mixers).

Probably not a solution, but a direction for you to fiddle around with at least.

---

### Post by rapsodia on 2009-11-04
hey this worked for me on my t42 ubuntu 9.04 should work on 9.10 too

type this on your terminal

# echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
 
for all other brands try this see if you are at least getting a signal from your keys 

# acpi_listen



you need to be root btw

hope it helps

---

### Post by kirenpillay on 2009-11-10
I'm experiencing the same problem on an HP nx9420. 

ACPI_LISTEN doesn't generate any events when I hit the buttons.

---

### Post by rapsodia on 2009-11-10
on my ibm t42 on ubuntu 9.10 acpi_listen  didnt work either it didnt show me anything at all but 

**sudo su echo enable,0x00ffffff > /proc/acpi/ibm/hotkey** 

did, and it got piped to my volume control right away

maybe check if  all you would have to is replace hp instead of ibm Im not sure never had an hp.

good luck let me know if you need more help

---

### Post by kirenpillay on 2009-11-11
Thanks for the suggestion. I've tried, but there isn't an hp folder.

My /proc/acpi folder looks like:

ac_adapter/          event                processor/
battery/             fadt                 sleep
button/              fan/                 thermal_zone/
dsdt                 info                 video/
embedded_controller/ power_resource/      wakeup

and under ./button
lid/   power/ sleep/

---

### Post by rapsodia on 2009-11-11
I found this link 

[http://aldeby.org/blog/index.php/en-hp-pavilion-multimedia-buttons-configuration-under-linux-linux-quickplay.html](http://aldeby.org/blog/index.php/en-hp-pavilion-multimedia-buttons-configuration-under-linux-linux-quickplay.html)

it gives instructions on how to get the keys working and how to map them 

as well I bet you have tried this already but i may as well ask did you try go to

system/preferences/keyboard shortcuts and try to set the shortcuts there using your multimedia keys ?

---

