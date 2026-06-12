---
title: "Cronjob Request"
date: 2011-03-01
forum: General Help
---

### Post by joeknoodle on 2011-03-01
Hello, and thanks for reading this...  Ubuntu 10.10 / Gnome 2.x  I have my images stored on a usb disk that is somewhat delayed when starting Ubuntu. My wallpaper app - Cortina (which I love) - has difficulty due to this delay.  Is there some way to start Cortina, say 5 minutes after Ubuntu / Gnome by using crontab?  In researching this, I don't see a "delayed start" type of function - but what do I know LOL  If so, could someone please show me how.  Thanks.

---

### Post by seawolf167 on 2011-03-01
Make a script called cortina_startup.sh

```
#!/bin/sh
sleep 5
cortina &
```

Put in in your /home folder and make it executable

```
sudo chmod +x ~/cortina_startup.sh
```

Then go System -> Preferences -> Startup Applications, and add your script location

```
bash /home/yourusername/cortina_startup.sh
```

---

### Post by joeknoodle on 2011-03-01
That was a no-go. It still starts up at boot, even after double and triple checking all settings in the app and in the script.

---

### Post by seawolf167 on 2011-03-01
Forgot to remove the startup service, its been a while since I've had to do this, so it may have changed, but here it is:

You can get a listing of services by typing

```
ls /etc/init.d/
```

To remove a service, you'd then use the command

```
update-rc.d -f *servicenamehere *remove
```

Then your service (cortina) won't start until your startup script runs

---

