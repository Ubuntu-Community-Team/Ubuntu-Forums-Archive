---
title: "Ubuntu hangs on suspend/hibernate screen"
date: 2011-01-12
forum: General Help
---

### Post by Natasha D on 2011-01-12
Ok so I'm still a bit of a Ubuntu n00b and I just installed 10.04 on my new laptop (Asus U35F) and it's working pretty well except for one problem..
Every time the laptop goes to sleep/suspends/hibernates, when I try to resume it again it hangs.
So I end up seeing the screen to re-log in and I can usually move my mouse around and start typing my password in and all of that for maybe a second, but after that it just freezes!

Especially since right now Ubuntu is the only operating system I have running, and since I use this in school and need to conserve battery as much as possible so it stays running through 6 hours of class, I really need to get this fixed up soon.. Any help would be madly appreciated :)

Natasha!

---

### Post by DanneStrat on 2011-01-12
How much RAM do you have and what size is your swap partition?

Have a look at this page

[https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate)

You have a couple of different options to hibernate.

If one doesn't work you can try another.

---

### Post by Natasha D on 2011-01-13
> **DanneStrat said:**
> How much RAM do you have and what size is your swap partition?

Have a look at this page

[https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate)

You have a couple of different options to hibernate.

If one doesn't work you can try another.


It has 4 gigs of RAM and 5 gigs of swap

---

### Post by DanneStrat on 2011-01-13
Ubuntu uses swsusp as default for hibernating

the computer. You can try uswsusp instead.

It's a userspace variant of hibernating.

Open a terminal and type the following:


```
sudo apt-get install uswsusp
```


Now that you have uswsusp installed

you have three choices:


s2disk = Hibernate

s2ram = Suspend

s2both = A combination of suspend and hibernate


To try it out you can open a terminal and type:

```
sudo s2disk
```

If everything works well your computer

should go into hibernate and resume without hanging.

Next thing is to integrate uswsusp with gnome, but you can try 

what i mentioned above and let me know if it works.

---

### Post by Natasha D on 2011-01-13
> **DanneStrat said:**
> Ubuntu uses swsusp as default for hibernating

the computer. You can try uswsusp instead.

It's a userspace variant of hibernating.

Open a terminal and type the following:


```
sudo apt-get install uswsusp
```
Now that you have uswsusp installed

you have three choices:


s2disk = Hibernate

s2ram = Suspend

s2both = A combination of suspend and hibernate


To try it out you can open a terminal and type:

```
sudo s2disk
```If everything works well your computer

should go into hibernate and resume without hanging.

Next thing is to integrate uswsusp with gnome, but you can try 

what i mentioned above and let me know if it works.

(So forgive me if I sound like a complete moron at any time during this post).

hibernate worked I think (Although not as cleanly as the normal default hibernate).. 
But if sudo s2ram was supposed to suspend, it didn't do so!...

natasha@natasha-laptop:~$ sudo s2ram
[sudo] password for natasha: 
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "ASUSTeK Computer Inc.        "
    sys_product  = "U35F"
    sys_version  = "1.0       "
    bios_version = "U35F.201"
See [http://suspend.sf.net/s2ram-support.html](http://suspend.sf.net/s2ram-support.html) for details.

---

### Post by DanneStrat on 2011-01-13
> hibernate worked I think (Although not as cleanly as the normal default hibernate).. 
But if sudo s2ram was supposed to suspend, it didn't do so!...
You could try to do a:

```
sudo s2ram --force
```

---

### Post by Natasha D on 2011-01-13
> **DanneStrat said:**
> You could try to do a:

```
sudo s2ram --force
```


That suspended it, but it hung again!

---

### Post by DanneStrat on 2011-01-13
> **Natasha D said:**
> That suspended it, but it hung again!

You can also try the following.

Copy and paste this in a terminal:

```
sudo -s
echo shutdown > /sys/power/disk
echo disk > /sys/power/state
```

You can then try to hibernate and suspend as

you normally would from your desktop(no terminal)

---

### Post by Natasha D on 2011-01-13
> **DanneStrat said:**
> You can also try the following.

Copy and paste this in a terminal:

```
sudo -s
echo shutdown > /sys/power/disk
echo disk > /sys/power/state
```You can then try to hibernate and suspend as

you normally would from your desktop(no terminal)


ok when I type that into the terminal, it freezes, but then if I click the power off button and turn it back on, it resumes from where it was...
However, even after that suspending still hangs it :(

---

### Post by DanneStrat on 2011-01-13
> **Natasha D said:**
> ok when I type that into the terminal, it freezes, but then if I click the power off button and turn it back on, it resumes from where it was...
However, even after that suspending still hangs it :(

Type this in terminal:

```
sudo -s
echo platform > /sys/power/disk
echo disk > /sys/power/state
```

This will get you back to the default setting again.

I don't know why it's not working.

If someone with a little more knowledge on this could

help it would be great.

---

### Post by Natasha D on 2011-01-13
Ah well, thanks for trying :)
At least I got windows dual booted again, so I guess I'll have to switch back for a while till I can get this figured out :(

---

### Post by Natasha D on 2011-01-17
ok so in case anyone else is having the same problem i just got it working by using the solution I got from: [http://ubuntuforums.org/archive/index.php/t-1444822.html](http://ubuntuforums.org/archive/index.php/t-1444822.html)

In particular (From John Dias and ipsi):

The problem is about the ehci builtin controller and xhci module.
The better solutions is to disable all devices that uses ehci_hcd from  Kernel, and to unload module xhci, before suspend/hibernate. For the  last, you can use the nuage6's solution, but I prefer to use the  "config.d", as I describe in section 2. Another solution is to complete  disable usb support in BIOS, but I guess you don't need to do this.

1. Unbind ehci_hcd from kernel:

First, verify what devices you need to unload from kernel. Simple list  the directory "/sys/bus/pci/drivers/ehci_hcd/" and pick all devices id  that has names like "0000:00:1a.0". You may have more than one device  listed.


# ls /sys/bus/pci/drivers/ehci_hcd/
0000:00:1a.0  bind    new_id     uevent
0000:00:1d.0  module  remove_id  unbind

I picked "0000:00:1a.0" and "0000:00:1d.0".

Because newer version of Ubuntu came with ehci_hcd builtin kernel, you  have to unbind all devices. For this, create a file  "/etc/pm/sleep.d/20_custom-ehci_hcd", with the  following content:

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac

Obs.: For this work for you, you have to substitue "XXXX:XX:XX.X" with your settings.
 
2. Unload modelue xhci (usb3):

Create a file "/etc/pm/config.d/usb3-suspend-workaround", with the  following content:

#File: "/etc/pm/config.d/usb3-suspend-workaround".
SUSPEND_MODULES="xhci"

3. execute the following command:

sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd

---

### Post by rjovec on 2011-05-30
Thank you very much!

That worked for me! Now my computer is not going on profound coma anymore!

See you!

---

### Post by chinna saaeb on 2011-07-20
Well the suggestion works well.
But there is a proble. The usb modem (Huawei EC1262 ) and usb mouse logitech are not detected after waking from hibernation / suspension

---

