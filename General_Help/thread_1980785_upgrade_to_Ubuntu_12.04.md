---
title: "upgrade to Ubuntu 12.04"
date: 2012-05-15
forum: General Help
---

### Post by manav_gupta on 2012-05-15
So I have spent half a day trying to resolve this with no luck.

I upgaded from 11.10 to 12.04 overnight, but I get no display.

/var/log/Xorg.0.log has:



lspci -v | grep NV
01:00.0 VGA compatible controller: NVIDIA Corporation GT218[NV 3100M] (rev a2) (prog-if 00 [VGA controller])


Attached is my xorg.conf and Xorg.0.log.

please help.

---

### Post by JC Cheloven on 2012-05-15
Hi, 

1) I understand that "no display" means you are presented with a text console. Have you tried this? ```
Ctrl-Alt-F7
```

2) Also, from a console (please hit Ctrl-ALt-F1 and log in just to be sure), try ```
sudo service gdm stop
``` then ```
sudo service gdm start
``` and go to ```
Ctrl-Alt-F7
``` or ```
Ctrl-Alt-F8
``` if you are not automatically presented to the desktop.

EDIT: I didn't analyze in depth your xorg.log, but it says at the end something about a mismatch between created screens and detected devices. ¿Do you have more than one monitor or something? If so, try to unplug some. 
Also you don't (probably) need xorg.conf, you can try deleting it (well, change its name or move it to a safe place just in case).

---

### Post by manav_gupta on 2012-05-15
Thank you for your reply. 

And yes, by no display, I meant no x - i only get presented with text login console.

Clt+Alt+F7 shows me (among other messages):

```
* Starting LighDM Display Manager    [fail]
```

After pressing Ctl+Alt+F1:

```
$ sudo service gdm stop
stop: Unknown instance:
``` 

Then:

```
$sudo service gdm start
gdm start/running, process 2970
```


Ctl+Alt+F7 doesn't show any new messages

Ctl+Alt+F8 shows me a blinking cursor on top left.

Thanks again, and any suggestions would be much appreciated!

EDIT: Attached the new /var/log/Xorg.0.log and blacklist.conf if it'd offer any insight..

EDIT 2: Removed xorg.conf and restarted gdm. Attached is the latest /var/log/Xorg.0.conf ... it shows the following line with EE:

```
(EE) No drivers available
```

---

### Post by JC Cheloven on 2012-05-16
> gdm start/running, process 2970 So it reports gdm as running, but still no desktop in the 7-nth console... 
Hope someone smarter will jump in with an explanation :)

In the meanwhile, as it could be a matter of configuration across versions, could you please run ```
sudo dpkg-reconfigure xserver-xorg
``` and see if that helps?

JC

EDIT: I hate upgrades, I always install clean. This kind of things reinforce my convictions  :neutral:

---

