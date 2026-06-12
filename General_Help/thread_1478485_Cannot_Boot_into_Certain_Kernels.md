---
title: "Cannot Boot into Certain Kernels"
date: 2010-05-09
forum: General Help
---

### Post by nbadal on 2010-05-09
I recently upgraded from karmic to lucid, and now when i try to boot into most of the recent kernels, or the latest Ubuntu cd, I get a black screen with corrupted-looking white bars along the bottom (see picture)

When I am able to get into older kernels (usually has to be through recovery mode) it tells me that my xorg.conf is incorrect or corrupt and gives me the option to reset it, which doesn't fix the problem.

Does anybody have any idea what could be causing this? Any more info I should provide?
Thanks in advance

---

### Post by Luftfuß on 2010-05-09
try reinstalling the kernels (any of them that you want to use) once you boot into ubuntu successfully. 
command:

$ sudo apt-get --reinstall <name of kernel package>

---

### Post by Luftfuß on 2010-05-09
Also can you run the kernels you want without x? (push: ctrl + alt + f2) when it seems to be done loading, and if that works you may want to reinstall either GNOME or KDE(which ever you use).

---

### Post by nbadal on 2010-05-09
> **Luftfuß said:**
> try reinstalling the kernels (any of them that you want to use) once you boot into ubuntu successfully. 
command:

$ sudo apt-get --reinstall <name of kernel package>

I just tried that, and I got the same result.  Let me try the other thing right now, and I'll see if that's whats wrong.

---

### Post by nbadal on 2010-05-09
Nope. I couldn't go to any of the Ctrl+Alt+F*s
Killing the x server with Ctrl-Alt-Backspace didn't change the screen either.

I've narrowed it down to 2.6.32-22-generic and 2.6.32-21-generic, everything before that at least goes into low graphics mode.

---

### Post by nbadal on 2010-05-10
Nobody has any ideas?

---

### Post by happyhamster on 2010-05-10
Which video driver does your system use?

---

### Post by nbadal on 2010-05-10
> **happyhamster said:**
> Which video driver does your system use?

I'm using the latest ubuntu-repository nVidia drivers on dual 9800 GT's

---

### Post by happyhamster on 2010-05-11
- Few things you could try. First, try booting with the kernelparameter "nomodeset" (to disable kernel-modesetting). To do this: boot into the grub menu, choose a kernel you want to boot, and press 'e'. Select the line starting with "linux /boot/vmlinuz...." and press the End key to get at the end of it (it will usually end with "quiet splash"). Add 

nomodeset

- to it. Then press Ctrl-x to boot. If this happens to solve your problem, then you can make the change permanent by editing grub:

gksudo gedit /etc/default/grub

- Find the line GRUB_CMDLINE_LINUX_DEFAULT="......" and add nomodeset to the list of parameters (between the quotes). Save, exit the editor, and update grub:

sudo update-grub


- If the above doesn't solve your problem, you could try generating a new xorg.conf manually. Boot into a recovery kernel, and choose to drop into a root shell. You are root at this moment, so be careful. In order, run:

cd /etc/X11
cp xorg.conf xorg.conf.backup
Xorg -configure
cp /root/xorg.conf.new xorg.conf
reboot

- The first command navigates to the proper folder.
- Second one makes a backup of your current xorg.conf
- Third creates a new config file: /root/xorg.conf.new 
- Fourth command does the actual overwriting of the old xorg.conf
- You don't need to use "sudo", because you're root. Also, note the letter x is sometimes used upper case and sometimes lower case.

- Anyway, in case things didn't work out, boot into a shell once more, and copy the old xorg.conf back again:

cd /etc/X11
cp xorg.conf.backup xorg.conf

- Good luck.

---

