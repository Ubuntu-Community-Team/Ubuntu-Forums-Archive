---
title: "Function (Fn) Keys don't work properly"
date: 2012-03-29
forum: General Help
---

### Post by kpuz on 2012-03-29
Hi,
I am running Xubuntu 11.10 and only my brightness function keys (Fn + up/down) work.  The sound functionality (Fn + left/right) doesn't do anything.  The function keys work perfectly on Ubuntu 11.10 and Linux Mint 12.  Can anyone tell me what I could do to fix this?  What package is used to drive this Fn key functionality (perhaps I could reinstall it). 
I am using a Lenovoo E-350 laptop.  Thanks in advance.

---

### Post by kpuz on 2012-03-31
bump?

---

### Post by 2F4U on 2012-04-01
Here is what I did to get around this for my Logitech keyboard. Open Settings Manager and then Keyboard. Open the tab Application Shortcuts. Click Add to create a new shortcut.
The commands I am using are:
- Lower volume: amixer set Master 5%-
- Raise volume: amixer set Master 5%+
- Mute: amixer set Master toggle

When you click on Add it asks for a command, then enter the amixer command given above. Next it asks for a key, so press the key you want to associate with it.

---

### Post by idoitprone on 2012-04-01
> **kpuz said:**
> Hi,
I am running Xubuntu 11.10 and only my brightness function keys (Fn + up/down) work.  The sound functionality (Fn + left/right) doesn't do anything.  The function keys work perfectly on Ubuntu 11.10 and Linux Mint 12.  Can anyone tell me what I could do to fix this?  What package is used to drive this Fn key functionality (perhaps I could reinstall it). 
I am using a Lenovoo E-350 laptop.  Thanks in advance.

Fn keys are managed by the bios, youe bios most likely have some drivers for linux

this link will give you a explanation
[http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do](http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do)

Remember, be careful, since this is a config file for your bootloader, botching this will only get you annoyance of a live cd rescue
go to 
/etc/grub/default

```
gksudo gedit /etc/grub/default
```At this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
add these few strings
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_osi=Linux **"
```
save 

when your done
```
sudo update-grub
```

---

### Post by brainwash on 2012-04-01
The daemon **xfce4-volumed** should manage the volume up and down keys. Click on the volume indicator on your panel and select the "Master" control.

Don't think that your problem is related to the BIOS, because you are able to adjust the brightness with [fn] + up/down .

---

### Post by idoitprone on 2012-04-01
> **brainwash said:**
> The daemon **xfce4-volumed** should manage the volume up and down keys. Click on the volume indicator on your panel and select the "Master" control.

Don't think that your problem is related to the BIOS, because you are able to adjust the brightness with [fn] + up/down .

i didnt say his bios has a problem, but he need kernel driver

[http://en.wikipedia.org/wiki/Fn_key](http://en.wikipedia.org/wiki/Fn_key)

fn keys are special, the os does not understand the key presses of fn keys. So he needs to add the kernel parameter acpi_osi=Linux. This will probably solve his fn key problem

---

### Post by brainwash on 2012-04-01
[QUOTE=idoitprone]i didnt say his bios has a problem, but he need kernel driver[/QUOTE]

Neither did I...

By setting the kernel parameter *acpi_osi=Linux* you tell the kernel how to respond, if the BIOS asks, which operating system you are running. The BIOS can offer different/new functionality based on the argument string. However, **kpuz** mentioned, that his FN keys work on Ubuntu 11.10 and Linux Mint 12. Also the keys to adjust screen brightness do work running Xubuntu.

So I think, that he should follow my instructions or create new custom keyboard shortcuts.

---

### Post by idoitprone on 2012-04-01
> **brainwash said:**
> Neither did I...

By setting the kernel parameter *acpi_osi=Linux* you tell the kernel how to respond, if the BIOS asks, which operating system you are running. The BIOS can offer different/new functionality based on the argument string. However, **kpuz** mentioned, that his FN keys work on Ubuntu 11.10 and Linux Mint 12. Also the keys to adjust screen brightness do work running Xubuntu.

So I think, that he should follow my instructions or create new custom keyboard shortcuts.

well my eeepc and my acer laptop was is no different situation from the op. Brightness keys work, but the volume keys doesnt. This is something I do not understand. All i knew is that that have to add that kernel parameter to get my volume keys working

---

### Post by kpuz on 2012-04-01
First of all.  Thank you everyone.  
I tried the changing the parameter in the /etc/default/grub file and updating grub but it didn't fix the issue.  Whats also interesting is that in Xubuntu 12.04 beta 2, pressing the Fn + left/right (volume) does initiate the notification bubble with changing sound level but the sound doesn't actually change.

---

