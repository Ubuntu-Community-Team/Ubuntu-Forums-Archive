---
title: "Nvidia Beta Driver: Resolution can not be saved in xorg File"
date: 2011-01-31
forum: General Help
---

### Post by Tobelli on 2011-01-31
Dear Community,

I have been having this Problem for over 2 month now and I can't seem to find a solution.


I am using 10.10 64bit with a Nvidia GeForce Graphic Card on my Acer 5741G 434 Notebook.

I have always used Compiz and without it I can barely use my Notebook. Apparently I had to install the Nvidia accelerated 3d Drivers (current version) in order to use Compiz.

However I cannot enable the "normal" visual effects (right click on desktop / change bakcground/ visual effects) that are necessary for using compiz.

Also everytime I reboot my resolution goes back to 800x600 although I saved the resolution to 1366. So everytime I start my Notebook I have to go to the Nvidia X server settings and set the resolution to 1366.


What I tried until now:

- I tried to reinstall Ubuntu twice!
- I tried to unistall all nvidia Drivers and install through the terminal using the command "sh" the nvidia drivers i downloaded from their website
- I tried to use the nouveau open source driver


Additional Information:
- when I boot a logo of the nvidia BETA driver appears
- for the past couple days I even experienced another problem: the windows do not have the minimize/close and maximize buttons



I really hope somebody could help me out with my issue. I am even willing to install the System again!

I had nothing but problems with the latest 10.10 ubuntu distribiution.

---

### Post by cwwilson721 on 2011-01-31
The reason you can't save the settings in xorg.conf is because Nvidia Settings, by default, doesn't run as sudo.

Easy fix:

Open a terminal, and type
```
gksudo /usr/bin/nvidia-settings
```Enter the password, adjust to what you want, and now it will save to xorg.conf.

As for the other issue, try searching the forum first. You may be surprised...

---

### Post by Tobelli on 2011-01-31
I wish it was that easy!

Unfortunately I tried that "solution" many times but it did not work. I also edited the xorg File as root and saved it as root but still after every reboot its back to the unwanted resolution.

But thanks anyway... I wonder what I am doing wrong..

---

### Post by cascade9 on 2011-01-31
> **Tobelli said:**
> What I tried until now:

- I tried to reinstall Ubuntu twice!
- I tried to unistall all nvidia Drivers and install through the terminal using the command "sh" the nvidia drivers i downloaded from their website
- I tried to use the nouveau open source driver


Additional Information:
- when I boot a logo of the nvidia BETA driver appears
- for the past couple days I even experienced another problem: the windows do not have the minimize/close and maximize buttons


Did you try the normal way to install the nvida drivers?

System-> administration-> hardware drivers. 

*edit- doing this wont help if you have manually installed drivers 

Beta drivers are far more likely to give you problems.

---

### Post by Tobelli on 2011-01-31
> **cascade9 said:**
> Did you try the normal way to install the nvida drivers?

System-> administration-> hardware drivers. 

*edit- doing this wont help if you have manually installed drivers 

Beta drivers are far more likely to give you problems.

Yes I did. Indeed when I used the normal way of installing hardware drivers Ubuntu installed the Beta Drivers. 
I then installed the normal drivers through synaptic and am now using the nvidia current drivers.

---

### Post by cascade9 on 2011-01-31
> **Tobelli said:**
> Yes I did. Indeed when I used the normal way of installing hardware drivers Ubuntu installed the Beta Drivers. 
I then installed the normal drivers through synaptic and am now using the nvidia current drivers.

The only ways to get beta drivers is with manually installing them, or possibly from a PPA. 

If you did add a PPA, then got the normal 260.xx drivers from synaptic, that could be at least part of your problem.

---

### Post by Tobelli on 2011-01-31
> **cascade9 said:**
> The only ways to get beta drivers is with manually installing them, or possibly from a PPA. 

If you did add a PPA, then got the normal 260.xx drivers from synaptic, that could be at least part of your problem.

It turns out I did not have a PPA of the nvidia drivers. 



Is there a way of making sure to unistall ALL nvidia drivers.
Because I uninstalled every "nvidia" package from Synaptic and installed only the "current" one, but still I am experiencing troubles (can not activate effects).

Thank you

---

### Post by cascade9 on 2011-01-31
sudo apt-get --purge remove nvidia-*

That should do it.

---

### Post by Tobelli on 2011-01-31
> **cascade9 said:**
> sudo apt-get --purge remove nvidia-*

That should do it.

Ok thank you!

And what package from synpatic should I install? Nvidia-current?

---

### Post by cascade9 on 2011-01-31
If you arent using a PPA, System-> administration-> hardware drivers is the best way. 

Not that a PPA is always a problem, or will stop that method working.

---

### Post by realzippy on 2011-01-31
Can you post your nvidia bug report as attachment?
Open terminal,run:
```
sudo nvidia-bug-report.sh
```

..file will be in your /home folder.

---

### Post by Tobelli on 2011-01-31
> **realzippy said:**
> Can you post your nvidia bug report as attachment?
Open terminal,run:
```
sudo nvidia-bug-report.sh
```

..file will be in your /home folder.

Attached you will find the bug report.

I will in the meantime trying to uninstall all nvidia packages and reinstall it through "administration/.."

Thank you

---

### Post by Tobelli on 2011-01-31
> **cascade9 said:**
> If you arent using a PPA, System-> administration-> hardware drivers is the best way. 

Not that a PPA is always a problem, or will stop that method working.

I did unistall all nvidia drivers. 

1.Now if I go to administration / hardware   it just tells me that I have a "Wlan" Driver installed, but does not ask me if I want to install a nvidia driver?

2. In the synaptic paket manager the following packages are installed:
- nouveau firmware
- x-server-xorg
- jockey common
- jockey gtk

Should I unistall them as well?



I am really thankful for your patience and knowledge.

---

### Post by realzippy on 2011-01-31
Your log file:

ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: **Installation has failed.**  



your last attempt to install the driver manually failed,because you had to stop X before running the nvidia.sh file.
Anyway it is better to install the driver like *cascade9* suggested and you meanwhile do.. we will see.

---

### Post by realzippy on 2011-01-31
@cascade9

just wondering about the laptop Acer 5741G 434.
Isn't it an Optimus ?

---

### Post by Tobelli on 2011-01-31
> **realzippy said:**
> Your log file:

ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: **Installation has failed.**  



your last attempt to install the driver manually failed,because you had to stop X before running the nvidia.sh file.
Anyway it is better to install the driver like *cascade9* suggested and you meanwhile do.. we will see.

I am aware of the fact that the last few times I tried to install it manually the isntallation did fail, but I was able to install it through synaptic.

Unfortunately I am not able to install the drivers like cascade9 suggested since as I go to the Administration/drivers  I am not aksed if I want to install a new driver?!

What shall I do?

---

### Post by Tobelli on 2011-01-31
> **realzippy said:**
> @cascade9

just wondering about the laptop Acer 5741G 434.
Isn't it an Optimus ?

The laptop I own is an Aspire.

---

### Post by cascade9 on 2011-01-31
> **realzippy said:**
> @cascade9

just wondering about the laptop Acer 5741G 434.
Isn't it an Optimus ?

According to some german forum/tech site I just looked at, its not optimus, the core iX video is disabled.  


*edit-  link removed because it wasnt playing very nicely. 
__
But the full number for that model they were talkinmg about is "Aspire 5741G-434G64BN" and the last few numbers (G6BN) could make a difference. 

@ Tobelli- nVidia 'optimus' is a system developed by nvidia. Its meant to lengthen the battery life, but its got no support at all under linux, and has causde people all sorts of problems with the nvidia drivers. 

Since you only managed to install the dirvers with synaptic, and there is nothing when you try administation-> etc etc, there is something going wrong. 

Could you please post the entire output of-

sudo lshw -C video

---

### Post by Tobelli on 2011-01-31
Oh I understand, thanks for clearing that up.

Here is the outcome of **sudo lshw -C video**:


```
 *-display               
       description: VGA compatible controller
       product: GT216 [GeForce GT 320M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:b2000000-b2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128) memory:b3080000-b30fffff

```

---

### Post by realzippy on 2011-01-31
Has your "System/Administration/Hardwaredrivers" (jockey) ever
offered any NVIDIA drivers (when it was fresh installed and updated) ?

---

### Post by Tobelli on 2011-02-07
Status Quo:

Right now when I start my Notebook a *nvidia beta driver* logo appears.
After logging in I have to open the *nvidia x server settings* and change the resolution to 1366.
Then I have to right click on the desktop /visual effects and click on the normal  option. Then ubuntu tells me "not possible to activate *normal effects*" but the window buttons (close/minimize/maximize) appear.



As far as I remember the System/Administration/Hardwaredrivers   has never offered to install any drivers.
But now I do have* nvidia current*   installed although the Nvidia beta  splash screen still appears at the boot.

---

### Post by realzippy on 2011-02-07
Please post your xorg.conf.
Which nvidia driver version according to nvidia-settings is now running?

---

### Post by Tobelli on 2011-02-09
> **realzippy said:**
> Please post your xorg.conf.
Which nvidia driver version according to nvidia-settings is now running?

According to my Nvidia-settings I have the following version installed:
**Nvidia Driver Version: 260.19.06**
[B]Server Version Number: 11.0
Server Vendor String: The X.Org Foundation
Server Vendor Version: 1.9.0 (10900000)
NV-CONTROL Version: 1.24[/B]




Is it possible that my issue has something to do with Compiz? Because I can start Compiz but if I click any of the options (general settings etc) there is no reaction.

---

### Post by realzippy on 2011-02-09
*Is it possible that my issue has something to do with Compiz?*

Maybe;you could reinstall it (also remove hidden config files!),
but,I have asked you already,
can you post your xorg.conf's content?
(it is in /etc/X11 )

---

### Post by Tobelli on 2011-02-10
> **realzippy said:**
> *Is it possible that my issue has something to do with Compiz?*

Maybe;you could reinstall it (also remove hidden config files!),
but,I have asked you already,
can you post your xorg.conf's content?
(it is in /etc/X11 )


Sorry! I meant you wanted the xorg infos.
Here you go:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LGD LP156WH2-TLE1"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 320M"
EndSection

Section "Screen"

# Removed Option "metamodes" "1366x768_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1366x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by dino99 on 2011-02-10
try without xorg.conf as now the kernel directly deal with X, so weird/old xorg.conf often conflict with kernel. Either rename or remove it:

sudo rm /etc/X11/xorg.conf

---

### Post by realzippy on 2011-02-10
> **dino99 said:**
> try without xorg.conf as now the kernel directly deal with X, so weird/old xorg.conf often conflict with kernel. Either rename or remove it:

sudo rm /etc/X11/xorg.conf

No.
malicious command....do **NOT** run this.
Nvidia driver needs an xorg.conf.....only the free drivers,set up by KMS, can run without.

---

### Post by realzippy on 2011-02-10
> **Tobelli said:**
> Sorry! I meant you wanted the xorg infos.
Here you go:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LGD LP156WH2-TLE1"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 320M"
EndSection

Section "Screen"

# Removed Option "metamodes" "1366x768_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1366x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The file looks fine.Please create again a nvidia-bug-report,
the last one was without running nvidia-drivers;so we might now get a clue why the resolution is not set during boot..

---

### Post by tredegar on 2011-02-10
If this is driving you *crazy*, there may be an easy solution.

Install the NVIDIA driver, any way you like, and don't worry too much about the resolution it chooses.

Run **nvidia-settings**
Set your resolution, brightness, to whatever to what you like.
At the bottom of the left pane is "nvidia-settings Configuration". Click it.
Choose "Save current configuration".

The configuration will be saved.
Now write a little script:```

#!/bin/bash
nvidia-settings -l
```
Save it as **.fix-nvidia** in your home directory
Make it executable: ```
chmod +x ~/.fix-nvidia
```

Now make an entry in the Startup Applications thing:
**Add** where```
Name = FixNVIDIA
Command = ~/.fix-nvidia
Comment = Load my default nvidia settings
```

Click Save.

Next time you login, things should be set up correctly.

---

### Post by realzippy on 2011-02-10
> **tredegar said:**
> If this is driving you *crazy*, there may be an easy solution.

Install the NVIDIA driver, any way you like, and don't worry too much about the resolution it chooses.

Run **nvidia-settings**
Set your resolution, brightness, to whatever to what you like.
At the bottom of the left pane is "nvidia-settings Configuration". Click it.
Choose "Save current configuration".

The configuration will be saved.
Now write a little script:```

#!/bin/bash
nvidia-settings -l
```
Save it as **.fix-nvidia** in your home directory
Make it executable: ```
chmod +x ~/.fix-nvidia
```

Now make an entry in the Startup Applications thing:
**Add** where```
Name = FixNVIDIA
Command = ~/.fix-nvidia
Comment = Load my default nvidia settings
```

Click Save.

Next time you login, things should be set up correctly.

Ok,but no need for a script.
Just add

nvidia-settings -l

to StartupApplications
(as command;name it as you want)

---

### Post by Tobelli on 2011-02-11
Too late "Unfortunately" I did run the command 

sudo rm /etc/X11/xorg.conf

which I was supposed not to run.
However now it works! After rebooting my Notebook the systems starts with exactly the resolution I like.

However the one issue remains:

I still can not activate compiz?



@Realzippy: I will gladly file a bug report however I do not what command I should run in the terminal. Would you be so kind to tell me? Thanks

---

### Post by Tobelli on 2011-02-11
So apparently I can not activate Compiz because I do not have the appropriate drivers.

**A little summary:**
under System/additional drivers  I have the following installed:

- Nvidia Current
The binary driver provide optimized hardware acceleration of OpenGLapplications via a direct-rendering X Server. AGP, PCIe, SLI, TV-outand flat panel displays are also supported.

This package also includes the source for building the kernel modulerequired by the Xorg driver, and provides NVIDIA's implementation ofthe Video Decode and presentation API. The latter enables accelerationfor NVIDIA 8 and later series cards for h264 video.

GPUs such as GeForce series 6 or newer are supported.

See /usr/share/doc/nvidia-current/README.txt.gz for a complete listof supported GPUs and PCIIDs

If I go into Ubuntu software center I have the following installed:

- Additional Driver Jockey-gtk 0.5.10-0ubuntu5.2 (jockey-gtk)

---

### Post by realzippy on 2011-02-11
Open
nvidia-settings
Since you removed the xorg.conf file,the nvidia driver still is installed,but not in use.
Can you confirm this before we go on?

---

### Post by Tobelli on 2011-02-21
> **realzippy said:**
> Open
nvidia-settings
Since you removed the xorg.conf file,the nvidia driver still is installed,but not in use.
Can you confirm this before we go on?

I can confirm that. 
When I open the nvidia x server settings the following message appears:

"You do not appear to be using the nvidia x driver. "

---

### Post by realzippy on 2011-02-21
So recreate a xorg.conf...
open terminal,type:

```
sudo nvidia-xconfig
```

reboot or restart X server...
...nvidia driver in use then ?

---

### Post by Tobelli on 2011-02-21
> **realzippy said:**
> So recreate a xorg.conf...
open terminal,type:

```
sudo nvidia-xconfig
```

reboot or restart X server...
...nvidia driver in use then ?

I typed in the command and the terminal told me that I created a xorg file.
However when I now start the nvidia-server-settings the same error message as before appears.

---

### Post by realzippy on 2011-02-21
..can you post the xorg.conf  ?

---

### Post by Tobelli on 2011-02-21
Unfortunately after I rebooted the system ubuntu dropeed to a shell and I had to reinstall the nvidia drivers manually from the shell.

After I did that and I logged in the resolution was the wrong one.
I reentered the command you asked "sudo nvidia-settings" and created a xorg file.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.36  (buildmeister@swio-display-x86-rhel47-01.nvidia.com)  Tue Jan 18 17:15:10 PST 2011

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.36  (buildmeister@swio-display-x86-rhel47-01.nvidia.com)  Tue Jan 18 17:15:22 PST 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    ModelName      "LGD LP156WH2-TLE1"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 320M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1366x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Isn't it possible to just reinstall Ubuntu from scratch and delete every folder from .home that I do not need and start again? Because this issue is bothering me quite a lot actually!

thank you very much

---

### Post by realzippy on 2011-02-21
...did 10.04 LTS run fine?
Can you test Forlong's script "[compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check")" and post it's output?

---

### Post by Tobelli on 2011-02-22
> **realzippy said:**
> ...did 10.04 LTS run fine?
Can you test Forlong's script "[compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check")" and post it's output?

Yes, 10.04 ran perfectly!

Here is the output of compiz-check:

```

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GT216 [GeForce GT 320M] (rev a2)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

 The nv driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

```

Should I try to reinstall 10.4 LTS?

---

### Post by realzippy on 2011-02-22
As you can see,the nvidia driver is not installed.
Not even the free nouveau driver is in use;you run the rudimentary
nv driver.
...you blacklisted nouveau during an manual nvidia installation attempt?
...System/Administration/Hardware drivers shows nvidia-current as installed
   & nvidia-settings does not complain about "driver not using"???!

Set up a dualboot with 10.04 if it runs fine...so you have a running
system,anyway 10.04 is LTS version,so it is a good idea to keep it,
and you can still try to fix 10.10.

---

### Post by Tobelli on 2011-02-23
> **realzippy said:**
> As you can see,the nvidia driver is not installed.
Not even the free nouveau driver is in use;you run the rudimentary
nv driver.
...you blacklisted nouveau during an manual nvidia installation attempt?
...System/Administration/Hardware drivers shows nvidia-current as installed
   & nvidia-settings does not complain about "driver not using"???!

Set up a dualboot with 10.04 if it runs fine...so you have a running
system,anyway 10.04 is LTS version,so it is a good idea to keep it,
and you can still try to fix 10.10.

Unfortunately I did not see that the Nvidia is not installed, it is very probable that I did blacklist the drivers.

I would prefer to try to fix 10.10 if there is any way?
How can I do this?

Otherwhise I am just going to install 10.04. Do you think that If I install 10.04 I wont have the same issues as I am experiencing with 10.10?

Man I really loved ubuntu until 10.10 came out!

---

### Post by realzippy on 2011-02-23
...fix 10.10  :

Make a fresh install,do **not** set your resolution,then run
```
sudo apt-get update
sudo apt-get upgrade
```

Reboot,then install nvidia-current in System/Administration/Drivers,reboot.
Then we know your system status...


[I]Do you think that If I install 10.04 I wont have the same issues as I am experiencing with 10.10?
[/I]
..well,you said it ran fine....??  (..*Yes, 10.04 ran perfectly!*)

---

### Post by Tobelli on 2011-02-23
> **realzippy said:**
> ...fix 10.10  :

Make a fresh install,do **not** set your resolution,then run
```
sudo apt-get update
sudo apt-get upgrade
```

Reboot,then install nvidia-current in System/Administration/Drivers,reboot.
Then we know your system status...


[I]Do you think that If I install 10.04 I wont have the same issues as I am experiencing with 10.10?
[/I]
..well,you said it ran fine....??  (..*Yes, 10.04 ran perfectly!*)


Thank you very much indeed! 
I will try to apply your suggestion and let you know how it works.

I asked if with a fres install of 10.4 will work because I fear that my issue has something to do with the configuration files stored in my home folder.

Kindest regards

Tobelli

---

