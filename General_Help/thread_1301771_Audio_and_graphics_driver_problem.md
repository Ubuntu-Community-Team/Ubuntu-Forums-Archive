---
title: "Audio and graphics driver problem"
date: 2009-10-26
forum: General Help
---

### Post by agnivade on 2009-10-26
Hello friends,

I have just installed Ubuntu 9.04 in my laptop. But there is no sound coming of it. This may be a very lame question, plz bear with my ignorance.

Also, in visual effects, I tried to increase it from None to normal. It searched for drivers and then I got the message that Desktop effects could not be enabled. I reasoned that I should install graphics drivers.  So I downloaded the proper driver from ATI's site. Its a .run file
I did $ >   ./file_name.run

I got this- 

Created directory fglrx-install.wdqFjm
Verifying archive integrity..... All good.
Uncompressing ATI propreitory Linux driver-8.661 .......
...............

Detected configuration:
Architecture: i686 (32-bit)
X Server: X.org 7.4 and later releases

then I get a window titled "Message" with an empty button  :confused:

Whether I click the button or close the window, I get this
Removing temporary directory: fglrx-install.wdqFjm

Then its finished.....

Guys, can you help me out here ?


----
I have Dell Studio 15
ATI Radeon mobility HD 4570

---

### Post by clevertomato on 2010-01-26
I have a Studio 1555 with ATI 4570. I never even tried Jaunty on it because I heard from others it doesn't do well on this machine. It's new hardware, so I would recommend Karmic. I'm running Karmic amd64 on mine with no problems. If there's not a compelling reason that you're using Jaunty, try Karmic (9.10) instead.

I had difficulties when trying to use the drivers from the ATI site (the xxx.run files), although not the difficulties you describe, I'm sure because you're on Jaunty and I'm on Karmic. What works for me and what I stuck with is:

1. Installed Karmic from CD as you normally would.
2. Installed proprietary ATI drivers via System/Administration/Hardware Drivers (OR via terminal with "sudo apt-get install xorg-driver-fglrx fglrx-amdcccle")
3. Added " noapic" to the end of the appropriate line in my Grub file to get the brightness Fn keys working and the lid closure behavior working (note I did NOT have to change any ACPI settings)

I hope this helps.

---

