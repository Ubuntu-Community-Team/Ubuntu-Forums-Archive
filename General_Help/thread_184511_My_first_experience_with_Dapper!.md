---
title: "My first experience with Dapper!"
date: 2006-05-30
forum: General Help
---

### Post by maka on 2006-05-30
Hi all... finally installed dapper drake 6.06 RC.  i just couldn't wait til June 1st. was too tempting

So far it's been overall a nice experience learning and testing everything seeing how everything works.

-i was able to set up my dual boot with windows xp and ubuntu!!
-i was able to install all my audio and video codecs via the extra repositories :-D 
-i was able to install flashplayer and fix the invisible text via ms fonts  :cool: 

here's where I'm struggling a bit...
-I seem to have a problem with the system hanging on bootup when I have my usb external harddrive connected. (hangs on "Mounting root file system").  Just wanted to know if theres a way to fix this, so i dont have to always unconnect my harddrive before booting
-Suspend isn't working... It seems to suspend fine, but it never wakes back up :confused: 
-My video card is a nvidia 5200fx, i was wondering where I go to see if it was detected and installed automatically or if not, how to install it?
-I installed the sun-java5-bin package from the terminal but firefox doesn't seem to recognize it yet.  Was wondering how to get firefox to recognize java?


Any help would be great!! Thanks in advance  :mrgreen:

---

### Post by badrinarayan on 2006-05-30
Regarding your last question, you will need to install sun-java5-plugin
You can open /etc/X11/xorg.conf, scroll down to the Device section to see
what driver has been assigned. See [this howto]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia"). You may search these forums if you want to install the latest drivers.

---

### Post by ssam on 2006-05-30
do you have an sata drive? possibly the usb drive is getting recognised first and taking /dev/sda, then when the start up tries to mount your sata drive its not where it expects to be.

can you attach your /etc/fstab

---

### Post by maka on 2006-05-30
[QUOTE=ssam]do you have an sata drive? possibly the usb drive is getting recognised first and taking /dev/sda, then when the start up tries to mount your sata drive its not where it expects to be.

can you attach your /etc/fstab[/QUOTE]

how do i get the fstab? sorry i'm still new to this

---

### Post by FredB on 2006-05-30
I used the howto and it works perfectly. Even if I think Planet Penguin Racer is kinda hard sometimes 8)

---

### Post by st4rdr1ft3r on 2006-05-30
in commandline:
```
gedit /etc/fstab
```

or go
Places>Computer

Then select Filesystem which takes you to /.
then the etc folder, then scroll down to fstab and open it that way.

---

### Post by maka on 2006-05-30
[QUOTE=ssam]do you have an sata drive? possibly the usb drive is getting recognised first and taking /dev/sda, then when the start up tries to mount your sata drive its not where it expects to be.

can you attach your /etc/fstab[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

heres my fstab with my external connected.. not sure whats going on  :-?

---

### Post by maka on 2006-05-30
sorry... bump?

---

### Post by g14 on 2006-05-30
[QUOTE=maka]
here's where I'm struggling a bit...
-I seem to have a problem with the system hanging on bootup when I have my usb external harddrive connected. (hangs on "Mounting root file system").  Just wanted to know if theres a way to fix this, so i dont have to always unconnect my harddrive before booting
-Suspend isn't working... It seems to suspend fine, but it never wakes back up :confused: 
-My video card is a nvidia 5200fx, i was wondering where I go to see if it was detected and installed automatically or if not, how to install it?
-I installed the sun-java5-bin package from the terminal but firefox doesn't seem to recognize it yet.  Was wondering how to get firefox to recognize java?

Any help would be great!! Thanks in advance  :mrgreen:[/QUOTE]
Download and install the stuff you need
```

sudo apt-get install sun-java5-plugin sun-java5-jre nvidia-glx nvidia-kernel-common

```

Reconfigure x.org to use the proprietary nvidia drivers and select nvidia instead of the open source nv driver. (run this command again and select nv if it breaks things for some reason.)
```

sudo dpkg-reconfigure xserver-xorg

```

FYI: compiz + Xgl + wobbly window goodness works PERFECTLY with the nvidia geforce 5200 FX. Here is a real quick minihowto on it:

1.) Install everything you need (older versions) in the ubuntu repositories.
```

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

```

2.) Run the first command and then make the bottom of the file look like everything below it:
```

sudo gedit /etc/gdm/gdm.conf-custom
[servers]
0=Xgl
1=Standard

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

3.) In the gnome menu, go to System --> Preferences --> Sessions --> Startup --> Add. Add the following entries:
```

gnome-window-decorator
compiz --replace gconf
xmodmap /usr/share/xmodmap/xmodmap.us

```

4.) Kill x and restart it using CTRL ALT Backspace. 

5.) From the terminal, run these command once:
```

nohup gnome-window-decorator &
nohup compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

```

The steps in 5 are only to test if it works. If it does, you should upgrade to the newest version in the repositories set up by QuinnStorm and compiz.net.

6.) Add the repositories for the newest compiz + x.org by running the first command and adding the next 2 lines to the bottom of the file:
```

sudo gedit /etc/apt/sources.list
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

```

7.) Update your system and kill the older versions of compiz:
```

sudo apt-get update && sudo apt-get dist-upgrade
killall compiz.real gnome-window-decorator

```

8.) Press CTRL ALT Backspace to restart X, login, and be amazed.

---

### Post by KrazyPenguin on 2006-05-30
[QUOTE=maka]sorry... bump?[/QUOTE]

I think it should be mounted as sda instead of hda.

Anybody else have any suggestions on this??

---

### Post by maka on 2006-05-31
> 
5.) From the terminal, run these command once:
```

nohup gnome-window-decorator &
nohup compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

```

The steps in 5 are only to test if it works. If it does, you should upgrade to the newest version in the repositories set up by QuinnStorm and compiz.net.

nohup gnome-window-decorator &
nohup compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

when i try to run these commands, i get this:
[1] 18331
desktop:~$ nohup: appending output to `nohup.out'
nohup compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
[2] 18367
[1]   Exit 127                nohup compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher
nohup: appending output to `nohup.out'

I also tried the way Poofyhairguy explained in his post:[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

doing his way, when i would run "thefuture" i would get these errors:
$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

not sure what the problem is, but seems like there were others who had this problem but couldnt find a solution.  thanks for the help btw :)

---

