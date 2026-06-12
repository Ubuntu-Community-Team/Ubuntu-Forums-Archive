---
title: "GRUB2- GRUB _HIDDEN_TIMEOUT=0 doesn't work"
date: 2010-02-15
forum: General Help
---

### Post by volvolinux on 2010-02-15
Hi, friends.

According to the Grub community documentation. the value of GRUB_HIDDEN_TIMEOUT will control the display of the menu.

there are 2 files which contorl the grub.cfg after you run update-grub command.

1. /etc/default/grub

2. /etc/grub.d/*.*

here is my /etc/default/grub file output:

------------------------------------------------------------------------------------------------------------------
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=90
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=795"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1280x800

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
---------------------------------------------------------------------------------------------------------------------------------

all the scripts involved have the x bit set.

however , after I run the update-grub. My system will still display the menu....

Can I know what's the problem?

---

### Post by nixclusive on 2010-02-15
> GRUB_TIMEOUT=90 

Hmmm, my /etc/default/grub file has the value of GRUB_TIMEOUT in quotes.

```
GRUB_TIMEOUT="10"
``` 

Not sure why an integer value should be in quotes but I didn't change anything and I don't see the grub menu either.

Do you see a 90 second timeout when you're shown the grub menu?

edit:
I usually keep the "shift" key depressed while powering on the system to get the grub menu. FYI.

---

### Post by volvolinux on 2010-02-15
yes, I have set it to 90 seconds to have a test.

the value shouldn't be in quotas, as the docemnt said. but I will have a try to see if it works I quote the value.

THanks.

---

### Post by wojox on 2010-02-15
Are you dual booting?

---

### Post by jsriz on 2010-02-15
Hey if you want 2 esc the menu use 
```

grub_timeout=0

```
not the grub _hidden_timeout

> 

[list]
[*]**grub_hidden_timeout=0**
[list]
[*]the hidden timeout option allows a screen to be displayed without the grub 2 menu, awaiting input from the user for a given number of seconds. It is available to single-os computers - if multiple os's are known to grub 2, this option is bypassed. 
**on single-os computers:**
[list]
[*]the menu will be hidden unless the user adds a # symbol to the beginning of this line ( # grub_hidden_timeout=0 ) and the grub_timeout value is greater than 0.
[*]**for integers greater than 0**: The system will pause without displaying a menu for the designated number of seconds. If the user does not press any key during the timeout the system will then boot the default os/kernel.
[*]with a value of **0**: The system will boot the default os/kernel with no delay. No menu will be displayed.
[*]if enabled, the splash image designated in 05_debian_theme will be displayed rather than a blank screen.
[*]the user may press any key during the timeout to display the menu.
[*] the user may force displaying the menu as the computer boots by holding down the shift key.
[*]during boot, the system will check the shift key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the esc key.
[/list]

**on computers on which grub 2 recognizes multiple os's:**
[list]
[*]this entry is ignored.
[*]the menu will be displayed for the value designated in grub_timeout.
[*]the *hidden menu timeout* option is not available, as it is bypassed by a conditional in */etc/grub.d/30_os-prober*.
[*]the system can still boot without displaying a menu by setting the grub_timeout value to **0**, however a timeout delay with a blank screen is not available.
[*]the keystatus check for *shift* key usage is bypassed by the scripts. Holding down the *shift* key during boot will not display the menu.
[*]if the user of a multi-os computer wishes to hide the menu while incorporating a blank screen timeout the scripts in */etc/grub.d/30_os-prober* can be modified. Please refer to [grub 2 title tweaks]("http://ubuntuforums.org/showthread.php?t=1287602").
[/list]
[/list]

[*]**grub_hidden_timeout_quiet=true**
[list]
[*]true - no countdown is displayed. The screen will be blank.
[*]false - a counter will display on a blank screen for the duration of the grub_hidden_timeout value.
[/list]
[/list]



---

### Post by pmlxuser on 2010-02-15
does duel booting have an effect on this value??

---

### Post by volvolinux on 2010-02-15
> **jsriz said:**
> Hey if you want 2 esc the menu use 
```

grub_timeout=0

```not the grub _hidden_timeout

hey man, you are right....

It works now. Thanks!

---

### Post by audiomick on 2010-02-15
> **pmlxuser said:**
> does duel booting have an effect on this value??
As far as I know, it is only relevant if you are dual booting. If there is only one OS on the machine, the menu stays hidden.

---

