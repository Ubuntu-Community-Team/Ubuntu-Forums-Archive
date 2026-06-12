---
title: "Laptop heating up more than it used to"
date: 2011-07-26
forum: General Help
---

### Post by Condenzationator on 2011-07-26
My laptop (HP ProBook 4710s) has been running very hot since I installed Ubuntu about a week ago. Is this a driver issue? I can hear the fan running, so I know it's not broken/malfunctioning, but regardless it heats up till it's almost unbearable. Any ideas?

Thanks!

---

### Post by el_koraco on 2011-07-26
a) do you have an ATI graphics card? 
b) did you install the driver for it?

---

### Post by Condenzationator on 2011-07-26
Forgot to list that! My apologies.

Yes, I do have an ATI graphics card.
No, I have not installed any drivers, since the last time I installed the (proprietary) drivers, it killed my OS.

Thanks for the quick response!

---

### Post by Condenzationator on 2011-07-26
I did find this for the ATI drivers:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

but will it kill my OS again? It looks like it's the same one that auto-installed
when I had installed Ubuntu the first time. If it fails and the drivers don't work,
is there a way to recover without having to reinstall/lose all my data?

---

### Post by Haneef Mubarak on 2011-07-26
Actually, there is.

**Backup Hard Drive:**
Get a backup hard drive compatible with Linux, and backup your laptop. Then try the driver, if it doesn't work and it kills your system, reinstall Ubuntu and recover your data from your backup hard drive. 

**Normal External Hard Drive:**
Alternatively, you could just an external Linux-compatible hard drive and copy your data to that. Then, is you need to reinstall Ubuntu again, you can just copy your data from your hard drive back to your laptop.

Hope this helps!

---

### Post by Condenzationator on 2011-07-26
I'd still have to reinstall if I did it that way, but you are right, that looks like my only option. I've actually been backing it all up since my last post, just about done. :)

Thank you for your input! :D

---

### Post by Theredbaron1834 on 2011-07-26
Or you could install to a SD card/flash drive/ext drive, and try it out. Then if it works, it works and you can do it to your real install, if not, well, no harm no foul.

---

### Post by Condenzationator on 2011-07-26
That sounds like a good idea too, but I don't have a spare sd/flash drive, and the only ext hdd that I have is for backups. =/

But thanks! :)

---

### Post by Theredbaron1834 on 2011-07-26
Eh, well, then, you can repartition your disk from the live, it will take a while, depending on the size of your drive, and how much is used. The min you need to install is 4 gb, so as long as you have that much free space, you can do that too. And then install to the new partition. You then can boot to a second install of ubuntu to check it out, while keeping your present.

Though, really, it doesn't matter too much, since even on my slow as sin lappy, it installs in less then 40 min. So no matter what, you lose just a few hours total.

---

### Post by el_koraco on 2011-07-26
Before you try the ATI driver, if you're afraid of it, try this. 

ALT + F2, enter ```
gksudo nautilus
```

Navigate to File System - etc - X11

Once you're in that folder, create a file named xorg.conf, and paste this into it

```
Section "Device"
        Identifier  "Videocard0"
        Driver      "radeon"
        Option "ClockGating"       "true"
        Option "ForceLowPowerMode"
        Option "DynamicPM"         "true"
EndSection
```

Save and reboot. See if it helps any, but really, the open source drivers suck at power management.

---

### Post by el_koraco on 2011-07-26
Btw, what is your card? 

Type ```
lspci | grep VGA
```

in a Terminal Window.

---

### Post by Condenzationator on 2011-07-26
[QUOTE=Theredbaron1834]Eh, well, then, you can repartition your disk from the live, it will  take a while, depending on the size of your drive, and how much is used.  The min you need to install is 4 gb, so as long as you have that much  free space, you can do that too. And then install to the new partition.  You then can boot to a second install of ubuntu to check it out, while  keeping your present.

Though, really, it doesn't matter too much, since even on my slow as sin  lappy, it installs in less then 40 min. So no matter what, you lose  just a few hours total.[/QUOTE]

I went ahead and just installed the driver, so far so good. Thanks for the tips though. :)

[QUOTE=el_koraco]Before you try the ATI driver, if you're afraid of it, try this. 

ALT + F2, enter      Code:
     gksudo nautilus 
Navigate to File System - etc - X11

Once you're in that folder, create a file named xorg.conf, and paste this into it

     Code:
     Section "Device"         Identifier  "Videocard0"         Driver      "radeon"         Option "ClockGating"       "true"         Option "ForceLowPowerMode"         Option "DynamicPM"         "true" EndSection 
Save and reboot. See if it helps any, but really, the open source drivers suck at power management.[/QUOTE]

Wish I'd known that sooner, it would've been nice to try. :o
I did install it anyway, so far it's not running so hot/high. :)

[QUOTE=el_koraco]Btw, what is your card? 

Type      Code:
     lspci | grep VGA 
in a Terminal Window.     [/QUOTE]

My card is an ATI Mobility Radeon HD 4330

Here's the results though:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
```Thanks again to all of you who have responded! I really do appreciate it. :D

I'll try to post again here in another hour or two, I'll be able to spot differences better then (since it'll be running longer). :)

---

### Post by Condenzationator on 2011-07-26
Well, the computer just crashed, it's still reaching the high heats. The driver installed properly from what I could tell, so I'm not sure what the issue is now.

Any ideas? :)

---

### Post by el_koraco on 2011-07-27
I'm surprised. The only thing I can think of is that your laptop has power management setting tied to the Windows PM system in Windows. Either that, or the driver didn't install. 

First, type ```
lspci -k
``` in the terminal window and look for the "VGA" section. If the driver is installed, you'll see a kernel driver in use=fglrx line. If it's not installed, we'll try to improve the install process. 

If it is installed, you can try this. 

```
gksudo gedit /etc/default/grub

```

And add the line acpi_osi=\\\"Linux\\\""

to GRUB_CMDLINE_LINUX_DEFAULT line, after "quiet splash. Then do a 

```
sudo update-grub

```
reboot, and see is the issue persists.

---

### Post by hawthornso23 on 2011-07-27
Try adding pcie_aspm=force to your /etc/default/grub. For example as follows.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"
```

Then run sudo update-grub and reboot.

This fixes the recent power regressions in the kernel and can make a huge difference to battery life. Be warned however that some older hardware that doesn't deal with aspm properly may lock up with this boot parameter. But if your hardware can handle aspm turning it on makes a huge difference.

---

### Post by Condenzationator on 2011-07-27
[QUOTE=el_koraco]I'm surprised. The only thing I can think of is that your laptop has  power management setting tied to the Windows PM system in Windows.  Either that, or the driver didn't install. 

First, type      Code:
     lspci -k 
 in the terminal window and look for the "VGA" section. If the  driver is installed, you'll see a kernel driver in use=fglrx line. If  it's not installed, we'll try to improve the install process. [/QUOTE]

First of all, thank you very much for posting back! :)
Alright, it does look like it has that line, here is the VGA part of the output though:

```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
    Subsystem: Hewlett-Packard Company Device 3074
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
```[QUOTE=el_koraco]If it is installed, you can try this. 

     Code:
     gksudo gedit /etc/default/grub 
And add the line acpi_osi=\\\"Linux\\\""

to GRUB_CMDLINE_LINUX_DEFAULT line, after "quiet splash. Then do a 

     Code:
     sudo update-grub 
reboot, and see is the issue persists.     [/QUOTE]

I tried to update after changing the file, but it returned this:

```
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
```Since I don't know the exact issues (other than a syntax error), I changed the line back to how it was before. ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```[QUOTE=hawthornso23]Try adding pcie_aspm=force to your /etc/default/grub. For example as follows.

     Code:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force" 
Then run sudo update-grub and reboot.

This fixes the recent power regressions in the kernel and can make a  huge difference to battery life. Be warned however that some older  hardware that doesn't deal with aspm properly may lock up with this boot  parameter. But if your hardware can handle aspm turning it on makes a  huge difference.     [/QUOTE]

Thanks for posting this!
I'm going to wait to try it until I've finished the other though.
But what is the differene between your code and the one el_koraco posted? Or what does it do differently I should say?

Thank you again to y'all who've taken the time to respond, I would really like to keep Ubuntu on, and this is the only block that it's got right now. Also, I should also mention that it is the only OS installed, it is not a dualboot. :)

Edit:
Forgot to note, most of the flash apps that run go quite slow, especially those that are highly graphical.

---

### Post by vahnx on 2011-07-27
I recommend keeping an eye on [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/488152](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/488152) until someone reports success. For now I suggest staying away from Ubuntu/Linux on that machine to avoid damage.

---

### Post by Condenzationator on 2011-07-27
[QUOTE=vahnx]I recommend keeping an eye on [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/488152]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/488152") until someone reports success. For now I suggest staying away from Ubuntu/Linux on that machine to avoid damage. 	[/QUOTE]

Oh, that's actually rather disappointing...
Well, I'm going to wait for some replies to my last post before I go back to XP, but thank you very much for that link! If all else fails, I'll be following your advice most assuredly! I do hope the fixes will be able to be released soon, but I understand that there are probably more important things to be done. :)

Thanks again!

---

### Post by el_koraco on 2011-07-27
> **Condenzationator said:**
> 
```
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
```Since I don't know the exact issues (other than a syntax error), I changed the line back to how it was before. ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```


Maybe we had one quote mark too many. 

The line should look like this

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

```

then sudo update-grub

If it doesn't work, try the other option. If that doesn't work either, just go with XP or another Linux distro.

---

### Post by Condenzationator on 2011-07-27
[QUOTE=el_koraco]Maybe we had one quote mark too many. 

The line should look like this

 	Code:
 	GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\"" 
then sudo update-grub

If it doesn't work, try the other option. If that doesn't work either, just go with XP or another Linux distro.[/QUOTE]

Alright, that's all done, updated and rebooted too.
My computer won't shut down now unless I hold the button down though.
I'm going to leave it on for an hour or two and check again for heating, then I'll post an update.

Thanks again! :)

---

### Post by Condenzationator on 2011-07-27
Alright, an hour later, and it's pretty hot. I'm going to try the other code and let it rest, then I'll post again.
If it doesn't work, I'll have to switch back to XP until the bugfix is done. :(

But thank you everyone (especially el_koraco!) for your help, of which I appreciate very much! :D

---

### Post by Condenzationator on 2011-07-27
Alright, well, no change, sadly. :(

It looks like I'll be back to XP, at least for the time being, till the bugfix is done.

But regardless of that, thank you again to every one who has posted here and given me (and others, hopefully) some tips and help in fixing this issue! Without your help, I might still be using Ubuntu till my GPU overheats and melts something. :o

I'm going to mark this solved, since it does look like the problem is the bug, and my point here was to find the issue, and possibly, a solution that allowed me to still use Ubuntu. Regardless that I cannot, it was very helpful and I can't say thank you enough! :)

---

### Post by el_koraco on 2011-07-27
Sorry it didn't work out. Sometimes it's just hardware inconsistencies. It might be due to a bug in the later versions of the kernel. You can try to use an older kernel on Ubuntu, or install a distro with older kernel versions, like Debian, Crunchbang, Scientific Linux.

---

