---
title: "XGL doesn't start"
date: 2006-06-19
forum: General Help
---

### Post by Neo Ex on 2006-06-19
Hi everybody. Today and yesterday I tried to help a friend of mine installing XGL, but it doesn't start. That's what we did:
First, we installed nVidia drivers following the wiki:
```
sudo apt-get install nvidia-glx-legacy
```
Then, we modified the xorg.conf file and we changed "nv" into "nvidia". After rebooting, the nVidia logo appear (and glxgears works great), so the drivers are properly installed. We have removed the logo adding
Option          "NoLogo"
in xorg.conf.

Afterwards, we added these three lines to /etc/apt/sources.list

#compiz Quinn's
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

We issued
```
wget http://www.beerorkid.com/compiz/quinn.key.asc
sudo apt-key add quinn.key.asc
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```

Now, we created the XGL script:
```
sudo gedit /usr/bin/startxgl.sh
```
Inside we put

```
#!/bin/bash
/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
exec gnome-session
```

We tried with and without the #!/bin/bash line.
Then,
```
sudo chmod 755 /usr/bin/startxgl.sh
sudo gedit /usr/share/xsessions/xgl.desktop
```
and we paste

[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

We created the compiz script which we put on the desktop:

#!/bin/bash
gnome-window-decorator &
compiz --replace gconf

```
sudo chmod +x ./compiz
```

Now, we come to GDM, we restart the X server with Ctrl+Alt+Backspace, but when we try to log into XGL, this error appear:

X session : unable to launch "/usr/bin/starxgl.sh 
X session --- " /usr/bin/startxgl.sh 
"not found; falling back to default session

But... /usr/bin/startxgl.sh exists! What can we do?
Thanks in advance.

---

### Post by bluevoodoo1 on 2006-06-19
[QUOTE=Neo Ex]

```
#!/bin/bash
/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
exec gnome-session
```
[/QUOTE]

Instead of that (make a backup of it). Try this:

```
#!/bin/bash  

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2 && DISPLAY=:1 gnome-session
```

EDIT: This link may help as well...
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)

---

### Post by Nexus_ZX on 2006-06-19
Done,  but it is not change. (I' m Neo Ex's friend)

---

