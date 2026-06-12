---
title: "stuck while booting."
date: 2011-11-27
forum: General Help
---

### Post by Matrix01 on 2011-11-27
when i turn this netbook on,
xubuntu stops booting live session from usb pen drive,
so
press alt ctrl delete
and 
booting continues.

---

### Post by WinterMadness on 2011-11-27
I dont think ctrl alt del does anything in linux.... could be wrong though.

anyway, are you trying to say that you cant ever boot successfully? You arent able to log in, no graphical user interface, no command line etc?

Tell me if one of these two possibilities arise:
1) You see a cursor blinking
2) Black screen (could be blue or any other color, but its just blank)

If so, try turning ACPI off via grub. Also, when you turn it off, realize that this is a temporary solution ONLY. Setting ACPI equal to nothing is one thing, actually turning it off can cause hardware issues(such as turning your fans off, not being able to read the state of the battery. Keeping it in this state can cause hardware failure).

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Matrix01 on 2011-11-27
cursor under the xubuntu logo moving for a while, then stops,
and
log in tab shows up, 
blue blank screen is on background, nothing else.


> **WinterMadness said:**
> I dont think ctrl alt del dndoes anything in linux.... could be wrong though.

anyway, are you trying to say that you cant ever boot successfully? You arent able to log in, no graphical user interface, no command line etc?

Tell me if one of these two possibilities arise:
1) You see a cursor blinking
2) Black screen (could be blue or any other color, but its just blank)

If so, try turning ACPI off via grub. Also, when you turn it off, realize that this is a temporary solution ONLY. Setting ACPI equal to nothing is one thing, actually turning it off can cause hardware issues(such as turning your fans off, not being able to read the state of the battery. Keeping it in this state can cause hardware failure).

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by WinterMadness on 2011-11-27
Well, that certainly sounds odd, and im sure someone else can come in and offer more advice. However, I think you should try the ACPI thing. Dont worry about screwing it up, because it resets every time you boot unless you follow specific instructions to make it not do so

goto the link i gave
ctrl+f How to temporarily set kernel boot options on an installed OS (not wubi)

---

### Post by BC59 on 2011-11-27
You should consider as well to re-create the boot USB because sometimes after some uses they tend to fail.

---

### Post by WinterMadness on 2011-11-27
thats a good point.

---

### Post by Matrix01 on 2011-11-27
well,
i created this persistent usb flash drive yesterday,
and ran chkdsk,
output is no problems.



> **BC59 said:**
> You should consider as well to re-create the boot USB because sometimes after some uses they tend to fail.

---

### Post by oldtimer7777 on 2011-11-27
Here is something they don't tell you about Pendrive/Thumbdrive Live sticks of Ubuntu.

You need to always power your system off all the way down to remove them. 

If you remove one before the power cycle is done, or you force a cold boot, this is happen everytime. 

Or if you press the power off and can't power down the system normally, then you will have a problem just like this happen. 

Always power your system down all the way down using USB Live Ubuntu.  If it hangs, and you power off sooner than it is done, you have to create a new image on your USB. No if ands or buts about it.

> **Matrix01 said:**
> when i turn this netbook on,
xubuntu stops booting live session from usb pen drive,
so
press alt ctrl delete
and 
booting continues.

---

