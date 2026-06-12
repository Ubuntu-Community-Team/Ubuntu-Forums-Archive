---
title: "How do I install my scanner in ubuntu 9.10? (Installation requires root access)"
date: 2009-11-03
forum: General Help
---

### Post by weverjames on 2009-11-03
I need to access as root to finish installing my scanner. Ijust don't find the way to doit in karmic. I did easily in previous editions. I need some help here.

---

### Post by RiceMonster on 2009-11-03
> **weverjames said:**
> I need to access as root to finish installing my scanner. Ijust don't find the way to doit in karmic. I did easily in previous editions. I need some help here.

why don't you just use sudo?

---

### Post by koenn on 2009-11-03
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

what exactly is it that you need to do to get your scanner working ?

---

### Post by saulgoode on 2009-11-03
'**sudo -i**' will log you in as root.

---

### Post by earthpigg on 2009-11-03
this command will also log you in as root:
```
sudo su
```

but, beware & please consider answering the above questions about "why not just use sudo?" to accomplish your task.

whatever how-to guide you are reading is not intended for ubuntu, but can probably/possibly be modified a bit to work fine...

if you see this command:
```
# grep this bla bla that make build
```

you will want to enter this:
```
***_sudo_*** grep this bla bla that make build
```

---

### Post by weverjames on 2009-11-03
I am following the brother driver instruction. The last step is to modify a file system. For that, I need to login as root. I used to do that enabling login as root. But in karmic I can not get root to login, even after asssigning a password.
What should I do?

---

### Post by wildweathel on 2009-11-03
Forum policy: I can't tell you how to enable root login.  Can you link to or type up the last step of the instructions.  I (and a lot of other people) *can* translate into Ubuntu-ese.

---

### Post by weverjames on 2009-11-03
Let see how good you are:;)
Here you have:

Ubuntu 9.04
    1. Open "/lib/udev/rules.d/50-udev-default.rules" file.
    2. Edit "0664" to "0666" in "libusb device nodes" section.

    Before the edit---------------------------------

    # libusb device nodes
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0664"


    After the edit----------------------------------

    # libusb device nodes
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0666"


    3. Restart the OS.

---

### Post by earthpigg on 2009-11-03
```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```

---

### Post by koenn on 2009-11-03
> **earthpigg said:**
> ```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```

I'd try 
```
gksu gedit /lib/udev/rules.d/50-udev-default.rules
```

---

### Post by wildweathel on 2009-11-03
Two caveats from following those instructions:

1) That file may be changed by updates.  Thus, some time down the road, you'll install an update and your scanner will stop working.
2) That change opens a security hole by allowing any user access to your usb devices.

It's not a huge security thing, maybe you don't want to worry about it.  A possible scenario is that someone who has use of your computer (maybe a second login or SSH account--if you choose to activate SSH) might access an external hard drive bypassing permissions.  

#1 has the potential to be very irritating, though, so I'll try to do better.

Go to the folder /etc/udev/rules.d/ .  There's a README file that explains that files here override the /lib/udev/rules.d/ files.  More importantly, upgrades won't touch them.

So, use ALT-F2 to run these commands:

```
gedit /lib/udev/rules.d/50-udev-default.rules
gksu gedit /etc/udev/rules.d/51-scanner.rules
```Copy the line you want to change to the new file.  Now, there are two ways to change it.  Either 664 -> 666, which gives everyone access (possibly bad, but I'm sure it will work), or [FONT=monospace]add [/FONT]

```
GROUP="admin",
```to the line to give access to people who have permission to run sudo.

Save the new file, plug in scanner.  Hopefully that should be enough for it to work.  If not, please make sure the scanner is plugged in, open a terminal, run 

```
ls -l /dev/usb/
``` and post the output, plus the contents of the new (/etc/udev/rules.d/) file.

---

### Post by koenn on 2009-11-04
re. wildweathel's comments : that makes sense. Maybe the instructions should be updated.

weverjames, where did you get those instructions ?

---

