---
title: "How do I turn off Bluetooth support?"
date: 2012-01-18
forum: General Help
---

### Post by Dragonbite on 2012-01-18
It used to be I could go into the Startup Applications section and uncheck anything I don't want to auto-start when I log in.

In Unity, it doesn't show things like Bluetooth and other system services.  I see the startup-sound and any applicable applications I have installed (Guake, Dropbox, etc.), but I can't get to the more system-orientated ones.

My laptop does not have bluetooth and 99.9% never will (and if I get it somehow, then I'll turn it on).  It may not take much in the way of resources, but I still want to turn it off (it's an older system.. the released resources may be noticeable).

---

### Post by wolfen69 on 2012-01-18
Click on the little thing next to your name where you shut down, and select system settings. You will find bluetooth settings there.

---

### Post by Dragonbite on 2012-01-18
> **wolfen69 said:**
> Click on the little thing next to your name where you shut down, and select system settings. You will find bluetooth settings there.

I have it turned off, but on bootup (or shutdown.. can't remember which right now) I see bluetooth included in the text stream and list of processes.

---

### Post by syerges on 2012-01-18
uninstall it if you don't need it/want it.

---

### Post by ajgreeny on 2012-01-18
> **syerges said:**
> uninstall it if you don't need it/want it.
+1

That's what I have done for some years.  Just keep a look out for other packages that are removed when you remove the bluetooth packages, as some of the library packages also will remove things you probably still need.

---

### Post by mcduck on 2012-01-18
This guide will help you to make the Startup Applications show all the services, not just the ones you've added yourself, like it did in previous Ubuntu versions: [http://shuffleos.com/3496/how-to-enable-all-applications-in-startup-applications-ubuntu-11-10/]("http://shuffleos.com/3496/how-to-enable-all-applications-in-startup-applications-ubuntu-11-10/")

...and if you want to turn Bluetooth off by default, you can edit /etc/default/bluetooth and change "BLUETOOTH_ENABLED=1" to "BLUETOOTH_ENABLED=0". (my current laptop seems to remember if I've turned bluetooth off from the indicator, but the one I had before always defaulted to booting with bluetooth enabled no matter what I did, and changing this setting solved the problem)

edit: I was just going to add that disabling the device from BIOS would be a good idea, and then I realized you said the machine doesn't even have bluetooth. In that case you of course don't need to do that, and changing the setting in /etc/default/bluetooth makes no difference.

---

### Post by Dragonbite on 2012-01-18
> **ajgreeny said:**
> +1

That's what I have done for some years.  Just keep a look out for other packages that are removed when you remove the bluetooth packages, as some of the library packages also will remove things you probably still need.

Any information on "some of the library packages also will remove things you probably still need." may be?

The link will probably do it for me though.

---

### Post by ajgreeny on 2012-01-19
> **Dragonbite said:**
> Any information on "some of the library packages also will remove things you probably still need." may be?

The link will probably do it for me though.
OK, here goes.

**libbluetooth3** -  will also remove evolution and several other evolution packages, and other non evolution packages.
**libgnome-bluetooth7** - will also remove gnome-network-manager.

This is in 10.04.  I have no idea about later ubuntu versions.  I did not,therefore, remove those two packages, but all other bluetooth packages were removed from my machine with no ill effects.

---

