---
title: "How do I enable SLI?"
date: 2009-09-28
forum: General Help
---

### Post by Kasinator009 on 2009-09-28
Hi i just got a second nvidia GTS250 video card for my beast of a rig i built. But how Exactly can I enable SLI configuration without losing my GUI? It happened to already and i had to reinstall. running jaunty.

---

### Post by Kasinator009 on 2009-09-28
Should i run envy?

---

### Post by Kasinator009 on 2009-09-28
this still beats vista.

---

### Post by falconindy on 2009-09-28
[http://www.phoronix.com/scan.php?page=article&item=860&num=1](http://www.phoronix.com/scan.php?page=article&item=860&num=1)

This might be of interest to you. Personally, I think the fix is to remove one of your video cards.

---

### Post by Kasinator009 on 2009-09-28
Is sli that much trouble?

---

### Post by falconindy on 2009-09-28
IMO, the extra performance isn't worth the money and excess power consumption. Great, you get double the bandwidth but only 30-40% extra processing power? It's only been recently that you've been able to use SLI with multiple monitors. With the way the graphics market is going these days, you're better off pouring your money into a single high end card than 2 middle of the road cards.

---

### Post by Kasinator009 on 2009-09-28
well after reading this I knew SLI wasn't going to be as huge a difference as say using windows sli. i still could use the power boost. any helpful information would be very much appreciated.

---

### Post by Kasinator009 on 2009-09-28
besides ts already paid for. I would just like to use what i have around me. I am not worried about power consumption, I am worried that I can't enable sli. plain and simple.

---

### Post by Kasinator009 on 2009-09-28
I''m gonna keep lurking in the meantime.

---

### Post by NoaHall on 2009-09-28
Have you installed the driver? If so, run "gksudo nvidia-settings", then you'll see GPU0 and GPU1. If you haven't, System -> Admin -> Hardware Drivers.

---

### Post by Bölvaður on 2009-09-28
I got lost while copy and pasting, there might be some things in wrong order. I urge you to follow the top url and if there are some problems you may gain from our conversation, even though it might be in wrong order, and a little bit confusing.

> **falconindy said:**
> [http://www.phoronix.com/scan.php?page=article&item=860&num=1](http://www.phoronix.com/scan.php?page=article&item=860&num=1)

This might be of interest to you. Personally, I think the fix is to remove one of your video cards.

incorrect the fix is not to remove anything.

A friend of mine had 4 cards running with SLI in ubuntu. There is just some configs that need to be changed to enable it.


This is a log from when I tried to help him via IM
> [COLOR="Sienna"] [http://ubuntuforums.org/showthread.php?t=1043758&highlight=dual+graphic+card]("http://ubuntuforums.org/showthread.php?t=1043758&highlight=dual+graphic+card")

this thread.

scroll down to where linuxNC says SOLVED!!, it is fairly early in the thread


this looks simple enough.[/COLOR]


(paste it into the terminal either by right clicking with mouse or ctrl+shift+v)
[QUOTE]lspci | grep VGA

(example output:
**07**:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GX2 (rev a2)
**0b**:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GX2 (rev a2)

these are 2 graphic cards, notice the bold numbers, btw B is a hex number)

that is, list everything connected via pci and grep (aka filter) VGA

take note which one is the most likely to be the one connected to your monitor and write that number in xorg

again in the terminal (there is a gui way but ye... <edited for the children> it)
sudo nano /etc/X11/xorg.conf

add      ```
BusID          "PCI:7:0:0"
``` like he did in his post but not have 7 but something else



then run the other commands
```

sudo nvidia-xconfig --multigpu=on
sudo nvidia-xconfig --sli=o
```



um lets make a backup before doing anything
let's still say "<deleted for the children> the gui way" as this takes shorter time
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
next

```
gksu gedit /etc/X11/xorg.conf $
```

the dollar sign is not important though...


it's good to have that backup tbh


[COLOR="Sienna"]My friend: so install the driver yer?[/COLOR]
Me: yes
but dont restart
we need xconf to be changed before continuing

[COLOR="Sienna"]My friend: same one   recommended?[/COLOR]
Me: 180

[COLOR="Sienna"]My friend: ok done, installed[/COLOR]

Me:ok no paste this

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_nvidia_backup
```
```
gksu gedit /etc/X11/xorg.conf $
```



can you copy me the last thingy there
something like

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BusID          "PCI:7:0:0"
    VendorName     "NVIDIA Corporation"
EndSection



[COLOR="Sienna"]My Friend:
Section "Screen"
 Identifier "Default Screen"
 Monitor  "Configured Monitor"
 Device  "Configured Video Device"
 DefaultDepth 24
EndSection

Section "Module"
 Load "glx"
EndSection

Section "Device"
 Identifier "Configured Video Device"
 Driver "nvidia"
 Option "NoLogo" "True"
EndSection[/COLOR]


<added>  Change the last bit to this &#8595; </added>

Section "Device"
 Identifier "Device0"  &#8592; &#8592; &#8592; &#8592; NOTICE THIS is not "Configured Video Device"
 Driver "nvidia"
** BusID "PCI:7:0:0"**  &#8592; &#8592; &#8592; &#8592; NOTICE THIS
 Option "NoLogo" "True"
EndSection


```

sudo nvidia-xconfig --multigpu=on
sudo nvidia-xconfig --sli=on/CODE]


and then final backup

[CODE]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_nvidia_final_backup
```


[COLOR="Sienna"]My friend: so done the 3 commands
shall i try the restart?

i think we have graphics drivers[/COLOR]


ME: 

make sure everything is correct
```
glxinfo | grep vendor
glxinfo | grep renderer

```

and also check **System &#8594; Administration &#8594; Nvidia x server settings**
and look at the left side of the screen, does it say GPU 0 and GPU 1 ? If it is GPU 0 only then it failed, if it says both 0 and 1 then what you just did fulfills the definition of a success
[/QUOTE]

---

### Post by Kasinator009 on 2009-09-28
Hold that thought. I attempted another try tweaking Xorg and it cost me. Ill try that idea after I reinstall.

---

### Post by falconindy on 2009-09-28
> **Kasinator009 said:**
> Hold that thought. I attempted another try tweaking Xorg and it cost me. Ill try that idea after I reinstall.
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
The above is a lot faster than reinstalling every time you fubar your xorg config...

> incorrect the fix is not to remove anything.
Sarcasm, friend. Was merely expressing my distaste for SLI.

---

### Post by YaKillaCJ on 2009-09-28
Yea imma try this myself. Thinkin this may be my issue.

---

### Post by Kasinator009 on 2009-09-28
[http://www.youtube.com/watch?v=JEvK4fl1jmQ](http://www.youtube.com/watch?v=JEvK4fl1jmQ) I tried this but xorg didn't show up it was empty.

---

### Post by Kasinator009 on 2009-09-28
Install is almost finished. im gonna brew me a pot of coffee. something tell me this is going to be a long one.

---

### Post by Kasinator009 on 2009-09-28
> **Bölvaður said:**
> I got lost while copy and pasting, there might be some things in wrong order. I urge you to follow the top url and if there are some problems you may gain from our conversation, even though it might be in wrong order, and a little bit confusing.



incorrect the fix is not to remove anything.

A friend of mine had 4 cards running with SLI in ubuntu. There is just some configs that need to be changed to enable it.


This is a log from when I tried to help him via IM
just so I am sure this is AFTER i install the restricted drivers?

---

### Post by Kasinator009 on 2009-09-28
any one know wether or not i follow those instructions after i install restricted drivers?

---

### Post by Kasinator009 on 2009-09-28
anyone please?

---

### Post by Kasinator009 on 2009-09-28
Ok ill take a risk here

---

### Post by YaKillaCJ on 2009-09-28
Just did it. It worked perfect for me and im currently booted in2 Ubuntu.
Kasinator, I can assist ya and walk ya thrue step by step if ya need. PM me your MSN/Yahoo.

---

### Post by YaKillaCJ on 2009-09-28
Hope these examples can help any1. I installed the Drivers and made changes b4 rebooting.

Heres my "lspci | grep VGA" results:

```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

```

Heres my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "MultiGPU" "on"
    Option         "SLI" "on"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by Kasinator009 on 2009-09-28
@.@ Im still going at it

---

### Post by Kasinator009 on 2009-09-28
:guitar:[SIZE=7]YES!!! YES!!! THERE IS A GOD! I GOT IT WORKING! THANKS UBUNTU COMMUNUTY!!:guitar:[/SIZE]

---

### Post by Kasinator009 on 2009-09-28
Uh how do i set the thread to solved?

---

### Post by YaKillaCJ on 2009-09-29
Thank U as well. Ya helped me figure out what was the issue in the first place. I thought nothin bout the Dual Cards. Glad I can be of assistance.

BTW for any other readers. I added the Bus, MultiGPU and SLI manually because wheneva ya use the sudo nvidia-xconfig cammands, it erases the BusID. I also used gedit and not nano for personal preference. If U wanna say print out the options and do strictly in command prompt (what ure likely seein if U rebooted b4 editin the options) then U can use nano just fine.

What ya need to do is run:
```
lspci | grep VGA
```
My results were:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
I have my monitor plugged in2 my top video card PCIe on the board which is 01:00.0.

Next I did the initial auto configurator:
```
sudo nvidia-xconfig
```

**Remember, U should always make a backup b4 ya go edditing xorg.**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then I used to do the editing:
```
sudo gedit /etc/X11/xorg.conf
```
Then added the lines marked in blue in place:
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    [COLOR="DeepSkyBlue"]BusID          "PCI:1:0:0"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    [COLOR="DeepSkyBlue"]Option         "MultiGPU" "on"
    Option         "SLI" "on"[/COLOR]
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

I highly recommend doin this before rebooting, immediately after you install the nVidia Proprietary Drivers. If the first BusID doesnt work, then try the 2nd/3rd and move your cable to the respective card. They do work. This shall fix any issues for ppl who have Dual Cards on there board but doesnt/cant do SLI. All ya do is not add the addition Options and only add the BusID.

Also if ya readin this after U ran in2 the issue, U can do this by doin a Live boot via Ubuntu CD or any linux to make changes to the file. NO Need 2 do a fresh install ^_^

Thanx Bölvaður and Kassinator009 for your help. I recommend changin the title of this to SLI and/or Dual Video cards or somethin like that so ppl dont overlook it.

---

