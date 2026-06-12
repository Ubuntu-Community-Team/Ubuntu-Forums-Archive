---
title: "Karmic a pain to boot up"
date: 2010-02-03
forum: General Help
---

### Post by garfieldwasacat on 2010-02-03
Hi friends,

I'm looking for some assistance with an issue I am having booting up karmic.

I have been using karmic for a while now and since the beginning I have had troubles when booting into it.

I am using grub2 and my Win 7 installation loads fine.

**The issue I am having is when I select karmic from the grub2 menu, I am usually taken to a command prompt login, instead of the GUI login.**

Sometimes restarting once, or 10 times will solve this and it will load the GUI, other times I don't have such luck.

Once loaded, karmic runs fine. I have all updates done as far as I know

I am not sure if this is a graphics card issue or a mounting issue.

Any ideas out there on how to check what is causing this?

Thanks

---

### Post by audiomick on 2010-02-03
Hi.
I doubt it is a graphics issue. More like something is having trouble reading the drive.
Are the Win7 and the Ubuntu installations on the same drive?

What helped me with recurring boot troubles was turning off all the "fast boot" options in BIOS. I can't say if windows is less sensitive than Ubuntu, as the machine is a single boot.

---

### Post by garfieldwasacat on 2010-02-03
Hi there and thanks

Yes, same drive - separate partitions

I will check the bios for anything that looks suspect but I don't recall seeing anything in the past

---

### Post by garfieldwasacat on 2010-02-04
Still having this problem

any other suggestions out there?

---

### Post by timZZ on 2010-02-04
You do not have any screen output?

Can you tell us the visual steps.

I.e. 1. I click 'Ubuntu' 2. I see a loading screen 3. suddenly brought to a prompt.

---

### Post by garfieldwasacat on 2010-02-04
I am brought directly to a command prompt login directly after selecting Ubuntu from the grub menu

It seems fully functional, just no GUI

1. grub menu loads

2. I select ubuntu

3. white ubuntu logo appears then disappears

4. command prompt



Is there any command I can use to run a diagnostic or something?

---

### Post by garfieldwasacat on 2010-02-04
Bump

must be some  way to check whats wrong?

---

### Post by Monotoko on 2010-02-04
if its actually Ubuntu and not BusyBox:

try logging in when the prompt comes up, then type "startx"

---

### Post by Leppie on 2010-02-04
> **garfieldwasacat said:**
> Bump

must be some  way to check whats wrong?
have you checked the logs in /var/log?

---

### Post by garfieldwasacat on 2010-02-05
I tried "startx" but got this error
 
Fatal server error:
No screens found
 
I have not been able to log in to ubuntu tonight due to this problem so I have not checked any logs
 
I also tried
 
"sudo /ect/init.d/gdm start"
 
and the command or file could not be found
 
Any other ideas?

---

### Post by audiomick on 2010-02-05
If you can boot into a live CD, you can use that to check the logs, I think.

---

### Post by running_rabbit07 on 2010-02-05
When something like this starts eating time, I just reinstall Ubuntu. It takes less than an hour to reinstall, do updates, and install all of my programs.

---

### Post by Leppie on 2010-02-05
> **garfieldwasacat said:**
> I have not been able to log in to ubuntu tonight due to this problem so I have not checked any logs
you don't need an x session to view the logs...
 
> **garfieldwasacat said:**
> I also tried
 
"sudo /ect/init.d/gdm start"
 
and the command or file could not be found
this should now be something like this:
```
sudo service gdm start
```

---

### Post by garfieldwasacat on 2010-02-05
I have reinstalled before and this problem does not go away

I am now using a Live CD and am in usr/var

I see a bunch of files and folders, which one is the one I want?

Thanks

---

### Post by Leppie on 2010-02-05
try the "messages" one, if you're in that dir:
```
cat messages | tail
```

---

### Post by garfieldwasacat on 2010-02-05
Thanks for your help Leppie

the messages file is extremely long but here is the last error that I can see

NVRM: RmInitAdapter failed! (0x23:0xffffffff:684)
NVRM: rm_init_adapter(0) failed

from the x0rg.0 file

(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:0:13:0. 
(EE) NVIDIA(0):     Please check your system's kernel log for additional error
(EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) NVIDIA(0):     README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


There is much more but I am not sure what to be looking for

I have tried the latest Nvidia drivers and even the beta but still have this problem

---

### Post by Leppie on 2010-02-05
it looks like your xorg.conf contains settings your nvidia card cannot use.
try renaming it:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```then try rebooting into your normal install.

---

