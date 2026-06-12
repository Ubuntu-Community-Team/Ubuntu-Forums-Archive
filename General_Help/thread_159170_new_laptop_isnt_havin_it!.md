---
title: "new laptop isnt havin it!"
date: 2006-04-12
forum: General Help
---

### Post by honeydew on 2006-04-12
recently purchased a akoya ls.. I was hoping to install ubuntu on it, looked at all the bits and pieces and it seemed like the system was going to support it quite well.. however.. it unpacks the kernal.. and then just sits there.. this happens w/ both ubuntu 5.10 and 5.4 I havnt played w/ dapper, because it still seems pretty unstable.. it runs open/freebsd ok but openbsd dosnt support the wifi drivers.. has anyone else come accross such a problem? I tried playing around w/ the bios and found nothing.. Im kinda in the dark.

---

### Post by Al3xanR0 on 2006-04-12
Does the live cd run on it?

---

### Post by apjone on 2006-04-12
try ubuntu server first. You may need to specify special boot options when installing.

---

### Post by honeydew on 2006-04-12
nope server or expert mode does the same thing..

goes to

Uncompressing Linux... OK, Booting the kernel.


and stalls...

---

### Post by apjone on 2006-04-12
When you put the install disk in instead of pressing 'enter' or typing 'linux' or 'server' type 'linux pci=noacpi'

---

### Post by honeydew on 2006-04-12
[QUOTE=apjone]When you put the install disk in instead of pressing 'enter' or typing 'linux' or 'server' type 'linux pci=noacpi'[/QUOTE]


well golly Im to the install screen =]  what does that command do exactly? and is there anything I should look for when installing?

---

### Post by apjone on 2006-04-12
it turns off ACPI (Advanced Configuration and Power Interface)  which causes problems on certian hardware. basically its stuff like standby and hibernation. So give it a try.

---

### Post by honeydew on 2006-04-12
this mean I may not be able to use things like standby? and sleep?

---

### Post by apjone on 2006-04-12
You may be able to. just test it. If not you can always try something else

---

### Post by honeydew on 2006-04-12
yah.. it dosnt like freebsd.. I had it installed.. then when ever I would halt the system.. on reboot it couldnt find the kernel.. hopefuly Ill have a better run w/ ubuntu

---

### Post by apjone on 2006-04-12
o well, good luck and enjoy!!!

---

### Post by Sidk on 2006-04-12
After  you get it installed do a dist-upgrade then try editing the noapic in grub to see if it will boot for you. Lots of updates to acpi since those cd's.

---

### Post by rabidphage on 2006-04-12
try noapic as the boot parameter not acpi=off
apic is some sort of adbvanced interrupt controller for symmetric multiprocessing
it's not needed for normal laptops.
try just this parameter
might help

---

### Post by honeydew on 2006-04-12
if I do that and it dosnt work.. is there a way that I can edit the grub.. if the system fails?

---

### Post by honeydew on 2006-04-20
I tryed all recomended methods.. but had noo luck.. how can I test to see if suspend is working? I dont think it is.. I went to system Logout and tried to hibernate the computer... *shrugs*

---

