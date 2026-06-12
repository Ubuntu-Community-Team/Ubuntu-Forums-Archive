---
title: "Help ! Please!"
date: 2011-07-31
forum: General Help
---

### Post by thelildrummaboy on 2011-07-31
I have a problem with my acer aspire laptop and The screen is like completely black i mean if you hold a flashlight to a certain spot you can see a tiny bit. i was on another thread earlier and the posted this 
 
"This fixed a black screen issue and a brightness adjustment issue after installation of ubuntu. Also on 11.04 I couldn't get Unity to work until I edited grub I didn't come up with the fix but it took me forever to find a solution so I figured I would post it. If I have did something wrong just get a mod to delete or move this. I don't use forums often. 

Code:
 
sudo gedit /etc/default/grubEdit two lines to read as follows: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"GRUB_CMDLINE_LINUX="acpi_osi=Linux"sudo update-grub
                                              "
i dont know what that means or how to do it could you please help me figure it out. i want to know how to do it. :)

---

### Post by Wim Sturkenboom on 2011-08-01
Note:
commands are in bold

Assuming your in the graphical environment, press <alt><F2> (that is the alt-key and the F2 key at the same time)

In the window that pops up, type **xterm** and press <enter>
A terminal will be opened
type the first command
```

wim@ubuntu-desktop01:~$ **sudo gedit /etc/default/grub** 
[sudo] password for wim: 

```
An editor will open with the (more or less) following contents
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[B][COLOR="Red"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[/COLOR][/B]
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
Change the two red lines
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

```
and
```

GRUB_CMDLINE_LINUX="acpi_osi =Linux"

```
Save and exit the file

Next run the second
```

wim@ubuntu-desktop01:~$ **sudo update-grub**
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
wim@ubuntu-desktop01:~$ 

```
Reboot your system


Note:
If you're blind (because your screen is black), this might be difficult to do.

---

### Post by old farmer on 2011-08-01
HELP: how can I fix this: LC_ALL = (unset)
thanks

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_CA:en",
	LC_ALL = (unset),
	LC_TIME = "ca.UTF-8",
	LANG = "en_CA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory

---

### Post by Wim Sturkenboom on 2011-08-01
> **old farmer said:**
> HELP: how can I fix this: LC_ALL = (unset)
thanks

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_CA:en",
	LC_ALL = (unset),
	LC_TIME = "ca.UTF-8",
	LANG = "en_CA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Please start your own thread; I can't see how this relates to the original problem (or how it solves it ;) )

---

### Post by Wim Sturkenboom on 2011-08-01
It might be easier to do the initial changes in grub itself while the system boots.

Keep <shift> pressed while the system boots; you should see a grub menu come up after a while; I hope it's visible on your system at that stage

Highlight the first line and press <e> to make temporary changes

Find the line that starts with 'linux /boot/...' and ends with 'ro quiet splash' and edit it; the line is long and will probably occupy two lines on the screen; you can use the cursor keys to navigate

Change the line so the end reads
[code]
ro [COLOR="Red"]acpi_osi=Linux[/COLOR] quiet splash [COLOR="Red"]acpi_backlight=vendor[/COLOR]
[code]
In red the 'additions' that you specified in the opening post. Press <ctrl>x (that is control plus x) to boot with those settings. If that works, you can make the change permanent following the instructions in post #2

Good luck

---

