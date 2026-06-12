---
title: "boot parameter meanings &amp; how to implement"
date: 2011-01-23
forum: General Help
---

### Post by wpshooter on 2011-01-23
There are several boot parameters shown when pressing the F6 key on the Ubuntu Maverick Alternate install CD.

For example: ACPI=OFF
             NOAPIC
             NOLAPIC
             NOMODESET
             EXPERT MODE

Where do I find a "**_complete_**" explanation of what these parameters do, _when it is appropriate_ to select them and HOW to select them ?

Thanks.

---

### Post by tredegar on 2011-01-23
Try [http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
or [http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch10.html](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch10.html)

Some kernel options may be specific to the customised kernel of the distro you are using. If this is the case, the distro's kernel documentation should explain them.

Hope this helps.

---

### Post by wpshooter on 2011-01-23
> **tredegar said:**
> Try [http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
or [http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch10.html](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch10.html)

Some kernel options may be specific to the customised kernel of the distro you are using. If this is the case, the distro's kernel documentation should explain them.

Hope this helps.

Thanks.

I briefly browsed these but mostly they are "Greek" to me.

For instance, somewhere in there it says that ACPI=OFF turns that parameters off, well I can pretty much discern that for myself BUT I can see NO specific explanation of WHY/WHEN I would want/need to turn it off, other than it saying that because your hardware had "trouble" with ACPI, what trouble are they talking about ?

And here is the reason that I am asking about these parameters.

Recently, I installed Maverick.  When I get to the desktop and if I walk away from the machine for about 15 minutes the screen goes BLANK because of inactivity.  And this happens in spite of the fact that I have the power management parameter set to NEVER.  Is using these boot parameters something that can possibly solved this problem or is the screen going BLANK even though the power management is set to NEVER just another bug in Ubuntu ?

Thanks.

---

### Post by Iowan on 2011-01-23
> **wpshooter said:**
> ... When I get to the desktop and if I walk away from the machine for about 15 minutes the screen goes BLANK because of inactivity.  And this happens in spite of the fact that I have the power management parameter set to NEVER. . The BIOS might also have a power management setting... unless that's the one you meant.

---

### Post by tredegar on 2011-01-23
I don't think the kernel boot options are going to help you here.
> When I get to the desktop and if I walk away from the machine for about 15 minutes the screen goes BLANK because of inactivity. And this happens in spite of the fact that I have the power management parameter set to NEVER.
Maybe this isn't because of power management (and there are several tabs for battery power, mains power, sleeping the computer, sleeping the display, dimming the display... - did you check them _all_?) but perhaps it is a screensaver?

---

### Post by wpshooter on 2011-01-23
> **tredegar said:**
> I don't think the kernel boot options are going to help you here.

Maybe this isn't because of power management (and there are several tabs for battery power, mains power, sleeping the computer, sleeping the display, dimming the display... - did you check them _all_?) but perhaps it is a screensaver?

All power management parameters in BIOS turned OFF AND ALL power management settings at Ubuntu desktop set to NEVER, and NO screen saver is ACTIVE and in spite of ALL of this the display still goes BLANK after about 15 minutes of inactive.

It is almost like, that when I am choosing the NEVER in the power management section, that it is NOT getting written to what ever configuration file controls this or that perhaps upon reboot the original configuration file is replacing the altered one !!!

Thanks.

---

### Post by tredegar on 2011-01-23
10.04 seems to be better behaved, and (mostly) does as it is told.

---

### Post by wpshooter on 2011-01-23
> **tredegar said:**
> 10.04 seems to be better behaved, and (mostly) does as it is told.

So are you saying that this IS a possible bug that is still in 10.10 ?

Note:  That when I reinstalled this same computer back to Jaunty 9.04, I had none of these display going blank problems.

A shame, that you would have to go all the way back to 2 or 3 versions back to get things to work properly.

Thanks.

---

### Post by wpshooter on 2011-01-30
> **tredegar said:**
> 10.04 seems to be better behaved, and (mostly) does as it is told.

So, today I finally got around to trying 10.04.

It has exactly the same problem.

Screen/display goes BLANK after about 10 to 15 minutes of inactivity despite the fact that the power management parameter is set to NEVER.  No there is no screen saver running/active.

Can anyone tell me what configuration file the "NEVER" in the power management section of Ubuntu is supposed to be written to, so I can check and see if that parameter is actually being written to the file when I change it from the install default setting to the NEVER setting ?

Thanks.

---

