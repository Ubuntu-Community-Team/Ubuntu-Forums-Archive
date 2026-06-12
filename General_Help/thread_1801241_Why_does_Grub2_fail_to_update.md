---
title: "Why does Grub2 fail to update?"
date: 2011-07-10
forum: General Help
---

### Post by Pipps on 2011-07-10
I amend the grub file at /etc/default/grub as administrator, I then open a terminal and perform 'sudo update-grub', but I receive the following error message:

> /etc/default/grub: 1: If: not found

What could this mean? How can I update Grub successfully?

---

### Post by andrewthomas on 2011-07-10
Post the contents of your /etc/default/grub file.

---

### Post by DanneStrat on 2011-07-10
> **Pipps said:**
> 1: If: not found

Hi.

It looks like something is missing in your grub config file.

Do this:

```
cat /etc/default/grub
```

and post the output.

---

### Post by Pipps on 2011-07-21
Thanks for helping me. The output of ```
cat /etc/default/grub
``` produced the following:

> If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Is there anything missing?

---

### Post by plucky on 2011-07-21
> Is there anything missing? 

A # in front of  ```
If you change this file, run 'update-grub' afterwards to update
```


Good Luck

---

### Post by Pipps on 2011-07-21
Ha! This worked perfectly! Thank you for such a speedy reply! :)

---

