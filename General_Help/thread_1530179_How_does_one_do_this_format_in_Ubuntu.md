---
title: "How does one do this format in Ubuntu?"
date: 2010-07-13
forum: General Help
---

### Post by datdaddy on 2010-07-13
I have a need for a particular kind of formatting for USB devices.
 
I have a plan that works, but I have to boot NimbleX up on a CD and then go through the commands to do it.
 
I'd like to be able to to it in ubuntu.  Does anyone know how to make this (from NimbleX) happen in ubuntu?  Steps follow:
 
[FONT=Calibri][SIZE=3]Plug in the USB device, a window should open choose the do nothing option and close the window.

To format the drive. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]
IMPORTANT – FIND OUT WHAT YOUR EXTERNAL DRIVE IS BEFORE DOING THIS.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]DO NOT JUST BLINDLY PUT IN THE sda1 or sda commands below.  Identify your stick or drive before hand and then use that nomenclature. [/SIZE][/FONT][FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri]Click on the TV screen type icon to open a command shell (Konsole)

Carefully type and enter the following

mkfs.ext3 /dev/[COLOR=red]sda1[/COLOR]

Next step is optional it let's you give the drive a name - the example calls it FoxsatBU

e2lable /dev/[COLOR=red]sda1[/COLOR] FoxsatBU

Now to set the partition type

fdisk /dev/[COLOR=red]sda[/COLOR]

type t and enter

then enter 83 at the prompt

type wq and enter

close the Konsole window

[/FONT]

---

### Post by nothingspecial on 2010-07-13
You need to put a sudo in front of the commands and install e2label

```
sudo apt-get install e2fsprogs
```

---

### Post by sisco311 on 2010-07-13
Or simply use the GUI (System -> Administration -> Disk Utility) to format the partitiona as ext3. ;)

---

### Post by egalvan on 2010-07-13
Or simply use the GUI (System -> Administration -> **Partition Editor**)

and use **gparted** to format the partition  :wink: :wink:


"Copying is the sincerest form of flattery"


of course, using the command line is most educational!

---

### Post by nothingspecial on 2010-07-13
> **datdaddy said:**
> I have a need for a particular kind of formatting for USB devices.
 
  Does anyone know how to make this (from NimbleX) happen in ubuntu? [FONT=Calibri]

[/FONT]

Yeah, but (s)he seemed very specific that it had to be done that way - maybe a script or something :P

---

