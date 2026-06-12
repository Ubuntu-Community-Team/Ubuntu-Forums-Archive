---
title: "How do you want the Trash to function in Ubuntu?"
date: 2009-08-06
forum: General Help
---

### Post by sancho panza on 2009-08-06
If none of the poll choices below suit you, suggest your own. Some related bugs on launchpad are:
[GNOME needs a "Trash Autopurge" functionnality]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150112")  
[add an option to autodelete items from trash:/ after a specified span of time]("https://bugs.launchpad.net/nautilus/+bug/228369")
[nautilus trash does not show file origin or deletion date]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/222068")
[in trash: show delete-date ]("https://bugs.launchpad.net/nautilus/+bug/301552")

---

### Post by sancho panza on 2009-11-22
The trash feature in ubuntu is useless to me in its current form. Can somebody tell me how I can permanently delete files that were deleted (sent to trash) more than 30 days ago?

Please help! The trash on my hard drive is swelling and I do not wish to permanently delete files that I deleted in the recent past!

---

### Post by Rod J on 2010-02-02
Yes, this is a badly needed feature. Being a long time Windows user and being somewhat conservative I have always had my Windows Recycle Bin sorted by deleted date and only manually purge the oldest files first. I think many people migrating to Ubuntu would be surprised by the lack of this feature in Ubuntu. I believe it's been implemented in KDE, so why not in Gnome?

---

### Post by ibuclaw on 2010-02-02
> **Rod J said:**
> Yes, this is a badly needed feature. Being a long time Windows user and being somewhat conservative I have always had my Windows Recycle Bin sorted by deleted date and only manually purge the oldest files first. I think many people migrating to Ubuntu would be surprised by the lack of this feature in Ubuntu. I believe it's been implemented in KDE, so why not in Gnome?

Every has their own priorities. Some get addressed sooner than others.

Last time I checked, everything is in place for this to be integrated into the GUI Browser.

A typical info file will look like this:
(Located in ~/.local/share/Trash/info )
```

[Trash Info]
Path=/media/usb0/DCIM/100D3000/DSC_9137.JPG
DeletionDate=2010-02-01T21:55:58

```
I do believe that is pretty much the bare-bones information of what you need to get what you want done.

Regards
Iain

---

### Post by hawthornso23 on 2010-02-02
Under the current system each user has to individually delete their own trash. Not all users can be trusted to do that regularly. Nor should they have to as this is a system maintenance type thing which ordinary users should not have to think about. Automatic trash deletion would help.

If your disk starts to get low on space then the first thing you want to do is delete trash to free up space. But with each user having their own separate trash (and with the problem of root trash as well) this isn't the simple operation it should be.

Would therefore also like to see a sudo password accessed option in system administration to manage trash by device, so that you could clear all trash stored on a particular device for all users (including root) easily.

---

### Post by sancho panza on 2010-02-02
The work is this bug is being "worked on" since 2002. There has been good progress
of late, but needs us users to push it to get out the door. 
The latest screenshot is [shown here]("http://ubuntuforums.org/showpost.php?p=8408238&postcount=11").

You can help push this bug by voting and commenting on [this page]("https://bugs.launchpad.net/nautilus/+bug/301552").
(click on the "This bug affects xx people. Does this bug affect you?" link in the bugreport)

---

