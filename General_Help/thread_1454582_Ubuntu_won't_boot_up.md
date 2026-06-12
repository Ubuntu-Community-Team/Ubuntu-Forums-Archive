---
title: "Ubuntu won't boot up"
date: 2010-04-14
forum: General Help
---

### Post by jsel21 on 2010-04-14
I had downloaded ubuntu 9.04 a while ago from this site but couldn't get it to move past the loading screen. I could see the loading bar and logo but it would stay there for hours. Does anyone know what could be wrong?

---

### Post by oleink on 2010-04-14
Could be a bad disc?? try burn the disc image again on a new blank cd

---

### Post by oleink on 2010-04-14
Any news?

---

### Post by jaco223 on 2010-04-14
> **jsel21 said:**
> I had downloaded ubuntu 9.04 a while ago from this site but couldn't get it to move past the loading screen. I could see the loading bar and logo but it would stay there for hours. Does anyone know what could be wrong?

What exactly do you mean when you say it won't move passed the loading screen?
Are you using a livecd? I'm assuming you are. Do you get to the point where you can
choose to try ubuntu without installing, or did you choose the install option?
Is it stalling at that point?

Jaco

---

### Post by jsel21 on 2010-04-15
yes it was an from the iso i downloaded here and i did choose to install it. Today i'm going to redownload it and burn it on a different drive, i will update you guys if it works for me.

---

### Post by jaco223 on 2010-04-15
> **jsel21 said:**
> yes it was an from the iso i downloaded here and i did choose to install it. Today i'm going to redownload it and burn it on a different drive, i will update you guys if it works for me.

Try burning it at like 4x speed. See if that changes anything.
You can also try hitting f6 to turn acpi off, you can do this from the
same screen where you're given the install option.

Jaco

---

### Post by jaco223 on 2010-04-15
> **jsel21 said:**
> yes it was an from the iso i downloaded here and i did choose to install it. Today i'm going to redownload it and burn it on a different drive, i will update you guys if it works for me.

Try burning it at like 4x speed. See if that changes anything.
You can also try hitting f6 to turn acpi off, you can do this from the
same screen where you're given the install option.
Hope all goes well for you.

Jaco

---

### Post by jsel21 on 2010-04-15
Ok i redownloaded and burned it on the slowest setting. the demo works fine and now i want to instal it. Since this is my first time using anything other than windows, im thinking its best that i choose the 'install side be side with windows' option for now. When i clicked 'install side by side with windows', a box came up that said 'any previous changes will have to be written to the disk, this cannot be undone'. What does that mean?

---

### Post by jaco223 on 2010-04-15
> **jsel21 said:**
> Ok i redownloaded and burned it on the slowest setting. the demo works fine and now i want to instal it. Since this is my first time using anything other than windows, im thinking its best that i choose the 'install side be side with windows' option for now. When i clicked 'install side by side with windows', a box came up that said 'any previous changes will have to be written to the disk, this cannot be undone'. What does that mean?

It means it's going to write the change in partitions to disk. You should be ok now,
Did you get that far yesterday? Just be careful when installing the bootloader, Do
you have just one hard drive? if so install GRUB to hd0.
Let me know.

Jaco

---

### Post by jsel21 on 2010-04-15
> **jaco223 said:**
> It means it's going to write the change in partitions to disk. You should be ok now,
Did you get that far yesterday? Just be careful when installing the bootloader, Do
you have just one hard drive? if so install GRUB to hd0.
Let me know.
Jaco

No, ive never gotten this far before. Last time i was also trying to use the demo and it didn't work. Yea i only have one HD.. what is GRUB?

---

### Post by Miljet on 2010-04-15
GRand Unified Boot loader. It is the boot device that lets you choose to either boot into Windows or Ubuntu at startup. GRUB will replace the Windows loader in the Master Boot Record of your hard disk. It should automatically install in the proper place during the Ubuntu install.

---

### Post by jaco223 on 2010-04-15
> **jsel21 said:**
> No, ive never gotten this far before. Last time i was also trying to use the demo and it didn't work. Yea i only have one HD.. what is GRUB?

GRUB is the bootloader that is usually installed so you can choose which OS you
want to boot in to, ubuntu or windows. Have you installed yet? How's it going?

Jaco

---

### Post by toxic9813 on 2010-04-15
"GNU GRUB is a Multiboot boot loader. It was derived from GRUB, the GRand Unified Bootloader, which was originally designed and implemented by Erich Stefan Boleyn. 

Briefly, boot loader is the first software program that runs when a computer starts. It is responsible for loading and transferring control to the operating system kernel software (such as the Hurd or the Linux). The kernel, in turn, initializes the rest of the operating system (e.g. GNU)."

Quoted from the GNU GRUB homepage.

---

### Post by jsel21 on 2010-04-15
Ok, installation went smoothly and i rebooted. On restart, there was nothing that gave me the option to boot into Ubuntu. Do i have to install GRUB seperatly or something?

---

### Post by ed-koala on 2010-04-15
Grub2 is hidden by default on a new 9.10 installation.  If you want to see it, hit shift key when you see grub loading.  If you want it to show all the time, you can edit the /etc/default/grub file and place a # sign (and a space after the #) in front of GRUB_HIDDEN_TIMEOUT=0 and it will show for 10 secs before booting to the default selection.

---

### Post by jsel21 on 2010-04-15
Ubuntu is up and running now, thanks guys. One more thing.. how do i connect to a wireless network? Do i have to reinstall my network card driver?

---

### Post by jaco223 on 2010-04-15
> **jsel21 said:**
> Ubuntu is up and running now, thanks guys. One more thing.. how do i connect to a wireless network? Do i have to reinstall my network card driver?

Go to System>Administration>Hardware Drivers

Check to see if the wireless driver is activated, If not activate it, Restart the computer,
Check the networkmanager applet to see if wireless is detecting any networks, you
may have to setup your connection, You can do this by selecting Create New Wireless
Network from the networkmanager applet menu. 
See if that gets you connected. Let us know.

Jaco

---

### Post by jsel21 on 2010-04-16
Ubuntu recognizes the wireless network, but it can't connect. Everytime i click on the network to connect it waits a little bit, then a dialogue box shows saying that im disconnected from the network....now neither ubuntu or windows will connect.

---

