---
title: "Help installing a driver"
date: 2009-12-12
forum: General Help
---

### Post by PaulStat on 2009-12-12
Right ok I've managed to install the nVidia graphics driver now! Now all that remains is to install the driver for my wifi card, which connects to the motherboard via one of the usb headers.

I've identified the card as being the VIA **[B]VT6656**[/B][B] and the drivers for linux are here: [http://www.viaarena.com/Driver/vt6656_linux_v1.19.zip](http://www.viaarena.com/Driver/vt6656_linux_v1.19.zip)

But I have absolutely no idea how to install them? Could someone give me a step by step of what I need to do?

Thanks,
Paul
[/B]

---

### Post by Sin@Sin-Sacrifice on 2009-12-12
[I guess we could Google that for you...]("http://lmgtfy.com/?q=building+the+vt6656+linux+driver+for+ubuntu")

---

### Post by 3rdalbum on 2009-12-12
1. First we need the build-essential and linux-headers-generic packages. You can install them from Synaptic. Build-essential allows you to compile, linux-headers-generic is necessary to compile kernel modules.

2. Extract the archive.

3. Open a terminal and navigate it into the folder that was just created when you extracted the archive.

Tip: If you don't know how to do this, then in the terminal type:

```
cd
```

leave a space at the end, and drag the folder into the terminal. Now hit Enter.

4. Type:

```
make
sudo make install
```

(Make does the compiling, sudo make install actually installs the software)

**You will need to follow this procedure every time you upgrade your kernel, so keep this information around.**

That's it. And next time try buying a wireless device that is supported out-of-the-box on Ubuntu, they aren't hard to find these days. Avoid anything VIA as they're not open-source-friendly. They didn't even provide a set of instructions for installing this driver.

---

### Post by PaulStat on 2009-12-12
I followed the steps in this link [http://xbmc.org/forum/showpost.php?p=405186&postcount=4](http://xbmc.org/forum/showpost.php?p=405186&postcount=4)

I can't tell if anything is working however. Doing iwconfig says the following

lo        no wireless extensions.

eth0      no wireless extensions.

And now when I reboot it takes quite a while to get to the login screen, any ideas?

Oh also when I do sudo iwlist scan I get the following

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by PaulStat on 2009-12-12
And doing a

```

modprobe -l
```

shows that the module is installed into the linux kernel as it lists it

...
...
kernel/drivers/net/vntwusb.ko

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
Try ```
sudo ifconfig wlan0 up
```

---

