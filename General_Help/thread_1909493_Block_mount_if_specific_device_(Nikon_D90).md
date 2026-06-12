---
title: "Block mount if specific device (Nikon D90)"
date: 2012-01-15
forum: General Help
---

### Post by LilYoda on 2012-01-15
Hey y'all

To be able to import pictures in Digikam from my D90, I need to make sure that it is not mounted by the OS

Is there a way to block a specific device from mounting?  By adding an entry in fstab maybe?

I have tried search, but it seems most people are having problems with something they want to mount and that isn't;  My issue is the opposite.  The OS mounts the D90 automatically, and I have to unmount it every time.

Thanks in advance

---

### Post by bluexrider on 2012-01-15
**Configuring Automounting**

 To enable or disable automount open a terminal and type **gconf-editor** followed by the **[Enter]** key. 
Browse to **/apps/nautilus/preferences/media_automount**. 
The **media_automount**  key controls whether to automatically mount media. If set to true, then  Nautilus will automatically mount media such as user-visible hard disks  and removable media on start-up and media insertion. 
There is another key **/apps/nautilus/preferences/media_automount_open**.  This controls whether to automatically open a folder for automounted  media. This key can also be set in the Nautilus (file manager) window.  From the **Edit** menu in Nautilus select **Preferences** and then select the **Media** tab.

This will prevent automounting of media and external drives. If you want specific drives mounted upon booting then edit /etc/fstab


**Configuring Program Autostart**

 To control which programs automatically start when you plug in a device, go to **System->Preferences->Removable Drives and Media**.  


ref: [HERE]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by LilYoda on 2012-01-15
That's an option.

I thought about this, but it would force me to define in fstab every USB key or SD card I have, or to mount them manually.  Considering the number of USB devices I have, it would be more cumbersome than unmounting the D90 every time I plug it.

Instead of preventing automount globally, I was wondering if there was a way to block a specific device from being mounted.

---

### Post by bluexrider on 2012-01-15
You may be able to use "Storage Device Manager" to set the parameters of each storage device.

available in the software center, this may help

---

