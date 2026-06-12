---
title: "Xorg.conf messed up my Ubuntu"
date: 2009-12-19
forum: General Help
---

### Post by xurma on 2009-12-19
Hello all, I'm a very beginner in Linux and Ubuntu. I actually installed Ubuntu on my computer because a virus had it messed up in Windows XP and I had had enough of formatting my computers.

Ubuntu would be great, but for few days I've been trying to get the default resolution options higher, because the highest I can choose now is 800x600 (And it's annoying me a lot). I did the exactly same thing as the OP in this thread 
[http://ubuntuforums.org/showthread.php?t=1319491](http://ubuntuforums.org/showthread.php?t=1319491)
,except that I use the name of my own graphics card in the template he had linked the others to; I got the same flashing login screen problem.

As I'm also new in Linux, I have no idea where should I have written those commands those few replies showed after about how to get out of the flashing issue. I tried them in terminal and run on my Ubuntu which I can use from the install CD, but nothing happens after I try to use them.

What should I do?

Thanks

---

### Post by xurma on 2009-12-19
bump

---

### Post by xurma on 2009-12-19
bump for answers

---

### Post by xurma on 2009-12-19
another bump... I really need a solution for this

---

### Post by xurma on 2009-12-20
bump...

---

### Post by wojox on 2009-12-20
Reboot and hold down the <shift> key and choose the failsafe ( I forget what it's called ) it's the second option. Then drop into a root shell and run those commands or go into your /etc/X11/ and look for xorg.conf.failsafe and copy it into xorg.conf:

```
cp xorg.conf.failsafe xorg.conf
```

---

### Post by xurma on 2009-12-20
Ok thanks, I was able to go to the root recovery console you mentioned, but there I couldn't go forward...

I first wrote into console: cd /etc/x11   , then I pressed enter. Then I just got "No such file or directory"
Same thing when I wrote: mv xorg.conf xorg.conf.old

After that I tried to write: sudo dpkg-reconfigure -phigh xserver-xorg 
Then after I pressed enter, it took few seconds before I could write something, but I didn't notice any changes.

Also, I searched my x11 folder through and I couldn't find a file named xorg.conf.failsafe.

Also, I'm using my Ubuntu CD now, and when I try editing the xorg.conf file directly with gedit, it doesn't allow me to save the file (For example when I try to erase everything in that file).
I have ubuntu 9.10 and the file wasn't there in the first place, I had to creat the xorg.conf file. I cannot seem to delete it though..

---

### Post by tcchris on 2009-12-20
The xorg.conf file is in /etc/X11 , the X is capitol .
To edit xorg.conf you have to have privileges .
in terminal type gksu gedit /etc/X11/xorg.conf
gksu gives permission , gedit is the editor , caps matter in linux

---

### Post by xurma on 2009-12-20
Ok thanks a lot, I got it to work again.

Now to the resolution issue... I've tried installing two different kinds of video drivers from System > Administration > Hardware drivers, but instead of getting higher resolution choices in display options, there is only 640x480 and 320x240, whereas without drivers applied 800x600 is the maximum... I've tried to search a lot of threads but they have too complicated instructions OR they haven't worked...

---

### Post by xurma on 2009-12-20
bump

---

### Post by tcchris on 2009-12-20
What video card do you have  ?

---

### Post by xurma on 2009-12-20
> **tcchris said:**
> What video card do you have  ?

nVidia Corporation NV34 [GeForce FX 5200] (rev a1), thats what I get when I use the lspci grep VGA command.

---

### Post by Lukas666 on 2009-12-20
> **xurma said:**
> nVidia Corporation NV34 [GeForce FX 5200] (rev a1), thats what I get when I use the lspci grep VGA command.


Could you please go to 

System->Administration->Hardware Drivers

and report what happens? Do you have nvidia drivers installed?

---

### Post by xurma on 2009-12-20
> **Lukas666 said:**
> Could you please go to 

System->Administration->Hardware Drivers

and report what happens? Do you have nvidia drivers installed?

See what I said in the second last post of Page 1, when I installed the drivers, I just got lower resolution, and in addition to that, the screen seemed to be partially away from my monitor, preventing me to see the right corner, for example.

---

### Post by Lukas666 on 2009-12-20
> **xurma said:**
> See what I said in the second last post of Page 1, when I installed the drivers, I just got lower resolution, and in addition to that, the screen seemed to be partially away from my monitor, preventing me to see the right corner, for example.

Sorry, I missed that. Could you post your driver version?  You can find in the NVidia Xserver settings (System->Administration). Also, Are you running 64bit ubuntu? 

You can include your ubuntu information in your forum profile. That's very helpful.

---

### Post by xurma on 2009-12-20
Well when I'm looking at the System -- Administration -- Hardware Drivers window, I see two options (of which neither worked properly):

NVIDIA accelerated graphics driver (Version 173) [Recommended]
NVIDIA accelerated graphics driver (Version 96)

Also, I don't know what it means to have a 64bit Ubuntu nor how to find it out. How do I do that?

---

### Post by Lukas666 on 2009-12-20
> **xurma said:**
> Well when I'm looking at the System -- Administration -- Hardware Drivers window, I see two options (of which neither worked properly):

NVIDIA accelerated graphics driver (Version 173) [Recommended]
NVIDIA accelerated graphics driver (Version 96)

Also, I don't know what it means to have a 64bit Ubuntu nor how to find it out. How do I do that?

Please open Nvidia X server settings (from System->Administration)

and post:

Operating System: (mine: Linux-x86_64)
NVIDIA Driver Version: (mine: 185.18.36)

---

### Post by xurma on 2009-12-20
> **Lukas666 said:**
> Please open Nvidia X server settings (from System->Administration)

and post:

Operating System: (mine: Linux-x86_64)
NVIDIA Driver Version: (mine: 185.18.36)

I can't find such a thing from the list which comes after you look at the System->Administration...

---

### Post by Lukas666 on 2009-12-20
> **xurma said:**
> I can't find such a thing from the list which comes after you look at the System->Administration...

Then you don't have it installed.

Please start  Synaptic Package manager (System->Administration) and search for "nvidia".

Then install the "nvidia-settings" package.

---

### Post by xurma on 2009-12-20
Ok thank you, I have it there now but as I open it I get a message saying: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " What is X?

---

### Post by Lukas666 on 2009-12-20
> **xurma said:**
> Ok thank you, I have it there now but as I open it I get a message saying: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " What is X?

X server is a Linux window management server - don't worry about that.

go to the console and run:

sudo nvidia-xconfig

you'll be prompted for your user password. Once you make any changes save them exit the program and restart Linux. That will also restart the X server.

---

### Post by xurma on 2009-12-20
> **Lukas666 said:**
> X server is a Linux window management server - don't worry about that.

go to the console and run:

sudo nvidia-xconfig

you'll be prompted for your user password. Once you make any changes save them exit the program and restart Linux. That will also restart the X server.

when I go to terminal and type it, I only get "command not found". How do I get to the console if its not terminal?

---

### Post by Lukas666 on 2009-12-20
> **xurma said:**
> when I go to terminal and type it, I only get "command not found". How do I get to the console if its not terminal?

"Console" and "terminal" are the same to me so I don't get your question. Sorry!

You can run it from Applications->Accessories-> Terminal.

Then:

sudo nvidia-xconfig

It should create a new xorg.conf file for you. Then reboot.

---

### Post by xurma on 2009-12-20
> **Lukas666 said:**
> "Console" and "terminal" are the same to me so I don't get your question. Sorry!

You can run it from Applications->Accessories-> Terminal.

Then:

sudo nvidia-xconfig

It should create a new xorg.conf file for you. Then reboot.

Yeah but the thing is that when I type in terminal: sudo nvidia-xconfig , then I get asked a password. But always when Im asked a password in terminal, I cant seem to type anything. And when I typed my password regardless of the field being empty, after that I get message
sudo: nvidia-xconfig: command not found

I also rebooted but I still couldnt use my drivers display settings you mentioned

---

### Post by Lukas666 on 2009-12-20
> **xurma said:**
> Yeah but the thing is that when I type in terminal: sudo nvidia-xconfig , then I get asked a password. But always when Im asked a password in terminal, I cant seem to type anything. And when I typed my password regardless of the field being empty, after that I get message
sudo: nvidia-xconfig: command not found

I also rebooted but I still couldnt use my drivers display settings you mentioned

Looks like you have more packages missing.

Please start  Synaptic Package manager (System->Administration) and search for "nvidia".

This is what I have installed on my machine:

nvidia-173-modaliases                          
nvidia-185-kernel-source                      
nvidia-185-libvdpau                             
nvidia-185-modaliases                          
nvidia-96-modaliases                            
nvidia-common                                   
nvidia-glx-185                          
nvidia-settings


Select them and inatall. Instead of "185" you may find "173", then use those. I think 173 is the family of the most recent drivers for your card. So don't install anything with numbers above 173.

---

### Post by xurma on 2009-12-20
> **Lukas666 said:**
> Looks like you have more packages missing.

Please start  Synaptic Package manager (System->Administration) and search for "nvidia".

This is what I have installed on my machine:

nvidia-173-modaliases                          
nvidia-185-kernel-source                      
nvidia-185-libvdpau                             
nvidia-185-modaliases                          
nvidia-96-modaliases                            
nvidia-common                                   
nvidia-glx-185                          
nvidia-settings


Select them and inatall. Instead of "185" you may find "173", then use those. I think 173 is the family of the most recent drivers for your card. So don't install anything with numbers above 173.


I found all of them except nvidia-173-libvdpau, 185 was there but I didnt install it. Unfortunately I will have to leave now, but Im coming back tomorrow. Thanks a lot for help, lets see if we can get this solved tomorrow.

---

### Post by xurma on 2009-12-21
Ok, I got the information you wanted to see:

Operating System: Linux-x86
NVIDIA Driver Version: 173.14.20

---

### Post by xurma on 2009-12-21
bump

---

### Post by Lukas666 on 2009-12-21
> **xurma said:**
> bump

So can you see the "nvidia-xconfig" command now?

If so, please run the following:

1. nvidia-xconfig -t (post the results here)
2 then: sudo nvidia-xconfig
3. reboot.

---

### Post by Lukas666 on 2009-12-21
> **xurma said:**
> Ok, I got the information you wanted to see:

Operating System: Linux-x86
NVIDIA Driver Version: 173.14.20

Ok, your Linux is 32 bit and  the most recent driver version for your card is 173.14.22.

Your version is ok for now.

---

### Post by xurma on 2009-12-22
> **Lukas666 said:**
> So can you see the "nvidia-xconfig" command now?

If so, please run the following:

1. nvidia-xconfig -t (post the results here)
2 then: sudo nvidia-xconfig
3. reboot.

Ok so my drivers are activated now, and now my resolution is lower again, 640x480 or something. I entered: "sudo nvidia-xconfig -t" in terminal, and what I got:

The only accepted parameters are:
  --output-xconfig=destination    write to a file other than /etc/X11/xorg.conf
  --help            displays this page

---

### Post by xurma on 2009-12-22
Also, here is what my current xorg.conf file contains:

Section "Screen"
    Identifier    "Configured Screen Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option    "NoLogo"    "True"
    Driver    "nvidia"
EndSection

---

### Post by dasunsrule32 on 2009-12-22
do an:

```
lspci |grep 'nvidia'
```What does it return for the make of the card?

EDIT: I saw you have the 5200. I had a similar problem. What I did to resolve the problem, is I entirely removed everything nvidia.

To do this:
```
sudo apt-get remove nvida-*
```Then:
```
sudo apt-cache clean
```Then:
```
sudo apt-get install nvidia-glx-185
```Once that is done, have it auto configure your xorg.conf and see how it works.
```
sudo dpkg-reconfigure nvidia-settings
```Reboot:
```
sudo reboot
```Let's see how that helps.

Here is a copy of my xorg.conf, if you need a reference:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Aug 14 18:33:37 PDT 2009

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "DELL E172FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800"
EndSection

```

Make sure the Section "Device" then Driver is "nvidia" not "nv", this can cause problems.

---

### Post by houseworkshy on 2009-12-22
I had the same problem and following the advice on this page solved it
[http://www.ubuntugeek.com/howto-install-nvidia-190-25-beta-drivers-in-ubuntu-jauntyintrepidhardy.html](http://www.ubuntugeek.com/howto-install-nvidia-190-25-beta-drivers-in-ubuntu-jauntyintrepidhardy.html)
It seems that the restricted nvidia drivers in the repositories were not quite up to scratch.  So the solution was to use the beta which they have just released aa stable.  My nvidia is not the same one as yours, however, there is a lot on the same site if you search for nvidia.

---

### Post by Lukas666 on 2009-12-22
> **xurma said:**
> Also, here is what my current xorg.conf file contains:

Section "Screen"
    Identifier    "Configured Screen Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option    "NoLogo"    "True"
    Driver    "nvidia"
EndSection

Very skimpy! :-)

Before you remove everything as other suggest, can you run 

1. run: sudo nvidia-xconfig
2. If the new file gets created, then reboot
3. Report the changes you see. You may need to go to NVidia configuration panel (System->Administration) and make additional changes (e.g. adjust resolution)


Let me know.

---

