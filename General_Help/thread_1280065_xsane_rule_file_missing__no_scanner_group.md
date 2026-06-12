---
title: "xsane rule file missing / no scanner group"
date: 2009-10-01
forum: General Help
---

### Post by hotrod6657 on 2009-10-01
I have my Brother MFC 240c printer/scanner working well.  Problem is that I can only access the scanner as root via:

```
sudo xsane
```

Now, all the tutorials about this say that I should edit the 

/lib/udev/rules.d/50-udev-default.rules" file.

Some of the tutorials list a different numbered file but the idea is the same.

Here's the info from Brother's site:

[http://solutions.brother.com/linux/en_us/instruction_scn1c.html#9]("http://solutions.brother.com/linux/en_us/instruction_scn1c.html#9")

My problem is that in the rules.d folder I only have three files.  10-vboxdrv.rules, 70-persistent-cd.rules, 70-persistent-net.rules, and the readme file.  What do i do?  There are several bug reports about this sort of thing but nothing has a solution.

If there is another way to add the appropriate permissions I'm all ears, I'm just getting tired of xsane yelling at me about how dangerous it is to run as root lol.

Thanks in advance.

hotrod

---

### Post by TopEnder on 2009-10-02
G'Day,  I think you looked a the wrong version of Ubuntu to edit, ie if you are using Ubuntu 8.04 Hardy Heron [I] think the file you should be editing is: 
Ubuntu 8.04/8.04.1, 8.10
    1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
    2. Edit "0664" to "0666" in "USB devices" section.

    Before the edit---------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
    SUBSYSTEM=="usb_device",                MODE="0664"

    After the edit----------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
    SUBSYSTEM=="usb_device",                MODE="0666"

    3. Restart the OS.

---

### Post by hotrod6657 on 2009-10-02
Sorry about that, i need to change my signature, i am using Jaunty.  The problem with all of the suggestions on that site is that I don't have any of the files they want me to edit.  I literally only have the files i listed in my initial post.

---

### Post by Bachstelze on 2009-10-02
Please paste the output of lsusb.

---

### Post by hotrod6657 on 2009-10-02
I'm in a computer lab right now waiting for class to start, when I get back home this evening I'll post that.

---

### Post by hotrod6657 on 2009-10-02
Here is the output of lsusb:

```

Bus 002 Device 004: ID 2040:6513 Hauppauge 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bc7:0008 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 003 Device 003: ID 04f9:01ab Brother Industries, Ltd MFC-240C**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Bus 003 Device 003 is my printer.

---

### Post by TopEnder on 2009-10-03
> **hotrod6657 said:**
> Sorry about that, i need to change my signature, i am using Jaunty.  The problem with all of the suggestions on that site is that I don't have any of the files they want me to edit.  I literally only have the files i listed in my initial post.
Try the following for Jaunty 9.04:

1.In Terminal:   Open to edit:"/lib/udev/rules.d/50-udev-default.rules file by

[COLOR="Blue"]gksudo gedit /lib/udev/rules.d/50-udev-default.rules[/COLOR]  and change the following

Before the edit --------------------------

Code:
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"

into:  After the edit --------------------------

Code:
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="[COLOR="Blue"]0666[/COLOR]"

2.Save file,

3.Restart the system.

Code:

[COLOR="Blue"]sudo /etc/init.d/udev restart[/COLOR]

&#65279;To get the scan-key-tool to start automatically at Ubuntu boot by default.

Install:    sane-utils (if not already installed , it's in Synaptic Package Manager)

Add the brscan-skey command to your startup program.

System -> Preference -> Sessions -> Startup Programs -> New

Enter "[COLOR="Blue"]brscan-skey[/COLOR]" in:
[COLOR="Blue"]Name: [/COLOR]                            and 
[COLOR="Blue"]Command:[/COLOR]
Comment: 	Enter what you want to call your Scanner

Press OK and enable the entry.

---

### Post by hotrod6657 on 2009-10-04
> **TopEnder said:**
> Try the following for Jaunty 9.04:

1.In Terminal:   Open to edit:"/lib/udev/rules.d/50-udev-default.rules file by



What I'm saying is that I don't have any files other than what I mentioned in the first post.  That folder only has the following files:

10-vboxdrv.rules
70-persistent-cd.rules
70-persistent-net.rules
the readme file

I know what I have to do if I had the file I need (I've done it plenty of times), my problem is that the file doesn't exist...  According to my Jaunty install there is no 50-udev-default.rules file, or anything with a similar name.

That's where my problem is coming from.

hotrod

---

### Post by fcorourke on 2009-12-17
Hi  -- for what it is worth I have the same problem. I can not believe that I can just copy the change into a file with that name & it will work. None of my files but 40-permission.rules has anything in it. NO ONE can seem to grasp that :-)  -- Your explanation was clear  -- no one seemed to read :-)  -- just give basic & seem to think the rest of what you are stating is not the problem. I did find about a 100page guide to writing your own rules, but it loks like Windows 7 for me  ---- every  upgrade kills your previous fix  -- as will all upcoming new improved releases. I have spent 10-20 hours& ZERO  --run Ubuntu in a bx in windows:-) You can use Windows to print scan do photo stuff & Ubuntu for safe surfing with no scanning or printing. SAD

    Fred

---

