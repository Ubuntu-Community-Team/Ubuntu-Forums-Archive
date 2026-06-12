---
title: "how to fix broken packages?"
date: 2012-06-16
forum: General Help
---

### Post by vikash_chandola on 2012-06-16
I open synaptic;  it doesn't show any message like broken packages but at the time try to install g++ with command ```
 sudo apt-get install g++
``` It shows an error that 
```

.............
.............
   Depends: x11proto-xf86dri-dev but it is not installable
            Depends: x11proto-xf86vidmode-dev but it is not installable
 xserver-xorg-dev : Depends: x11proto-video-dev but it is not installable
                    Depends: x11proto-dri2-dev (>= 2.3) but it is not installable
                    Depends: x11proto-fonts-dev but it is not installable
                    Depends: libxkbfile-dev but it is not installable
                    Depends: libpciaccess-dev but it is not installable
[highlight]E: Unable to correct problems, you have held broken packages.[/highlight]
vikash@vikash-desktop ~ $ 

```
what's happening>???
How to fix it??

---

### Post by kc1di on 2012-06-16
> **vikash_chandola said:**
> I open synaptic;  it doesn't show any message like broken packages but at the time try to install g++ with command ```
 sudo apt-get install g++
``` It shows an error that 
```

.............
.............
   Depends: x11proto-xf86dri-dev but it is not installable
            Depends: x11proto-xf86vidmode-dev but it is not installable
 xserver-xorg-dev : Depends: x11proto-video-dev but it is not installable
                    Depends: x11proto-dri2-dev (>= 2.3) but it is not installable
                    Depends: x11proto-fonts-dev but it is not installable
                    Depends: libxkbfile-dev but it is not installable
                    Depends: libpciaccess-dev but it is not installable
[highlight]E: Unable to correct problems, you have held broken packages.[/highlight]
vikash@vikash-desktop ~ $ 

```
what's happening>???
How to fix it??

in a terminal type this:
```
sudo dpkg --configure -a
sudo apt-get autocleal
```
that should clear the broken packages.

---

### Post by jmfal on 2012-06-16
I had trouble installing G++  from  synaptics also, ended up using codeblocks with emacs.

I googled  "G++ PPA"  there are a few choices, take your pick.

Sometimes fixing broken packages work better from >recovery<  >select fix broken packages > follow prompts (y/n) > may ask to enter command

```
   
sudo dpkg --configure -a sudo apt-get autoclean    
```
try autoclean not autocleal

---

### Post by firekage on 2012-06-16
> **jmfal said:**
> 
Sometimes fixing broken packages work better from >recovery<  >select fix broken packages > follow prompts (y/n) > may ask to enter command
l
In synaptic?

---

### Post by tomatoe on 2012-06-16
Hi!
No, in recovery mode. You can select in GRUB (hold shift while booting pc)

---

