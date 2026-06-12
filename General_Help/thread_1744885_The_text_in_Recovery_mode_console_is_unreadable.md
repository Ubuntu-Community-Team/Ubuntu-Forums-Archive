---
title: "The text in Recovery mode console is unreadable"
date: 2011-04-30
forum: General Help
---

### Post by zavaidok on 2011-04-30
Hi. I'm a new Ubuntu user (11.04 dual boot with Windows 7). When I try to load Ubuntu (recovery mode) or if I press Ctrl+Alt+F1, the image gets corrupted showing a white screen with black writing on it, but which is unreadable. Also the words seem to be spelled backwards. I'm trying to install an NVIDIA driver and I need to stop first the X server. Is there any solution to this?
Thanks.

---

### Post by zavaidok on 2011-05-03
Anyone?

---

### Post by SigmundFreud on 2011-05-05
No solution (except 'learn the key combinations and do it out of your head'), but I want to add to this: I have exactly the same problem. Kubuntu Natty, fresh installation, Nvidia driver.

---

### Post by Ter Rymon on 2011-05-21
[https://bugs.launchpad.net/ubuntu/+bug/782872](https://bugs.launchpad.net/ubuntu/+bug/782872)

This has been reported as bug in natty.  Please help by adding info to this bug.

---

### Post by linuxinstalledfromhdd on 2011-05-21
I would boot from a live usb ubuntu drive, and find the changes you made to the configuration settings, or undo the changes you made manually.

---

### Post by Ter Rymon on 2011-06-11
> I would boot from a live usb ubuntu drive, and find the changes you made to the configuration settings, or undo the changes you made manually.


Which configuration files set the console font and/or screen resolution?

---

### Post by Ter Rymon on 2011-06-11
From terminal: two things 

edit /etc/default/console-setup

```
sudo gedit /etc/default/console-setup

```

AND reconfigure console-setup

```
sudo dpkg -reconfigure console-setup

```

Note to get the recovery mode fixed AFTER doing the above:

1. boot into recovery mode
2. wait until its finished
3. press the down arrow until no movement on your screen
4. enter 
```
dpkg -reconfigure console-setup

```
 Yes, I know you can't read what you typed.
5. hit ENTER
6. enter
```
reboot
```
7. hit enter

---

### Post by udayarr on 2012-02-28
My ubuntu 10.04 LTS display text unreadable..[IMG]http://imageshack.us/photo/my-images/703/screenshot1hm.png/[/IMG]

---

### Post by udayarr on 2012-02-28
[IMG]http://imageshack.us/photo/my-images/407/screenshot1dy.png/[/IMG]the pic shows the detail.. nothing is readable including terminal .. only squared boxes everywhere..pls help me.. nothing is worked.

---

