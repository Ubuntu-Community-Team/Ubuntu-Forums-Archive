---
title: "Thinkpad x121e suspend-on-lid-close"
date: 2011-10-07
forum: General Help
---

### Post by MorrisseyJ on 2011-10-07
Hi,

I was wondering if anyone could help me in getting my suspend-on-lid-close to work on my Thinkpad x121e.

This is a new piece of hardware and there doesn't appear to be much on the web for solving it the problem.

When i close the lid, the machine seems to suspend, but when i open it i am met with a blank screen and can do nothing other than hard power down. I have noticed, however, that when i have my machine plugged into an external monitor, i can close the lid, observe the suspend and then open the lid to get a password login screen.

So it seems that the suspend is working but that the monitor doesn't come back to life when i open the lid. Having an external monitor plugged in seems to wake the monitor up and so give me the login screen.

This makes me think that this might not be too hard to solve. i don't really understand a lot of the hardware stuff but think that there might be a simple way to make sure that the screen triggers when i open the lid (or make the machine think that there is an external monitor plugged in). I am  guessing that there is just a switch that i need to stick to 'on'.

The thinkpad x121e is great as a portable machine. Getting this to work would vastly increase its portability.

Any suggestions?

---

### Post by ajgreeny on 2011-10-07
Does the same thing happen if you choose to suspend from the shutdown button or is it just when you close the lid?

---

### Post by MorrisseyJ on 2011-10-07
As far as i can tell - i haven't done this lots and lots of times - the same thing happens.

---

### Post by 2F4U on 2011-10-07
You should first look into /var/log/pm-suspend.log if you can see any errors when the machine resumes. If that doesn't reveal anything, try to add nomodeset to the grub kernel parameters. This fixed the suspend/hibernate problems on my old ThinkPad X31 with ATI card.

---

### Post by MorrisseyJ on 2011-10-07
2F4U: 

Thanks, can you tell me what i am looking for in /var/log/pm-suspend.log?

Also, do i add nomodeset to the grub kernel parameters by doing the following?

> [SIZE=4]**How to permanently set kernel boot options on an installed OS (not wubi)**[/SIZE]

To permanently change the default kernel boot options, press ALT+F2 or   open a terminal from system > accessories > terminal. Type in the  following command:

     Code:
     gksudo gedit /etc/default/grub 
a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
     Code:
     GRUB_DEFAULT=0 #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** GRUB_CMDLINE_LINUX="" 
add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:

     Code:
     GRUB_DEFAULT=0 #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"** GRUB_CMDLINE_LINUX="" 
Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:

     Code:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=[COLOR=Red]\"[/COLOR]Linux[COLOR=Red]\"[/COLOR]" 
Now in the terminal, run the following command to update your grub configuration with the new default settings:
     Code:
     sudo update-grub 
From: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

One more thing, if i do this, and its not the root of the problem, will it cause any problems?

Thanks.

---

### Post by MorrisseyJ on 2011-10-21
So installing 11.10 messed up my GRUB meaning that all i got on boot up was:

> error: invalid arch independences ELF magic
grub rescue >

As far as i can understand this was caused by my machine having a UEFI rather than a BIOS set up.

In any respect i wasn't able to resolve the GRUB problem in 11.10 and so had to reinstall 11.04. The good news is that my suspend-on-lid-close now works in 11.04!

I am not in a position to try and sort the GRUB issue in 11.10 now and so have reverted back to 11.04. 

When i get a chance i'll look at getting 11.10 working, though by then it might be 12.04...

---

