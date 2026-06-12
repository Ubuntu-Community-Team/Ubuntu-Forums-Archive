---
title: "no display after grub edit"
date: 2011-04-26
forum: General Help
---

### Post by launchy on 2011-04-26
hi,

i installed linux yesterday dual boot win7 but the Fn keys and adjusting the brightness wouldnt work so i tried a few workarounds searches in google. however, when i edited one of the grub lines and when i reboot the system, i see the screen messing up and then goes to black (no display at all). how can i fix this one? :(

---

### Post by idoitprone on 2011-04-26
what did you change in grub.

try to boot to safe mode first and undo you edit.
when your done ```
sudo update-grub
```

If safe mode does not work
When you enter grub press e for edit and try to make your grub entry somewhat similar to the link. Of course, your uuid will be different and you hd0,whatever
Undo those correction, when you boot to ubuntu.
Lastly ```
sudo update-grub
```

[https://help.ubuntu.com/community/Grub2#Creating the Custom Menu](https://help.ubuntu.com/community/Grub2#Creating the Custom Menu)

---

### Post by launchy on 2011-04-26
i edited this
GRUB_CMDLINE_LINUX=”acpi_backlight=vendor”
and this GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash acpi_osi=Linux”

from [http://www.ubuntugeek.com/how-to-fix-function-keys-fn-issue-after-upgrading-to-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-function-keys-fn-issue-after-upgrading-to-ubuntu-10-04lucid.html)

---

### Post by idoitprone on 2011-04-26
i know a little about those modules. try and delete the acpi_backlight=vendor, since you may only need apci_osi=Linux to get those function keys working. I know I had too because before the eeepc_wmi became mature, my eeepc 1005 ha funtion keys did not work. I had to add that line to add the eeepc-laptop module.

---

### Post by launchy on 2011-04-26
the thing is when i added this GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash acpi_osi=Linux” thts when it started not to display anything

btw how do i boot ubuntu to safe mode?

---

### Post by idoitprone on 2011-04-26
> **launchy said:**
> the thing is when i added this GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash acpi_osi=Linux” thts when it started not to display anything

btw how do i boot ubuntu to safe mode?

oh ok, then delete the that grub parameter. Just select the entry right under the default

---

### Post by idoitprone on 2011-04-26
nvm

---

### Post by launchy on 2011-04-26
Cool i can boot into ubuntu now! Time to fix lcd brightness :d thanks so much!

---

### Post by idoitprone on 2011-04-26
np, next time say what you have changed, so it tell other people about your situation better

---

### Post by launchy on 2011-04-27
> **idoitprone said:**
> np, next time say what you have changed, so it tell other people about your situation better

will do! thanks again. and i fixed LCD brightness thru compiz double solved tonight!! :guitar:

---

### Post by gregb49 on 2011-11-17
> **launchy said:**
> Cool i can boot into ubuntu now! Time to fix lcd brightness :d thanks so much!This worked for me to solve a dim screen on the eeepc 1005peb - now running 11.10 Oneiric Ocelot

(from: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Ubuntu_11.04_Natty]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Ubuntu_11.04_Natty"))

> Open a terminal and edit your Grub configuration file:
```
sudo gedit /etc/default/grub
```
And change the option row GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" as follow:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_backlight=vendor splash"
```
Then update Grub installation with the command:
```
sudo update-grub
```
and restart your netbook

Working hotkeys include: wireless toggle, brightness (except F7 to switch off screen), volume.

Neither of the disable touchpad keys work. 

From [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Ubuntu_11.04_Natty](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Ubuntu_11.04_Natty)

---

