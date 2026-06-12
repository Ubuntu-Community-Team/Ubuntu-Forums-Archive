---
title: "Grub2 error"
date: 2012-05-27
forum: General Help
---

### Post by caffeinatedev on 2012-05-27
I tried to use grub-customizer to edit the amount of time that GRub is shown during boot to zero seconds (I had previously dual-booted but Ubuntu 12.04 is my only OS now). Something happened while using the utility that ended up giving me this error (without quotations): "/usr/sbin/grub-mkconfig: 39: /etc/default/grub: Syntax error: EOF in backquote substitution". I have also tried editing /etc/default/grub manually with the "sudo gedit /etc/default/grub" command in terminal and it doesn't seem to change anything.

Also note that I can boot into Ubuntu fine and that trying to make GRub not appear is my only trouble.

---

### Post by drs305 on 2012-05-27
Although I'm pretty rusty when it concerns Grub Customizer, I did write a howto about it a while back. One of the problems may be that GC created some additional files/folders and your system is still using them.

There is a section on how to restore things. See the GC link in my signature line.

A second option is to post your /etc/default/grub file and let us look at it. But the issue descibed in the first paragraph may apply.

Another option is to completely purge and reinstall Grub2. Since you used GC, you will also probably have to remove some additional folders/files after purging but before reinstalling grub-pc. Instructions for purge/reinstall: [https://help.ubuntu.com/community/Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing")

Take a look at the howto, if you still have issues come on back and let us know what you've tried.

---

### Post by wilee-nilee on 2012-05-27
> **caffeinatedev said:**
> I tried to use grub-customizer to edit the amount of time that GRub is shown during boot to zero seconds (I had previously dual-booted but Ubuntu 12.04 is my only OS now). Something happened while using the utility that ended up giving me this error (without quotations): "/usr/sbin/grub-mkconfig: 39: /etc/default/grub: Syntax error: EOF in backquote substitution". I have also tried editing /etc/default/grub manually with the "sudo gedit /etc/default/grub" command in terminal and it doesn't seem to change anything.

Also note that I can boot into Ubuntu fine and that trying to make GRub not appear is my only trouble.

After the edit did you run.

```
sudo update-grub
```In the worst case, you could remove the customizer and purge and reload grub from the desktop and start over. Not sure if a edit then a update will get past the customizer to be honest, and you can do all that editing without it as well.

Setting the time out to 0 is not a good idea though unless you know you can still catch the grub menu if needed.

---

### Post by caffeinatedev on 2012-05-28
drs305,
I've actually seen the tutorial you wrote prior to positing this and I'm sad to say that it doesn't seem to apply to my situation.

The contents of my /etc/default/grub configuration:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\Linux\"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#UNNAMED_OPTION=""
#UNNAMED_OPTION=""
GRUB_DISABLE_OS_PROBER="true"
```

Thanks for the speedy reply :)

---

### Post by caffeinatedev on 2012-05-28
> After the edit did you run.

 	Code:
 	sudo update-grub 
In the worst case, you could remove the customizer and purge and  reload grub from the desktop and start over. Not sure if a edit then a  update will get past the customizer to be honest, and you can do all  that editing without it as well.

Setting the time out to 0 is not a good idea though unless you know you can still catch the grub menu if needed.

The problem is that whenever I try to upgrade my grub settings, it doesn't apply because of the syntax error.

---

### Post by wilee-nilee on 2012-05-28
[COLOR=White].[/COLOR]

---

### Post by drs305 on 2012-05-28
> **caffeinatedev said:**
> The problem is that whenever I try to upgrade my grub settings, it doesn't apply because of the syntax error.

The problem is in this line:
> GRUB_CMDLINE_LINUX="acpi_osi=\Linux**[COLOR="Red"]\[/COLOR]**"

GRUB2 doesn't like the trailing \. If I remove it and leave the rest of the line as is the command runs without error. I've not tried the option you are trying to use so I can't attest how it should be entered.

---

### Post by oldfred on 2012-05-28
I think it does not like this:
> GRUB_CMDLINE_LINUX="acpi_osi=\Linux\"See this bug report as it does have some work arounds on quotes & \\\:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445952](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445952)

---

### Post by caffeinatedev on 2012-05-28
SOLVED!

Thanks very much guys, I really appreciate the help I've received from this community:guitar:

---

### Post by listerdl on 2012-05-28
Also for for the future - take a look at [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

Really good Grub Rescuer - its worth burning it and keeping it for a crisis

---

### Post by caffeinatedev on 2012-05-29
How is Super Grub Disk different from using Boot-Repair from the Ubuntu Live CD?

---

### Post by oldfred on 2012-05-29
They are both good repair tools. Each works a bit different, so I have both in my repair toolbox just in case.

---

### Post by wilee-nilee on 2012-05-29
+1 on supergrub, but I just use it to get into a OS not booting, no boot repairs.

---

