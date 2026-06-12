---
title: "Installing camera that wants to use hotplug"
date: 2006-06-08
forum: General Help
---

### Post by steve0921 on 2006-06-08
I've got a usb ccd camera that has install instructions requiring the use of hotplug. Since Ubuntu uses udev, and I can't even find a hotplug package, this presents me a problem.

I need someway to do what they need done in hotplug, but in Ubuntu (with udev?).

Unfortunately, I don't know much about either hotplug or udev. Can somebody translate these instructions for me? Is there a guide somewhere for moving from one to the other? Is there someting else entirely that I can do?

The hotplug instructions are as follows:

First change usb.usermap:
```
sudo gedit /etc/hotplug/usb.usermap
```
Paste in the lines:
```
sbig 0x0003 0x0D97 0x0001 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
sbig 0x0003 0x0D97 0x0002 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
sbig 0x0003 0x0D97 0x0003 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
sbig 0x0003 0x0D97 0x0101 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000

```
Copy a script (presumably to execute when loading the device, it uses fxload which I installed from repository already):
```
sudo cp sbig /etc/hotplug/usb/
```
And finally:
```
sudo /sbin/depmod -a
```

Thanks,
-Steve

---

### Post by Ocxic on 2006-06-08
[QUOTE=steve0921]
Copy a script (presumably to execute when loading the device, it uses fxload which I installed from repository already):
```
sudo cp sbig /etc/hotplug/usb/
```
[/QUOTE]

I can get you to here, I just don't know where the script comes from or why it's talking about fxload.. 
Do you have a link to this guide?

---

### Post by steve0921 on 2006-06-10
Here is the entire guide as I have it (attached).

The part with the issue is under the header:
> How to activate the hotplug for SBIG USB cameras.

-Steve

---

### Post by steve0921 on 2006-06-10
Oh, and I think the script is for loading firmware to the camera.

I've attached it (as a .txt) if that helps.

-Steve

---

### Post by steve0921 on 2006-06-15
I really need to get this working soon.

Can anyone help me??

---

