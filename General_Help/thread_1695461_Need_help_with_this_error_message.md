---
title: "Need help with this error message"
date: 2011-02-25
forum: General Help
---

### Post by TimEnid on 2011-02-25
Can someone point me in the right direction regarding this message
[IMG]http://i1080.photobucket.com/albums/j324/timrock83/C360_2011-02-2522-25-56.jpg[/IMG]

---

### Post by 3Miro on 2011-02-25
I don't think this error is the real source of your problem. If you cannot get to graphical interface, then the video driver is most likely the culprit. Which video driver are  you using (assuming your signature is accurate, you are using either default Ubuntu or the proprietary ATI)

You should be able to login from this screen and enter console mode. Then you can type:
```
cat /var/log/Xorg.0.log
```
and
```
cat /var/log/Xorg.0.log | grep EE
```

The first command will list the log for the graphical environment and the second one will list all errors that you got. Please post those on the forum so that we can give further help.

PS You can still boot from a liveCD, right?

---

### Post by TimEnid on 2011-02-25
Here is what I get. I will try to boot from the live cd now. Sorry for the cam pics.
[IMG]http://i1080.photobucket.com/albums/j324/timrock83/C360_2011-02-2522-55-58.jpg[/IMG]

---

### Post by linuxien. on 2011-02-25
[SIZE=2]hope this would help[/SIZE]
[http://ubuntuforums.org/showthread.php?t=1315876](http://ubuntuforums.org/showthread.php?t=1315876)

---

### Post by TimEnid on 2011-02-25
Yes my signature is correct

---

### Post by TimEnid on 2011-02-25
> **linuxien. said:**
> [SIZE=2]hope this would help[/SIZE]
[http://ubuntuforums.org/showthread.php?t=1315876](http://ubuntuforums.org/showthread.php?t=1315876)
sorry, but im browsing this forum on my phone, since my pc is not functioning. can you just describe the fix for me. would really appreciate it. thanks

---

### Post by linuxien. on 2011-02-25
[SIZE=2]  I was suspecting it was a problem about my oldie GFX card just like you. But actually it wasn't. The problem is:  Ubuntu doesn't boot successfully if a USB disk (any USB mass storage device) was plugged in before boot.  My flash disk was left plugged on the PC from another session. I've also experienced this with a USB external Harddisk on another system just to make sure.  Some other people are experiencing this as well. They suppose it happens randomly, it is mostly because they leave their USB disks plugged in randomly.  I've also reported this as a bug in Ubuntu...  Thanks[/SIZE]

---

### Post by 3Miro on 2011-02-26
There is a problem with the proprietary ATI drivers. I am not sure what the problem is, but you can uninstall the drivers with:

```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```

```
sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core
```

Then Reboot. This should get you back to a graphical environment.

Unless you have a specific feature/problem with the default ATI drivers, it is recommended that you don't install the proprietary ones.

---

### Post by TimEnid on 2011-02-26
> **3Miro said:**
> There is a problem with the proprietary ATI drivers. I am not sure what the problem is, but you can uninstall the drivers with:

```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```

```
sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core
```

Then Reboot. This should get you back to a graphical environment.

Unless you have a specific feature/problem with the default ATI drivers, it is recommended that you don't install the proprietary ones.

That didn't work. After that first command I got this.
[IMG]http://i1080.photobucket.com/albums/j324/timrock83/C360_2011-02-2609-45-30.jpg[/IMG]

---

### Post by Yellow Pasque on 2011-02-26
Use this sequence of commands. Some of the commands may not work depending on how you installed fglrx, but run them anyway.
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
If you want to have a stab at installing fglrx again, use: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by TimEnid on 2011-02-26
> **Temüjin said:**
> Use this sequence of commands. Some of the commands may not work depending on how you installed fglrx, but run them anyway.
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
If you want to have a stab at installing fglrx again, use: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

wow. this fixed it. man, you guys are great. for a minute, i thought i would have to reinstall the entire system. thanks a lot for all your help.

---

### Post by TimEnid on 2011-02-26
althought the issue is fixed, when restarting, i still see the error message (minus the option to log in) in this pic
[img]http://i1080.photobucket.com/albums/j324/timrock83/C360_2011-02-2522-25-56.jpg[/img]
and i also notice that it takes a few seconds longer to boot into the gdm.

---

