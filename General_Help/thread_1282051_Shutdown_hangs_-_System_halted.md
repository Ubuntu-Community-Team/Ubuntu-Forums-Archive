---
title: "Shutdown hangs - System halted"
date: 2009-10-03
forum: General Help
---

### Post by InfectedDAS on 2009-10-03
Oh hello, I just started using Ubuntu 9.04 :) and i'm a newbie at it :(.
I managed to make the partitions and installed it using the graphical interface, and everything went smooth, but now when I turn it off an error occurs, which says #### System halted.

I tried to:

Terminal --> sudo gedit --> save --> restart --> no luck, error persists :confused:.

I tried:

sudo gedit /boot/grub/menu.lst
acpi=off apm=on 

sudo gedit /ect/modules
apm power_off=1


Any help would be appreciated :P.

BTW I'm using the x64 version, if it helps.

---

### Post by InfectedDAS on 2009-10-04
bump :-k

---

### Post by tuxxy on 2009-10-04
It would be helpful to have the actual errors it displays at boot-up and also make sure you create and installed to the partitions correctly.

---

### Post by InfectedDAS on 2009-10-04
Oh, ok ok (forgot that, sorry :|), the error appears when the laptop shuts down, then you have to press the power button in order to shut it down, else it just hangs there.

I'm not near the laptop.... or my house, so I can't write down the error :???:, I'll post it later, 
but it looks like "[111.111111] System halted"

Thanks by the way :-D!

---

### Post by InfectedDAS on 2009-10-05
Ok, I'm home, this was a long hard studying Sunday:wink:. 
The error that appears after the screen goes blank and everything seems shut down is:
[      54.658125] System halted.


hope this infromation helps :D

---

### Post by InfectedDAS on 2009-10-10
...ok, I've reinstalled Ubuntu 9.04 x64 and the problem persists.
[COLOR=DarkRed][  467.972000] System halted.[/COLOR]  --> the error ](*,)

I've added the lines inside

sudo gedit /etc/modules/

```
apm power_off=1
```

and inside sudo gedit /boot/grub/menu.lst 

```
acpi=off
```

If I add

```
acpi=force
```

Ubuntu won't load the logon screen.

So... I dont know what else to do, any idea, suggestion, something??

Maybe, maybe, but maybe it has something to do with the BIOS, but I don't know, and I'm not sure either. 


Thanks:wink:

---

### Post by knubles on 2009-10-11
I had the same problem on my 32 system.
It was caused by acpi=off.
Removed this and all OK.

---

### Post by InfectedDAS on 2009-10-11
> **knubles said:**
> I had the same problem on my 32 system.
It was caused by acpi=off.
Removed this and all OK.

Oh thanks knubles, but I tried it and still no luck, the laptop just stares at me with this
```
Boot from (hd0,7) ext 3 d2432b8a-b33b-4cbf-b3f1-be01766bd464
Starting up ...
Loading, please wait...
```

So it seems I can't delete or modify the 
```
acpi=off
```
line in the kernel sudo gedit /boot/grub/menu.lst

What else could it be?? How can it be solved??
Any ideas or suggestions. :confused:

Thanks

---

### Post by InfectedDAS on 2009-10-14
bump :confused:

---

### Post by InfectedDAS on 2009-10-16
Bumping :popcorn:

---

### Post by sirtrent on 2009-10-16
I'm not sure if this still exists in Jaunty, but I've for a long time had issues when shutdown would hang and it was because I had a smb/CIFS mount. Apparantly the network was being halted before the unmount, so my computer was unable to unmount the smb/CIFS properly and just hung, and in a similar way that you described.

If you have a smbfs mount try disabling it and see if you can shutdown.

If you don't use a smbfs mount, then I have no other idea.

---

### Post by InfectedDAS on 2009-10-16
[COLOR=#000000][FONT=arial]Oh thanks sirtrent:D, if i read correctly smb/CIFS is a sharing protocol (Windows based). [/FONT][/COLOR][COLOR=#000000][FONT=arial]
Unfortunately I'm a noob:???:, so I'm not quite sure if it is running or not, I may assume it's not, due to the fact that my wireless devices isn't detected and my ethernet does not connect to the Internet, though they're a separate problem, I'm "trying" to solve one at the time :rolleyes:[/FONT][/COLOR]

---

### Post by InfectedDAS on 2009-10-27
.....ok, i guess I'll wait for the new kernal 9.10 to come out, hope this problems is solved. ;)

---

