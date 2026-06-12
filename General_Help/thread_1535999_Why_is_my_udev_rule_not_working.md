---
title: "Why is my udev rule not working?"
date: 2010-07-21
forum: General Help
---

### Post by davavanstone on 2010-07-21
Hi
Ive created a rule using this information for my lg usb drive, i want it to perform a script upon connect.

looking at parent device '/devices/pci0000:00/0000:00:1a.7/usb1/1-4':
    KERNELS=="1-4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="300mA"
    ATTRS{urbnum}=="2485"
    ATTRS{idVendor}=="090c"
    ATTRS{idProduct}=="1000"
    ATTRS{bcdDevice}=="1100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="16"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="LG Electronics"
    ATTRS{product}=="USB Drive"
    ATTRS{serial}=="HNB0981113022756"

Here is the details my udev rule file

ATTRS{serial}=="HNB0981113022756", RUN+="/home/dava/bk.sh"

Its saved as 81-thumdrive.rules.

The file "bk.sh" is executable and works upon double click.

I have restarted udev but i still get nautilus loading the thumb drive to view the files on the drive, no script running...

---

### Post by davavanstone on 2010-07-21
ive added a symlink in the rule file

ATTRS{serial}=="HNB0981113022756", SYMLINK+="davesusb", RUN+="/home/dava/bk.sh"


running this

dava@dava-laptop ~ $ ls /dev/d* -la

i get
lrwxrwxrwx  1 root root      4 2010-07-21 21:20 /dev/davesusb -> sdc1  <<<<<
crw-rw----+ 1 root audio 14, 3 2010-07-21 07:54 /dev/dsp
lrwxrwxrwx  1 root root      3 2010-07-21 07:54 /dev/dvd -> sr0
lrwxrwxrwx  1 root root      3 2010-07-21 07:54 /dev/dvdrw -> sr0


As you can see the udev rule is working, but why is the script not?

---

### Post by beren.olvar on 2010-07-21
does your script start with the #!/bin/bash line?
i think the environment in which scripts are run is pretty basic, so it needs the appropriate initialization of environment.

---

### Post by davavanstone on 2010-07-21
ah ha, cured it!!! thanx for that! i over looked that the second time i did the script as i put firefox in it for simplicity!

Thanx again

---

### Post by davavanstone on 2010-07-22
kinda solved but now it runs 7 times lol

---

### Post by bob_hilton on 2010-07-22
I'm suffering from this problem too - only my script doesn't run.

the symlink shows up fine, and the script runs from the terminal.

anything else this may be?

---

### Post by beren.olvar on 2010-07-22
maybe if you paste the script here we can get a clue about what can be going wrong.

also running 
```

udevadm control --log-priority=debug
```
may give some information

---

### Post by bob_hilton on 2010-07-23
Thanks for showing me udevadm, i was unaware of it.

syslog shows that the script was being run, running the script with banshee gave me a display error, as did zenity. 

I guessed that this may have had somethig to do whith it being run be by the root/system rather that the user so i tried echoing some text to a file. which works fine.

Thanks for the help on this beren.olvar

---

### Post by beren.olvar on 2010-07-23
glad to help :)

@davavanstone
did your problem got solved??

---

### Post by bob_hilton on 2010-07-23
davavanstone, i was also having the same issue with the script running several times. Modifying my rules helped to solve it. 

When i ran:

```
sudo udevadm info --attribute-walk --name /dev/sdb2
```

i get about 7 blocks of info (all headed with their location) ranging from the very bottom of the tree (confusingly shown at the top) moving down to the root/top right at the bottom.

I tried a couple of combinations and personally think its better to take as many options as possible and all from the same block. i just added them one at a time and tested, until the script only ran once.

hope this helps if you've not already sorted it.



on a less related note, i was trying to run a gui app initially  and that needed some extra work to get running (which is why i thought it wasn't running at all to start).

---

