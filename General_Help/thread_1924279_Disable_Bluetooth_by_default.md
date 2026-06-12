---
title: "Disable Bluetooth by default"
date: 2012-02-12
forum: General Help
---

### Post by Captain Apollo on 2012-02-12
I have 11.10 running on a ThinkPad T420s. Every time I boot up, Bluetooth is enabled by default. I dont use it, and its a huge battery drain. Is there any way to set Ubuntu so that Bluetooth is **disabled** by default on boot?

---

### Post by 2F4U on 2012-02-12
In the file /etc/default/bluetooth, set

BLUETOOTH_ENABLED=0

If you are sure you don't need it, you can also remove the service

sudo update-rc.d bluetooth disable

---

### Post by ajgreeny on 2012-02-12
I often wonder how many users in %age terms have ever used bluetooth services on their computer!  I don't think I have ever met anyone, so I begin to think it would make more sense to disable bluetooth by default, but make it very simple to enable it if needed.

Incidentally, I have totally removed bluetooth from my system using synaptic, along with all the libraries etc etc, that it is possible to remove safely, ie, without removing any needed packages.

---

### Post by kolinab on 2012-03-30
Strangely, on my oneiric installation, changing this does NOT seem to disable bluetooth by default on my Lenovo x120e netbook. Any other ideas?

---

### Post by ubuntu27 on 2012-03-30
> **kolinab said:**
> Strangely, on my oneiric installation, changing this does NOT seem to disable bluetooth by default on my Lenovo x120e netbook. Any other ideas?

That's strange. In my Ubuntu Precise, Blutooth is disabled by default. I did not have to do anything.

---

### Post by kolinab on 2012-04-17
I finally got it. On my Thinkpad t60, adding the line:

```
rfkill block bluetooth
```

to /etc/rc.local always works to disable bluetooth on startup (working on 11.10 now).

On my other system, a Thinkpad x120e, neither adding this line, nor employing the solution earlier in this thread worked. I finally found the solution on the Arch Wiki at: [https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e](https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e)

First, I verified that the kernel module 'thinkpad_acpi' was loaded, by looking for it in the output of:

```
lspci
```

thinkpad_acpi indeed WAS listed as a loaded kernel module, so I simply added the line:

```
echo "disable" > /proc/acpi/ibm/bluetooth
``` to /etc/rc.local

On restart, bluetooth is off, but remains available in the notification area if I want to turn it back on.

---

