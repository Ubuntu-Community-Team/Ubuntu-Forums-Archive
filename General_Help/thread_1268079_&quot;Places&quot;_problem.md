---
title: "&quot;Places&quot; problem"
date: 2009-09-16
forum: General Help
---

### Post by Netspeed on 2009-09-16
I'm running 9.04 and I'm not sure what happened or where to check but I can't access anything in my "places". Even a USB stick plugged in can't be accessed.
Here's the message I get:
> Could not open location 'file:///home/keith/Pictures'
> No application is registered as handling this file

Any and all help is greatly appreciated!

---

### Post by wojox on 2009-09-16
Please open nautilus from command line or by pressing on a desktop without other opened window ALT+F2 keyboard keys and write into opened window nautilus.

Nautilus come in front of you select a directory on the right nautilus frame and right click with mouse a drop down menu come in front of you go to the end of this menu and select:
Properties - click on "Open with" tab
Select "Open Folder" application if it is already into list
If you don't have "Open Folder" listed please press the "+ Add" button and Select "Open folder" from the opened list of applications.
Then be sure "Open Folder" is selected and optionally remove other unused listed applications

Hope this helps

---

### Post by Netspeed on 2009-09-16
> **wojox said:**
> Please open nautilus from command line or by pressing on a desktop without other opened window ALT+F2 keyboard keys and write into opened window nautilus.

Nautilus come in front of you select a directory on the right nautilus frame and right click with mouse a drop down menu come in front of you go to the end of this menu and select:
Properties - click on "Open with" tab
Select "Open Folder" application if it is already into list
If you don't have "Open Folder" listed please press the "+ Add" button and Select "Open folder" from the opened list of applications.
Then be sure "Open Folder" is selected and optionally remove other unused listed applications

Hope this helps

Thanks Wojox! I didn't know what nautilus was so I went to Synaptic and it wasn't installed. When I marked it for install and I noticed a couple of "files" that were included as well. One was some type of bluetooth file. I think I had accidentally it earlier as I was getting rid of the bluetooth files and I must have taken nautilus with it.

After re-installation, everything works great. Thanks for setting me on the right path!

---

