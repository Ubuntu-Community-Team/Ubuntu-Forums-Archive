---
title: "Unkown Monitor: only 800x600, 640x480 and  400x300 screen resolution ?"
date: 2010-06-20
forum: General Help
---

### Post by ErjonH. on 2010-06-20
Hello, 

Yesterday i installed ubuntu 10.04 LTS, he allow me only 800x600, 640x480 and  400x300 screen resolution, how can i set 1280x1024 ?

---

### Post by NCLI on 2010-06-20
First of all, run Update Manager to make sure your system is up-to-date.

Then go to System->Administration->Hardware Drivers. This should show you a short list of drivers for your system, look for one for your graphics card.

---

### Post by ErjonH. on 2010-06-20
My system is up-to-date, while in Hardware Drivers no any drivers is on list.

[IMG]http://i48.tinypic.com/id572e.png[/IMG]

---

### Post by NCLI on 2010-06-20
Please open a terminal, then run these two commands:

```
lshw >> ~/Desktop/lshw
```
```
lspci >> ~/Desktop/lspci
```
This should create two files on your desktop. Please post them here as attachments.

---

### Post by ErjonH. on 2010-06-20
[IMG]http://i48.tinypic.com/9knria.png[/IMG]

thanks.

---

### Post by ErjonH. on 2010-06-21
another help ?

---

### Post by JamieEP on 2010-06-21
I am having exactly the same problem as you unfortunately. I've been trying for a week to resolve it, yet have had no luck. I suppose my problem is compounded by my being a new Ubuntu user. If I have any success I shall let you know, however at the moment, I have few hopes.

---

### Post by K.J. on 2010-06-21
For some reason your monitor isn't reporting it's identifier.  You will need to manually add the resolution you want to use to the X config.  For example, if you wanted to add the resolution 1280x1024 at 60 Hz refresh rate:


xrandr --addmode VGA 1280x1024
xrandr --output VGA --mode 1280x1024 --rate 60


Copy and paste the second xrandr command into ~/.xprofile to make it permanent.

---

### Post by JamieEP on 2010-06-21
I've tried that, unfortunately it returns "cannot find output 'xxx' ". I suspect it's because I use DVI, but I tried DVI, DVI-I, DVI-D, DVI-A and it still doesn't work. Any ideas?

Thanks.

---

### Post by cbrunhaver on 2010-06-21
post the results of:

lspci | grep vga


then type this:

sed -n '/- Modes/,/- End/p' /var/log/Xorg.0.log | sed 's/.*(0)://g' > $HOME/modes.txt

and post the contents of the modes.txt

---

### Post by JamieEP on 2010-06-21
I did this:

[IMG]http://i251.photobucket.com/albums/gg306/Jamieep89/Linuxissue.jpg[/IMG]

The modes.txt file was empty.

---

### Post by ErjonH. on 2010-06-22
> **K.J. said:**
> For some reason your monitor isn't reporting it's identifier.  You will need to manually add the resolution you want to use to the X config.  For example, if you wanted to add the resolution 1280x1024 at 60 Hz refresh rate:


xrandr --addmode VGA 1280x1024
xrandr --output VGA --mode 1280x1024 --rate 60


Copy and paste the second xrandr command into ~/.xprofile to make it permanent.

Cannot find output VGA :confused:

> **cbrunhaver said:**
> post the results of:

lspci | grep vga


then type this:

sed -n '/- Modes/,/- End/p' /var/log/Xorg.0.log | sed 's/.*(0)://g' > $HOME/modes.txt

and post the contents of the modes.txt

The modes.txt is empty :confused:

---

### Post by ErjonH. on 2010-06-22
Can i set up with a xorg.conf(need to create in 9.10) ?

---

### Post by corneal99 on 2010-06-22
[I][I]Can only get 600x480 screen resolution after fresh install?
[/I][/I]

---

### Post by cbrunhaver on 2010-06-22
no modes mens that it cannot get any EDID modes from your monitor.  You'll have to create a modeline in your xorg.conf.

Please type:

lspci 

and paste the whole output

---

### Post by cbrunhaver on 2010-06-22
There is no xorg.conf by default.  To generate one, type:

sudo gdm stop

sudo Xorg -configure

It puts it in your come directory, so type,

sudo cp ~/xorg.conf.new /etc/X11/xorg.conf

---

### Post by ErjonH. on 2010-06-22
> erjonhalili1@erjonhalili-desktop:~$ **sudo Xorg -configure**

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


I cannot find /tmp/.X0-lock to remove ?!

---

### Post by cbrunhaver on 2010-06-22
Sorry about being more specific.

press control + shift + F1 (or F2-F5) to get to a real terminal and then type the command.

---

### Post by JamieEP on 2010-06-22
Same issue:
[IMG]http://i251.photobucket.com/albums/gg306/Jamieep89/Ubuntuissue2.jpg[/IMG]

---

### Post by ionmich on 2010-06-22
Two suggestions.

!. Tell us the name and model number of your monitor. There is a chance that someone on this forum has a xorg.conf file you can copy.

2. Do a Google search with your monitor name and model number and the words "xorg.conf" included.

---

### Post by JamieEP on 2010-06-22
Well my monitor is a Samsung SyncMaster T200.

Thanks for any help :).

---

### Post by JamieEP on 2010-06-22
Sorry, double post.

---

### Post by ErjonH. on 2010-06-22
> **cbrunhaver said:**
> Sorry about being more specific.

press control + shift + F1 (or F2-F5) to get to a real terminal and then type the command.

I try but i fail in login :confused:

> **cbrunhaver said:**
> no modes mens that it cannot get any EDID modes from your monitor.  You'll have to create a modeline in your xorg.conf.

Please type:

lspci 

and paste the whole output

00:0c.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique] (rev 03)

---

### Post by JamieEP on 2010-06-22
I can't get a 'real' terminal, I don't know how to do that. I've tried the ctrl+shift+F1 but nothing happens. Anyway here's my lspci output:

[IMG]http://i251.photobucket.com/albums/gg306/Jamieep89/Ubuntuissue3.jpg[/IMG]

---

### Post by cbrunhaver on 2010-06-22
I'm sorry, it is control + alt + F1 to get into the terminal where you can type "sudo gdm stop" and generate a working xorg.conf.

It looks like others are having trouble with getting the matrox driver to work.    [http://ubuntuforums.org/showthread.php?t=1501511](http://ubuntuforums.org/showthread.php?t=1501511)
Obviously, the comment about nouveau driver is wrong (this is a matrox, not nvidia card).


You card is old enough that it is not supported by the matrox binary driver.
[http://www.matrox.com/graphics/en/support/drivers/latest/](http://www.matrox.com/graphics/en/support/drivers/latest/)
 
You can use the vesa driver driver for now but it is dead slow.  I would recommend spending $30 and buying this nvidia card like this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121360&cm_re=8400gs_pci-_-14-121-360-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121360&cm_re=8400gs_pci-_-14-121-360-_-Product)
It is dirt cheap and will breath new life into your system.

-Chris

---

### Post by cbrunhaver on 2010-06-22
Wow, a 440FX chipset.  Is that Pentium Pro or is it a early Pentium II?

---

### Post by JamieEP on 2010-06-23
No ideas?

---

