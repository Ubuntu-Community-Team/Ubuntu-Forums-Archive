---
title: "nvidia driver problem?"
date: 2006-05-18
forum: General Help
---

### Post by Prudentissimus on 2006-05-18
Hi,


   I run Geforce 4 4400. And when i try to do: 

```

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

```

I get

```

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```


Please help.

---

### Post by kzutter on 2006-05-18
You do not say which of the commands is triggering the error, but why not follow the suggestion of editing xorg.conf?

sudo /etc/X11/xorg.conf

find Driver "nv", change to Driver "nvidia"

^o to write the changes
^x to exit

kill and restart X (or reboot)

---

### Post by Prudentissimus on 2006-05-18
xserver doesn't boot when i change manually.

---

### Post by tseliot on 2006-05-19
Why don't you try my script?

[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by Prudentissimus on 2006-05-19
That script runs; but X server still doesn't work.... ><

---

### Post by tseliot on 2006-05-19
Try to restore the backup of your previous xorg.conf:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by Prudentissimus on 2006-05-22
this is hopeless ><

---

### Post by kzutter on 2006-05-22
1. I see that your tagline says GeForce FX 5700 and the post was asking about GeForce4 4400

2. You never said which of the commands in your original post is the one that triggers the error.

3. It is not hopeless, restore from your backup and start over.

---

