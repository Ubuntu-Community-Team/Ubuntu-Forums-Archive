---
title: "Kernel Update"
date: 2009-08-08
forum: General Help
---

### Post by fleamour on 2009-08-08
I have applied all updates but now on booting I have two options:

2.6.24-24

2.6.24-19

Has my kernel updated?  I guess the old one is left in case of any software incompatibility?  Can I get rid of old entry?

---

### Post by drs305 on 2009-08-08
You can see which kernel you are running with System, Administration, System Monitor, System or with:
```

uname -r

```

You can set the one that boots by either editing the menu.lst or using a GUI app called StartUp-Manager that can do it for you. The link is in my signature line under "SUM" - it includes a guide on installation, use and a bit about editing menu.lst manually.

Most users keep at least 2 kernels listed in the menu in case the newer one causes problems.

---

### Post by jbruced on 2009-08-08
You got it right.

Easy way to eliminate the unneeded entries is to get to a terminal.

Save your current configuration 1st by typing:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

then type:

sudo gedit /boot/grub/menu.lst

(that's an L not a one in lst)

remove older kernal entries you don't need, save, and reboot.

GL
Bruce

---

### Post by Crunchy the Headcrab on 2009-08-08
That's good advice.  Does anyone know how to remove the actual kernel though?  For good or ill I like to have control over things like that.

In Fedora I type:
> rpm -q kernelto get a list of the kernels.  Then I type
> rpm -e kernelnameto delete specified kernel.

Is there anything like this for Ubuntu/Debian.  It would be nice to know because I am planning on switching back to Ubuntu with Karmic Koala.

---

### Post by fleamour on 2009-08-08
Thanks.  I must say these forums are extremely well subscribed & friendly.  All my questions answered & loving the whole Ubuntu thing. :D 

Does OS always show a maximum of two kernels?  For example, when it upgrades to next kernel, will it show three entries?

---

### Post by drs305 on 2009-08-08
> **fleamour said:**
> Thanks.  I must say these forums are extremely well subscribed & friendly.  All my questions answered & loving the whole Ubuntu thing. :D 

Does OS always show a maximum of two kernels?  For example, when it upgrades to next kernel, will it show three entries?

No, your menu.lst will continue to grow unless you take steps to limit the displays. You can tweak them with StartUp-Manager. The "SUM" link in my signature line has guides on how to do it.

Crunchy: You remove a kernel and its header via synaptic. It's normally listed under "linux-image-2.6.XX-X" or "linux-image-2.6.XX-X-generic". If you remove a kernel via Synaptic it is automatically removed from the menu.lst

---

### Post by Crunchy the Headcrab on 2009-08-08
Thanks drs305.  I'll remember that.  I didn't even think of the GUI because I've become so attached to Yum (Fedora's apt-get).

---

### Post by drs305 on 2009-08-08
> **Crunchy the Headcrab said:**
> Thanks drs305.  I'll remember that.  I didn't even think of the GUI because I've become so attached to Yum (Fedora's apt-get).

Just to be clear, you can remove them from the command line as well, using "sudo apt-get remove" if you prefer to do it via the command line.  ;-)

---

### Post by Crunchy the Headcrab on 2009-08-08
How do you query to see which kernels are installed (from cli)?

---

### Post by drs305 on 2009-08-08
> How do you query to see which kernels are installed (from cli)?

You can use the following command, although note that the kernel you remove would be "linux-image...", so you would substitute "linux-image" for the "vmlinuz" part of the name.

```
sudo find /boot | grep vmlinuz*
```

---

### Post by Crunchy the Headcrab on 2009-08-08
Thanks again.  I'll get more familiar with it when the next version of Ubuntu comes out.  It might just be easier to use synaptic or whatever package manager they are using (I heard there is a new default for Koala).  Anyway it's nice to be able to do it both ways.

):P

---

