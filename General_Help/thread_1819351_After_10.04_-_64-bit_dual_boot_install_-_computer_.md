---
title: "After 10.04 - 64-bit dual boot install - computer will not boot at all - Emachines"
date: 2011-08-06
forum: General Help
---

### Post by Lbcnu24 on 2011-08-06
**[SIZE=2]Well,  I was installing Ubuntu 10.04LTS, to make a dual boot along side,  within windows 7 home edition...  the installing went fine, had no  issues resizing the partitions etc... installed all the necessary items  that i wanted, screenlets, driver for the video card to get "animations"  for wobbly windows etc... until...[/SIZE]**

[SIZE=3]i set the screen saver to 10 minutes and sleep modes to  never...  I shut the computer off a few times to check and see if I  could still get into win7 and ubuntu from boot menu... which I was able  to, **NO PROBLEM**...  until...[/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]i left the computer, assuming that the screen  saver turned on... came back to the computer, and then the computer was  trying to "reboot"...  but each time I would hard reset it, it would  give me the F12 or F10 options to get the BIOS setup ...  but it does  not boot further than that to actually get me to the boot menu where I  choose OS.    The monitor says "no signal to monitor" "going to sleep"  and it keeps resetting itself like that... now I cannot even get into  windows 7 at all and neither ubuntu...[/SIZE]
[SIZE=2]
its an Emachines 64bit AMDx2, 4 gigs of Ram, [/SIZE]
[SIZE=2]
the computer works fine from live cd... and I  have tried to boot from BIOS and have set Hard drive as primary for boot  sequence... nothing... doesnt even look into the hard drive at all...   but everything works fine from live cd, I love ubuntu :)[/SIZE]

 [SIZE=2]the only thing I can figure is that since i  changed the driver in ubuntu or "updated it" as the feature gave me, so I  can get the "extras - animations" - screwed the video card up... which  is integrated... and then now... it beeps while trying to boot, an  error beep... and then shuts down and then tries to reboot..., as I  said before, it doesnt go to boot menu where I get to choose which OS to  use... I get the splash screen that tells me about Emachines, Press Del  for settings and F12 for boot menu... thats it... what do I do?[/SIZE] HELP! [SIZE=2]please... what could it be?[/SIZE]

[SIZE=2]Also, not one thing was changed to cause an error beep.  It all happened after the install of Ubuntu 10.04, after checking to see if both OS's would work, which they did.  But now the computer is not cooperating.[/SIZE]

---

### Post by phosphide on 2011-08-06
Can you access your hard drive from the live cd?

---

### Post by Lbcnu24 on 2011-08-06
[SIZE=3]Yes I can!  but from the computer itself, it will not access the hard drive[/SIZE]

---

### Post by phosphide on 2011-08-06
> **Lbcnu24 said:**
> Yes I can!  but from the computer itself, it will not access the hard drive
Does it show that your Win 7 and Ubuntu installations are still there and partitioned correctly?

---

### Post by Basher101 on 2011-08-06
Could you also tell me your Model? I also got an eMachines with 4gigs, dual core and onboard graphics (Intel 4 Chipset Family). Mine is E725

---

### Post by Lbcnu24 on 2011-08-06
> **phosphide said:**
> Does it show that your Win 7 and Ubuntu installations are still there and partitioned correctly?

Like I said, It does not boot me that far to show me the options to choose from for boot...
 model number is not available at this time...  it is a media center Emachines... dual core AMD, within the last year, so it's relatively new

---

### Post by Lbcnu24 on 2011-08-06
[SIZE=3]I think I may have to fix the grub for it, after I trouble shoot the RAM sticks...  because it doesnt let me go to a grub menu...   

So what I did, I installed ubuntu from a live cd at initial boot.  Installed it into a new partition beside windows,so it's not inside of windows, but windows was on the hard drive first...

how do I fix the grub in this situation?  
[/SIZE]

---

