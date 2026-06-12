---
title: "Ubuntu 12.04 won't shutdown"
date: 2012-05-25
forum: General Help
---

### Post by neutronforrest on 2012-05-25
Hi Forum,

I am having an issue with a fresh install of Ubuntu 12.04.  I purchased a new intel mobo

**[FONT=Arial][SIZE=2]Intel BOXDH77KC LGA 1155 Intel H77 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard[/SIZE][/FONT]**

and an i3-2100 CPU.  When I installed ubuntu everything works great.  However, when I choose shutdown it begins to shutdown.  Then it pauses..the fans stop..very briefly..and it reboots.  It brings up the purple grub/recovery screen.  

I am so frustrated...I have no idea what is causing this.

---

### Post by sikander3786 on 2012-05-25
Nice machine. :)

Out of curiousity, I want you to try the shutdown from a Terminal:

```
sudo shutdown -h now
```

---

### Post by neutronforrest on 2012-05-25
Yep..I tried that.  Same thing.  I did email intel and they do not support linux on that board.  Could this be the issue?

---

### Post by sikander3786 on 2012-05-25
Did you try:

```
sudo shutdown --force
```

It might be an [ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface") problem. Let's make a few changes to Grub and see if things improve. The changes would only be temporary and would be reverted to the default one's on a reboot.

1. Reboot your PC.
2. From the Bios screen, press and hold down <Shift> key for gaining access to the Grub menu.
3. Pointing to the first entry for booting Ubuntu in Grub menu, press 'e' to edit it.
4. Navigate to the end of line which contains 'quiet splash' and add 'acpi=off'.
5. Press <Ctrl> + <X> to continue booting.
6. Once on the desktop, try shutting down your PC from the power menu and if it doesn't work, by using the 2 commands mentioned above.

---

### Post by sikander3786 on 2012-05-25
> **neutronforrest said:**
> Yep..I tried that.  Same thing.  I did email intel and they do not support linux on that board.  Could this be the issue?
Yeah, possibly. But most of the other hardware vendors don't support Linux either and still Linux works great on their products. Linux Kernel 3.4 was released a couple of days ago and if nothing else works, you can try installing that newest Kernel and test it. There is a possibility that it supports your hardware.

---

### Post by neutronforrest on 2012-05-25
Thanks for the detailed response.  I will try this.  I will respond later today and let you know what happens.

---

### Post by nothingspecial on 2012-05-25
Prefix changed from lubuntu to ubuntu.

---

### Post by neutronforrest on 2012-05-25
Hi...I tried sudo shutdown --force and it did not work.  I also changed the grub command to acpi=off.  Again,it still will not shutdown.  I am so frustrated with this.  Does anyone know why it is doing this?

I even installed 11.10 and it does the same thing.

---

### Post by quickridge on 2012-05-27
I ordered that motherboard online with the i7-3770 processor earlier this week and it is scheduled to arrive at my place some time next week. I'm going to slap Fedora 17 on the new system the instant it arrives ;) (I will leave a little room for an ubuntu install as well). I am interested to hear any updates you have in the meantime and will let you know what I find as soon as I get around to it.

Have you tried updating your kernel as sikander3786 suggested. I couldn't find one for kernel 3.4, but there is a PPA for kernel 3.3.6 found here: [https://launchpad.net/~upubuntu-com/+archive/kernel](https://launchpad.net/~upubuntu-com/+archive/kernel)
Instructions on how to use it to update your current kernel are found here: [http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-336-via-ppa.html](http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-336-via-ppa.html)

If you can't solve this problem in a straight forward way you should probably file a bug report with ubuntu. I think a developer might have better luck helping you troubleshoot this problem.

Also, can you get the system to sleep and wake up without any issues? I'm just curious because I rarely plan on actually shutting down or restarting my machine (you might want to use this as a temporary workaround as well).

---

### Post by sikander3786 on 2012-05-27
For installing Linux 3.4 on Ubuntu 12.04, you need to download the below mentioned packages for your respective CPU architecture, to an empty directory, from this page:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)

Packages:

```
linux-headers-3.4.0-xxx-generic_3.4.0-xxx_amd64.deb
linux-headers-3.4.0-xxx_3.4.0-xxx_all.deb
linux-image-3.4.0-xxx-generic_3.4.0-xxx_amd64.deb
```

Assuming that you downloaded those to your ~/Downloads/Kernel directory, the command for installing them would be:

```
cd ~/Downloads/Kernel
sudo dpkg -i *.deb
```

Please remember that I haven't tested it out myself and there is no guarantee that it won't brick your system, and if it would actually solve your original problem.

---

### Post by neutronforrest on 2012-05-27
Hi...so I found a method to shutdown my system.  I go into /etc/default/grub and add acpi=force just after quiet splash.  

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

I then save and do a sudo update-grub.  This works and shuts down the computer.  What is interesting is when I changed 

GRUB_TIMEOUT=10 --> GRUB_TIMEOUT=0

It did not work.  Anyway, I changed that back and my system shuts down.  

I have also been encountering an error from ubuntu.  The error is

"Sorry, Ubuntu has experienced an internal error"

Does anyone know why that is?

---

