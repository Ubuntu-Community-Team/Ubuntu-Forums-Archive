---
title: "Automatically import pictures from camera"
date: 2010-12-26
forum: General Help
---

### Post by atomant2 on 2010-12-26
I'm trying to set up my parent's PC to automatically import pictures (in the background without any prompts)from the digital camera when it is plugged in via USB.  And also to back up their Home/Pictures folder via ftp.

Is there a way to automatically import pictures in the background without any prompts? 

I am using Deja Vu to back up via ftp and it seems to work fine.  There is an option for daily backup, but I don't think I can pick what time of day it backs up.  Is there a better option than Deja Vu?


Thanks,
Adam

---

### Post by atomant2 on 2010-12-27
bump

---

### Post by tredegar on 2010-12-28
> I'm trying to set up my parent's PC to automatically import pictures (in the background without any prompts)from the digital camera when it is plugged in via USB.
You could write a **udev** rule, so when the camera is plugged in, a script is called which downloads the photos.

You could use **inotify** to watch for the creation of **/media/camera** and do the same.

You could ....

> There is an option for daily backup, but I don't think I can pick what time of day it backs up.
You can use **cron** to call your backup script at any time(s).

---

### Post by jkallis on 2010-12-28
Hi,
How to get automatic import picture inn camera.


[Vivekananda rock memorial](http://www.*****************.com/tour-package) | [Kanyakumari Photos](http://www.*****************.com/how-to-reach-us) | [Sight Seeing in Kanyakumari](http://www.*****************.com/contact-us)

---

### Post by hakermania on 2010-12-28
Ok, so,you can make a script, that works even if there are multiple folders in your camera.
That's it:
```

#!/bin/sh
while [ 1 ]; do
for dest in /media/CAMERA_NAME/*; do
if [ -s /media/* ]; then
cp -r "$dest"/* /home/$USER/Pictures
break
fi
done
sleep 5
done

```
Where camera_name is the name of your camera. This will check all folders (but no subfolders) every 5 secs in your camera and copy them to your Pictures folder. And then, when done, it exits.

Disclaimer: not tested

---

