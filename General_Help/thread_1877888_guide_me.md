---
title: "guide me"
date: 2011-11-08
forum: General Help
---

### Post by rahulhoare on 2011-11-08
i have win7 installed on my disk and i have already made 30gb free space for ubuntu11.10 to install.restarting and booting using usb ,using unetbootin to install, but kind of a dos page shows up in the initial menu. options there are:
default
help
install
command line install
expert install
rescue mode
install ubuntu.......
after selecting default , and doin the country, launguage and keyboard selection, a page opens asking partition disks using the partition methods:
guided-resize scsi2(0,0,0),partition #5(sda)and use freed space
guided-use entire disk
guided-use largest contiguous free space
guided-use entire disk and set up lvm
guided-use entir disk and set up encrypted lvm
manual.

confused on how to preceed. please guide

---

### Post by IWantFroyo on 2011-11-08
Choose "Default" if you want to go to the LiveCD environment (it's Ubuntu, except slower and running from the disc; you can still install from here).

Choose "Install" if you want to install it while skipping testing it.

I would recommend using "Default," so you can make sure your machine doesn't have any problems with Ubuntu.

---

### Post by rahulhoare on 2011-11-08
i chose default...this is what opened up

---

### Post by IWantFroyo on 2011-11-08
What opened up?

If the Ubuntu desktop comes up after several minutes (as Ubuntu gets heavier, the wait times get longer with LiveCDs), then everything is okay.

If it gives you a message about not meeting the hardware requirements, ignore it and install. You'll be able to install drivers afterwards using the "Additional Drivers" app.

---

### Post by rahulhoare on 2011-11-08
> **rahulhoare said:**
> 
after selecting default , and doin the country, launguage and keyboard selection, a page opens asking partition disks using the partition methods:
guided-resize scsi2(0,0,0),partition #5(sda)and use freed space
guided-use entire disk
guided-use largest contiguous free space
guided-use entire disk and set up lvm
guided-use entir disk and set up encrypted lvm
manual.

confused on how to preceed. please guide


as mentioned, the desktop doesnt appear, it proceeds direct to installation

---

### Post by IWantFroyo on 2011-11-08
Edit- Oops. Misread your post.

You'll want to tell it to use free space.

I thought you were asking which Unetbootin option to use.

---

### Post by rahulhoare on 2011-11-08
thank you for tht help, will proceed with the installation

---

### Post by rahulhoare on 2011-11-08
I installed grub boot loader to master boot record, now the computer boots into linux only, the boot screen doesn't appear asking me to choose between win7 and linux :(

---

### Post by rahulhoare on 2011-11-08
anyone... ???

---

### Post by oldfred on 2011-11-08
From the command line of your install.

```
sudo update-grub
```

That should show Windows as the last entry as it processes and then when you reboot it will be on your menu.

If that does not work post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

