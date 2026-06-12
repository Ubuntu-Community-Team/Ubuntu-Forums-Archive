---
title: "&quot;allow executing file as program&quot; automatically unchecks"
date: 2010-10-20
forum: General Help
---

### Post by alonewestand on 2010-10-20
Trying to test a game via wine in a Windows directory.  Cannot edit anything in the "properties" menu.  Anything I change automatically resets itself.  Cannot set program to executable so I can't run it to test it.

---

### Post by sikander3786 on 2010-10-20
Seems like you've got the **noexec** flag in the mount properties in fstab.

Can you please post the output from /etc/fstab?

```
gksudo gedit /etc/fstab
```

Copy/paste carefully. Donot change anything in the file or you might screw your system.

---

### Post by alonewestand on 2010-10-20
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=68e8d011-ed80-46ae-8676-4038926f6644 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a9c07eaf-9f93-4efe-aa0a-f417dc125868 none            swap    sw              0       0

---

### Post by ubudog on 2010-10-20
Have you tried this yet?

```
chmod +x filename
```

---

### Post by CharlesA on 2010-10-20
> **sikander3786 said:**
> Seems like you've got the **noexec** flag in the mount properties in fstab.

Can you please post the output from /etc/fstab?

```
gksudo gedit /etc/fstab
```

Copy/paste carefully. Donot change anything in the file or you might screw your system.

Use gksudo instead on sudo for graphical apps.

---

### Post by ubudog on 2010-10-20
Or you could use a command-line editor, like joe.  But yeah, for graphical apps, gksu or gksudo is best.

---

### Post by sikander3786 on 2010-10-20
> Use gksudo instead on sudo for graphical apps.

Point well noted :-) I have updated the code accordingly.

---

### Post by CharlesA on 2010-10-20
> **sikander3786 said:**
> Point well noted :-) I have updated the code accordingly.

Thanks. :)

---

### Post by ubudog on 2010-10-20
Just curious, would anything actually happen if you didn't use gksudo?

---

### Post by sikander3786 on 2010-10-20
> **ubudog said:**
> Just curious, would anything actually happen if you didn't use gksudo?
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[http://ubuntuforums.org/showthread.php?t=851911](http://ubuntuforums.org/showthread.php?t=851911)

---

### Post by alonewestand on 2010-10-20
The same thing comes up when I use gksudo as it does in my first reply.

chmod +x gives me bash: syntax error near unexpected token `('

---

### Post by gandaran on 2010-10-20
> **ubudog said:**
> Just curious, would anything actually happen if you didn't use gksudo?
I have used sudo every-tine for graphical apps  since ubuntu 7.04 and never had any problem!

---

### Post by CharlesA on 2010-10-20
> **alonewestand said:**
> The same thing comes up when I use gksudo as it does in my first reply.

chmod +x gives me bash: syntax error near unexpected token `('

Can you post the exact command you are using, including the error?

> **gandaran said:**
> I have used sudo every-tine for graphical apps  since ubuntu 7.04 and never had any problem!

The only thing that will happen is that it'll screw with the permissions, owner and group. See [here]("https://help.ubuntu.com/community/RootSudo#Graphical%20sudo").

---

### Post by ubudog on 2010-10-20
> **CharlesA said:**
> Can you post the exact command you are using, including the error?



The only thing that will happen is that it'll screw with the permissions, owner and group. See [here]("https://help.ubuntu.com/community/RootSudo#Graphical%20sudo").

Ah, I see.  Thanks!

Make sure you didn't misspell it or something.

---

### Post by VMC on 2010-10-20
Changing permissions didn't stick for me either until I rebooted.

---

### Post by mc4man on 2010-10-20
> Trying to test a game via wine in a Windows directory
By default wine (Wine Windows Program Loader) will not allow .exe's to run unless the exec. bit is set (which .exe's don't need), part of a new 'security policy'

Use wine instead which will bypass the cautious-launcher

either in a terminal
wine /path/to/whatever.exe

Or r. click  - open with - other application - custom command and use as the command
wine

Small note - it's probably not the best idea to run a windows program in wine if it's located on a windows install - you didn't say...

---

### Post by ubudog on 2010-10-20
Also, if you have a spare copy of a Windows CD, there is always virtualbox or VMware.  Virtualbox is free last time I checked.  You can install Windows in a virtual machine, and run everything you need on Windows via that.  Very useful.

---

### Post by alonewestand on 2010-10-20
> By default wine (Wine Windows Program Loader) will not allow .exe's to  run unless the exec. bit is set (which .exe's don't need), part of a new  'security policy'

Use wine instead which will bypass the cautious-launcher

either in a terminal
wine /path/to/whatever.exe

Or r. click  - open with - other application - custom command and use as the command
wine

Small note - it's probably not the best idea to run a windows program in  wine if it's located on a windows install - you didn't say... 	

This was the problem and it worked like you said by opening with the wine command rather than the program loader.  However trying to run through the terminal gives me the bash error.  I don't think I'm typing the path correctly.  Well as long as I can run it with the command through right clicking it should be fine.  Thanks all.

---

### Post by ubudog on 2010-10-20
Glad you got it working!

---

### Post by mc4man on 2010-10-20
> Well as long as I can run it with the command through right clicking
You should notice for future use that 'wine' has been added to your r.click open with menu (in other words no need to proceed on to the 'other application' menu

you could, if desired, set 'wine' as the default (d. left click) for .exe by r. clicking on any .exe -> properties -> open with (screen - if not see there than use the add button

For a terminal when using extended paths a little trick is to open a terminal, type the command and hit the spacebar.
Then drag and drop the file onto the terminal, click in terminal to return focus and press enter.

---

### Post by ubudog on 2010-10-20
> **mc4man said:**
> You should notice for future use that 'wine' has been added to your r.click open with menu (in other words no need to proceed on to the 'other application' menu

you could, if desired, set 'wine' as the default (d. left click) for .exe by r. clicking on any .exe -> properties -> open with (screen - if not see there than use the add button

For a terminal when using extended paths a little trick is to open a terminal, type the command and hit the spacebar.
Then drag and drop the file onto the terminal, click in terminal to return focus and press enter.

Then you can just double click the file, and it'll open in Wine.

---

### Post by tehweezil on 2010-12-24
> **ubudog said:**
> Have you tried this yet?

```
chmod +x filename
```

Same problem, except I'm using a Linux executable file and chmod +x doesn't work because when I attempt to run it I get the 'permission denied' error x|

Meh, this is shameful because I've been a proud Linux user and now Ubuntu's being paranoid and permission deadlocked as I remember Vista being before I got fed up with it and switched to Linux. Deja vu. x|

---

### Post by sid32 on 2011-01-16
I had this happen to me in 10.10. The issue seems to be with the newest udisk. 

To fix open synaptic (system - admin -synaptic). Check your udisk version number. See if there is a newer version available. If there isn't you'll want to go to: 

[https://launchpad.net/ubuntu/lucid/+package/udisks](https://launchpad.net/ubuntu/lucid/+package/udisks)

Download the version for your computer, probably the one found in 
udisks 1.0.1-1build1 in i386 (Release).

Eject all usb devices. Download to desktop, open a terminal and do a force install. sudo dpkg --force-overwrite -i nameofpackage.deb

Plug in USB again. Check to see if you can make programs executables. I use Floola to manage my ipod and thats the one I checked. If it works, open synaptic and lock the udisk version.

---

