---
title: "Changing the GRUB2 menu"
date: 2010-10-17
forum: General Help
---

### Post by thelugnut on 2010-10-17
I have separate partitions for three operating systems: Windows 7, Ubuntu 10.04, and another Ubuntu 10.04.
I want to modify the GRUB menu to eliminate the recovery mode options. I did this successfully with the controlling GRUB loader, but the menu still shows the other Ubuntu 10.04 recovery option.
Does anyone know how to handle this?:confused:

---

### Post by Quackers on 2010-10-17
Have you seen this guide by drs305?
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by sikander3786 on 2010-10-17
A nice guide mentioned by **Quackers** above.

You can also use statup-manager to do the job via GUI.

```
sudo apt-get install startupmanager
```

Start it from System > Administration > StartUp Manager.

---

### Post by Quackers on 2010-10-17
> **sikander3786 said:**
> A nice guide mentioned by **Quackers** above.

You can also use statup-manager to do the job via GUI.

```
sudo apt-get install startupmanager
```

Start it from System > Administration > StartUp Manager.

Doh! I always forget that one! It's a much safer way, for sure :-)

---

### Post by thelugnut on 2010-10-18
Sorry to be a bit dense. How can I eliminate a menu item using startup manager?

Perhaps I didn't state my case clearly.

I have two Ubuntu 10.04 o.s. on separate partitions.

I have successfully eliminated the "recovery" item on the Grub host Ubuntu o.s. 
I now want to eliminate the "recovery" item on the second Ubuntu o.s.

---

### Post by CowzRule on 2010-10-18
Boot into your second Ubuntu and remove the entry from it's grub.
```
sudo gedit /etc/default/grub
```
Look for the following entry
```
# Uncomment to disable generation of recovery mode menu entries
# GRUB_DISABLE_LINUX_RECOVERY="true"
```
Remove the "#" from the second line so it looks like
```
# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"
```
Then run
```
sudo update-grub
```
Reboot into your primary Ubuntu and run update-grub which will then remove the "recovery" line

---

### Post by Quackers on 2010-10-18
CowzRule's method is the one I used.
Looking at the Ubuntu page for Startup Manager it appears that many of the items it used to change with grub legacy don't even show up when grub2 is installed.
Hence your question, thelugnut.

In reply to your last question, I would suspect that you will need to edit the /etc/default/grub file in the "second" OS.

---

### Post by thelugnut on 2010-10-25
Sorry for the late reply... I was called away.
Okay, thanks for the replies. 
I followed CowzRule input and it did the job for me. :guitar:
I be happy now. Thanks

---

