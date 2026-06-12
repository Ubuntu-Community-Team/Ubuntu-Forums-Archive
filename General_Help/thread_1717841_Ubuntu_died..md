---
title: "Ubuntu died."
date: 2011-03-30
forum: General Help
---

### Post by Colo2 on 2011-03-30
Hello

I was wondering if someone could help me.

After tweeking some graphics settings, and replacing some hardware, ubuntu won't boot. Being left in the X session (CTRL + ALT + f7), it's what looks like a log: 

> * Checking battery state...                                   [OK]
* Setting sensors limits                                      [OK]

^ and that's where it hangs.

So I went into ctrl alt f1, and logged in with my user/pass, and did the command: startx

the screen flashes, and brings me back to a failed to open devices report. 
> (EE) Screens found, but none have a usable configuration.

ending on:

> xinit: No such file or firectory (errno 2):  unable to conntact to X server
xinit: No such process (errno 3): Server error.

So I assumed that the problem lies with X server.

So I:

> dpkg-reconfigure xserver-xorg

Rebooted, and exactly the same problem.

I tried re-installing GDM, but turns out that the PC isn't actually online, hence unable to install GDM after uninstallation. So I downloaded the gdm .deb, and tried to install it from a USB flash drive, but I get dependency errors.

I'm at a loss here, I could really use some help, this is the PC that has all my data on it, 450 GB +, I'd love to not have to transfer that over to a new installation!! hehe :P

Thanks

Tom.

---

### Post by Hashiru on 2011-03-30
Maybe you can connect to internet trough the terminal. Once that is done you should be able to reinstall. I did it for arch linux a long time ago, i don't know how to do this in ubuntu.

Maybe this helps searching for a solution.

---

### Post by Colo2 on 2011-03-30
> **Hashiru said:**
> Maybe you can connect to internet trough the terminal. Once that is done you should be able to reinstall. I did it for arch linux a long time ago, i don't know how to do this in ubuntu.

Maybe this helps searching for a solution.

Thanks, I'll see what I can do.

---

### Post by realzippy on 2011-03-30
Why not telling more about:

*After tweeking some graphics settings, and replacing some hardware*

**?**

Edit:
At least you can boot in recovery mode and undo changes;press "shift" during boot,menu appears.

---

### Post by TeoBigusGeekus on 2011-03-30
Before reinstalling, try this:
```
sudo rm /etc/X11/xorg.conf
```
and 
```
sudo reboot
```
If the fault is in the xorg configuration, a new file will be generated, hopefully with functioning results.

---

### Post by Colo2 on 2011-03-30
> **realzippy said:**
> Why not telling more about:

*After tweeking some graphics settings, and replacing some hardware*

**?**

Edit:
At least you can boot in recovery mode and undo changes;press "shift" during boot,menu appears.

> Before reinstalling, try this:
Code:
sudo rm /etc/X11/xorg.conf
and 
Code:
sudo reboot
If the fault is in the xorg configuration, a new file will be generated, hopefully with functioning results.

> Maybe you can connect to internet trough the terminal. Once that is done you should be able to reinstall. I did it for arch linux a long time ago, i don't know how to do this in ubuntu.

Maybe this helps searching for a solution.

Recovery with networking connects me with undesired IP settings which doesnt work on my network

So I opened up the interfaces file, to find it's been wiped.

Consequently the "dpkg" was unable to fix broken packages, as it involves downloading from the net.

And yeah, I've tried deleting the xorg.conf file, no avail.

The hardware changes were: I put a different graphics card in, which has undesired effects, so I took that one out, and put the old one in. I may have messed about with the xorg.conf file whilst the other card was in there tho, but thats nothing dpkg-reconfigure xserver-xorg can't fix... right?

[COLOR="Black"]**Is there any way this can be fixed using my Ubuntu LiveCD? I'm able to configure my network with the live CD in such a way that puts me online :P**[/COLOR]

Tom

---

### Post by conradin on 2011-03-30
Yes, ubuntu live CD!
Whats your hardware btw?
I installed a Nvidia geforce GTX 460 se recently and was in your situation.
I used the live cd, downloaded the installation package I needed, killed the graphical session, installed, then rebooted and I was golden.

---

### Post by Colo2 on 2011-03-30
Hey, thanks for your reply

I' have an old card in this pc, FX 5200 or something

Tom

---

### Post by ajgreeny on 2011-03-30
Incidentally the ```
dpkg-reconfigure xserver-xorg
```command (which should have been run with **sudo**) has not worked for several ubuntu versions as xorg has developed to the point where, in theory, at least, it should never be needed.  

Unfortunately, as you have seen, there are occasions where it would still be useful.

---

### Post by Colo2 on 2011-03-31
conradin's method worked! thank you :)

**EDIT: Still not working.**

---

### Post by Colo2 on 2011-03-31
I don't understand this.

conradin's method worked, if after installing the nvidia drivers, I do: startx, X server fires up, and sends me into my ubuntu desktop. 

**BUT As soon as I reboot, I get **
> Failed to start X server (your graphical interface).

Same problem this guy got back in 2006, but I've tried all ideas posted, nothing works. [http://ubuntuforums.org/showthread.php?t=231811](http://ubuntuforums.org/showthread.php?t=231811)

After that, doesnt work, Until I re-install the driver with commandline, and follow it with startx

What the heck? :S

---

### Post by Colo2 on 2011-03-31
At the end of my wits here. Does anyone know why the heck it's doing this? :( 

I really don't want to have to re-install

---

### Post by jerome1232 on 2011-03-31
Boot into recovery mode, select failsafeX, does that work?


Have you tried reconfigureing xorg? last I checked you had to add a higher priority to the reconfigure to get it to work. If you can't get into failsafeX you can try running these from a recovery mode root prompt, try each one individually and see if one works.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You said you installed nvidia drivers? Perhaps using their configuration utility will help

```
sudo nvidia-xconfig
```

lets us know how it goes, what works and what doesn't.

---

### Post by Colo2 on 2011-03-31
Hello
Thank you for your reply.

I tried both those commands, and then did startx.

I get this:

[IMG]http://i.min.us/jknJDY.jpeg[/IMG]

[IMG]http://i.min.us/jknJDY.jpeg[/IMG]

I'm puzzled about why it works when I startx right after driver install, but not after reboot? :S

---

### Post by rubylaser on 2011-03-31
It looks like your kernel was recently updated, and you need to reconfigure the NVIDIA drivers against it.  Also, what GPU are you using to be running the 173.14.28 drive?  If it's a newer GPU, I'd just grab the latest binary from NVIDIA's website (260.19.44 version), run it, and restart X.

[http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")
download, then make executable and install.

```
sudo -i
chmod +x NVIDIA-Linux-x86_64-260.19.44.run
sh ./NVIDIA-Linux-x86_64-260.19.44.run
```
follow the prompts through and when it's done.
```
exit
startx
```

If that doesn't work, please paste in your /etc/X11/xorg.conf file.

---

### Post by Colo2 on 2011-03-31
Hello.

the .run is what i'm using currently, the one that works with the startx command, but not after reboot. 

The card is ancient. FX 5200 or something. The driver file is called:

NVIDIA-Linux-x86-173.14.28-pkg1.run 

I downloaded it from the nvidia site.

---

### Post by Colo2 on 2011-03-31
OK:

I did exactly what you said rubylaser. Following the installation through etc..

Forgot to mention, theres a message that comes up at the begining, not sure if it's relevant:

> distribution provided pre-install script failed. Install anyway?

I was just hitting yes.

At the end of the installation, it asks me if I want it to update my xorg.conf to use the nvidia driver. I just selected yes.

The install ended, and I did exit, which took the prompt back to default, then I hit start X, bingo, X started, and took me to my ubuntu desktop.

So I restarted the PC, and it loaded ubuntu. (btw, when it loads ubuntu, when the ubuntu logo comes up, and the loading bar. It loads it in a tiny resolution, possibly 600 x 800)

Then it flashes black, and comes up with a blue screen and a grey box in it:

[IMG]http://support.citrix.com/article/html/images/CTX121616-1.gif[/IMG]

Do you want to see my xorg.conf file still?

---

### Post by Colo2 on 2011-03-31
**[SIZE="3"]My xorg.conf[/SIZE]**

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed Sep 29 10:19:47 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by rubylaser on 2011-03-31
Yes I do want to see your xorg.conf file.  And, in light of what you said, you are correct to use the legacy driver.

---

### Post by rubylaser on 2011-03-31
[http://ubuntuforums.org/showthread.php?t=1431440&page=1]("http://ubuntuforums.org/showthread.php?t=1431440&page=1")I don't know what kernel you're using, but noveau may be getting in the way.

---

