---
title: "Conky disappear"
date: 2010-11-10
forum: General Help
---

### Post by eeeH on 2010-11-10
Well, that's pretty much it... my conky disappear everytime I unmount any volume, as a pendrive or an external device. 
Does anyone know how to fix it?

---

### Post by VastOne on 2010-11-10
> **eeeH said:**
> Well, that's pretty much it... my conky disappear everytime I unmount any volume, as a pendrive or an external device. 
Does anyone know how to fix it?

Your conkyrc file is most likely still looking for the drives and will not start.

Try commenting out those lines with a # in front of the line and then unmount the devices to confirm

---

### Post by eeeH on 2010-11-11
> **VastOne said:**
> Try commenting out those lines...

Which ones?

---

### Post by VastOne on 2010-11-11
> **eeeH said:**
> Which ones?

Post your conkyrc file (or whichever one that does all conky commands) and I will take a look at what is going on.

---

### Post by eeeH on 2010-11-11
I have several conkyrc_something_else files. But the one who deals with the Hard Drives is this one:

```

#!/usr/bin/env python
import sys
import os
import subprocess

# root filesystem
print "${voffset}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -3}Ubuntu:${offset 8}${font Droid Sans:size=8}${voffset -1}${color2}${alignr}${fs_used /}${color} / ${color2}${fs_size /}${color}"

# /home folder (if its a separate mount point)
if os.path.ismount("/home"):
	print "${voffset -5}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -3}Home:${offset 8}${font Droid Sans:size=8}${voffset 5}${color2}${alignr}${fs_used /home}${color} / ${color2}${fs_size /home}${color}"

# folder in /media
for device in os.listdir("/media/"):
	if (not device.startswith("cdrom")) and (os.path.ismount('/media/'+device)):
		print "${voffset 4}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -3}"+device.capitalize()+":${offset 8}${font Droid Sans:size=8}${voffset -1}${color2}${alignr}${fs_used /media/"+device+"}${color} / ${color2}${fs_size /media/"+device+"}${color}"

```

---

### Post by blueridgedog on 2010-11-11
I suggest commenting out the media section then testing.  I suspect it is the cause.

---

### Post by eeeH on 2010-11-11
> **blueridgedog said:**
> I suggest commenting out the media section then testing.  I suspect it is the cause.

This isn't the best solution for me because I'll lose all the informations about my other partitions, and I really would like to keep it.

---

### Post by eeeH on 2010-11-11
Funny... I commented and uncommented this file and now I can unmout my devices and my conky's still there! That's pretty strange because I let everything like it was before. I hope it will stay this way when I'll reboot. 
But for now, the thread is solved...
Thanks guys.

---

### Post by VastOne on 2010-11-11
> **eeeH said:**
> This isn't the best solution for me because I'll lose all the informations about my other partitions, and I really would like to keep it.

I agree, but as a test we need to comment them out to verify that it is what is going on.  Once done we can troubleshoot further or post a bug regarding it.

---

### Post by VastOne on 2010-11-11
> **eeeH said:**
> Funny... I commented and uncommented this file and now I can unmout my devices and my conky's still there! That's pretty strange because I let everything like it was before. I hope it will stay this way when I'll reboot. 
But for now, the thread is solved...
Thanks guys.

Great to hear...

---

