---
title: "Can't get past the grub on install"
date: 2011-08-29
forum: General Help
---

### Post by jmsykes15 on 2011-08-29
1.I have downloaded the wubi onto my computer. 
2.I installed it.  
3.After restarting the computer it gives the option to use         windows 7 or ubuntu. 
4.I click ubuntu.  
5.It takes me to a screen that has 3 options. 
6.One is the ubuntu load(I believe) one is the safe mode(I believe) and the other says to go back to the windows 7 and ubuntu boot screen.  
7.When I click either of the ubuntu load or safe mode screens.  
8.It takes me to a black screen where I can here a drum but nothing on the screen.

Computer Specs:
Computer: Acer Aspire 5734z-4836
Processor: Pentium(R) Duel-Core CPU T4500 @ 2.30GHz
Ram: 3 gigs
System Type: 64-bit OS Windows 7 Home Premium
Intel GMA 4500m
250 GB HDD
Acer Nplify 802.11b/g/n

---

### Post by bcbc on 2011-08-29
[https://bugs.launchpad.net/null/+bug/779166](https://bugs.launchpad.net/null/+bug/779166)

Try boot options: acpi_backlight=vendor

See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) for setting boot options.

So you'll temporarily override, and then modify /etc/default/grub if it works with the override:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor quiet splash"
```

---

### Post by jmsykes15 on 2011-08-29
> **bcbc said:**
> [https://bugs.launchpad.net/null/+bug/779166](https://bugs.launchpad.net/null/+bug/779166)

Try boot options: acpi_backlight=vendor

See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) for setting boot options.

So you'll temporarily override, and then modify /etc/default/grub if it works with the override:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor quiet splash"
```

Am I just supposed to put that anywhere when I press "e" or am I supposed to put that in the terminal?

---

### Post by bcbc on 2011-08-29
As per that guide I linked to...
> How to temporarily set kernel boot options on an installed OS (not wubi)

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:



Select the default ubuntu kernel (usually the top one), and rather than pressing enter, press E to edit.

Press DOWN ARROW until you get to the line that starts with

Code:
linux /boot
and press END keys to position your cursor at the end of the that line usually ending with “quiet splash”. 

Now you can type in additional kernel options like nomodeset (please dont make the same typing error I made for this screenshot  ):

So, press E on the first entry, move to where it says "quiet splash" and add acpi_backlight=vendor afterwards (before is okay too) so it looks like **quiet splash acpi_backlight=vendor**

---

### Post by jmsykes15 on 2011-08-29
This is everything written on my screen before I press "e"

```

Ubuntu, Linux 2.6.38_8-generic
Ubuntu, Linux 2.6.38_8-generic (recovery mode)
Windows 7 (Loader)(on /dev/sdal)

```

After I click the "e" on Ubuntu, Linux 2.6.38_8-generic I get this:

```

set params 'Ubuntu, Linux 2.6.38-8-generic'

insmod part_msdos
insmod ntfs
setroot='(/dev/sda, msdos2)'
search --no -floppy --fs-uuid --set=root 0E6E7AC56E7AA4DD
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
Linux /boot/vmlinuz-2.6.38-8-generic root=UUID=0E6E7AC56E7AA4DD loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-8-generic

```

I am guessing you wanted me to put acpi_backlight=vendor after 
```

Linux /boot/vmlinuz-2.6.38-8-generic root=UUID=0E6E7AC56E7AA4DD loop=/ubuntu/disks/root.disk ro quiet splash

```

and I did but it did not work.  If you can just copy my code and add it in so i can see it.  That would make a big differents.

---

### Post by bcbc on 2011-08-29
```
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=0E6E7AC56E7AA4DD loop=/ubuntu/disks/root.disk ro quiet splash acpi_backlight=vendor
```

Then Ctrl+X to boot with your modified options.

---

### Post by jmsykes15 on 2011-08-29
> **bcbc said:**
> ```
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=0E6E7AC56E7AA4DD loop=/ubuntu/disks/root.disk ro quiet splash acpi_backlight=vendor
```

Then Ctrl+X to boot with your modified options.

It did not work,  but thanks for the help.  I am just going to continue using win 7.  When I get another computer I might try again.

---

### Post by bcbc on 2011-08-29
> **jmsykes15 said:**
> It did not work,  but thanks for the help.  I am just going to continue using win 7.  When I get another computer I might try again.

I thought that bug report applied to your computer. But I don't have one of those myself and it's quite possible that you have a different issue. Hopefully someone else with a similar computer will suggest a more effective remedy or if you post in that bug report you might get some responses from people in a similar situation.

Alternatively, release 11.10 is due out in October and it's going to be pretty good - and this issue is likely already resolved.

Good luck

---

