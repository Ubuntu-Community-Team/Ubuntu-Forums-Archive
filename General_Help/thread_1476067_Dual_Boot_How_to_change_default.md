---
title: "Dual Boot: How to change default"
date: 2010-05-07
forum: General Help
---

### Post by Tomination on 2010-05-07
Hey all, I am now dual booting between Windows 7 and Ubuntu 10.04

When i turn on my computer it goes to a GNU Grub screen where i can choose an OS to boot, in 6 seconds it auto chooses default.

How to i change the default from Ubuntu to Windows?

I have tried to edit the grub.cfg file but it wont let me ([http://www.linuxforums.org/forum/linux-kernel/14774-gnu-grub-selecting-default-boot-kernel.html](http://www.linuxforums.org/forum/linux-kernel/14774-gnu-grub-selecting-default-boot-kernel.html))

Please Help :) thanks, i need the .NET framework for a lot of my studies so i need to default into Windows

---

### Post by sunk8 on 2010-05-07
> **Tomination said:**
> 
How to i change the default from Ubuntu to Windows?
I have tried to edit the grub.cfg file but it wont let me 
Please Help :) thanks, i need the .NET framework for a lot of my studies so i need to default into Windows

Hmm... Did you do a 'sudo update-grub' after the changes?

On the other hand, why don't you install the package 'startup-manager'. It's a nice GUI app to configure some boot options... ;-)
Hope this solves your question...

---

### Post by Tomination on 2010-05-07
> **sunk8 said:**
> Hmm... Did you do a 'sudo update-grub' after the changes?

On the other hand, why don't you install the package 'startup-manager'. It's a nice GUI app to configure some boot options... ;-)
Hope this solves your question...

Hey :)

I am very new with Ubuntu so i havent done a sudo grub updater thing, but im not sure if this would solve my issue because i can see Windows 7 in the list, but i want it to be default selection instead of Ubuntu.

I havent heard of the Package Startup Manager, ill try and find that thanks :)

---

### Post by Tomination on 2010-05-07
Thanks :)

The startup manager worked great :)

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by patchwork on 2010-05-07
The file you need to modify is the /etc/default/grub file.  It should look similar to this:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
GRUB_CMDLINE_LINUX=""

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

```To modify the file, you will need superuser privileges, so start your editor with
```
gksu gedit
```You can either directly specify the grub menu position to load by default ( GRUB_DEFAULT = 0 in my example), or you can enter the word 'saved'.  

If you enter 'saved', you will need to run two additional commands, if you manually enter the position, you will need to run one additional command:

'saved': ```
sudo grub-set-default desired_position_number
sudo update-grub
```manually entered number:

```
sudo update-grub
```The benefit to setting the default to saved is that you can change the default position again in the future with the grub-set-default command and update-grub command without monkeying around in the file if the menu choice changes as kernels are upgraded.

Or, as the others have suggested, you can find a neat little graphical application to do this work for you.



EDIT:   too slow....

---

