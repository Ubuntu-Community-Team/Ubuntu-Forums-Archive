---
title: "Boot into terminal"
date: 2010-12-20
forum: General Help
---

### Post by linusnorton on 2010-12-20
Hi Guys,

I have been googling my *** off trying to find a way of getting Ubuntu 10.10 desktop edition to boot into the terminal (or runlevel 3?)

Suggestions have all been from around 2007 and no longer seem to work (creating /etc/inittab, rcconf, sysv-rc-conf all didn't work)

So how can I do it?

I don't want to have to install the server edition.

I'm not sure what I want is even possible but I'm building an arcade game cabinet and I would like the machine to boot into the shell, auto login and run a python script I have made.

---

### Post by wojox on 2010-12-20
Try this [Thread]("http://ubuntuforums.org/showthread.php?p=10247279#post10247279")

---

### Post by DarthScape on 2010-12-20
You could try starting the computer holding shift, should bring you to the grub menu, select recovery.

You could try booting like normal, in terminal type shutdown now, you might get a prompt to drop to shell.

For a more permanent solution, try Arch...

---

### Post by linusnorton on 2010-12-20
> **wojox said:**
> Try this [Thread]("http://ubuntuforums.org/showthread.php?p=10247279#post10247279")

Sorry, no dice. I tried adding 

```

if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
  . startx
  logout
fi

```

to ~/.bash_profile with no luck.

@DarthScape: I would like an automated method

---

### Post by oldos2er on 2010-12-20
If you're using grub2, edit /etc/default/grub, change

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to

GRUB_CMDLINE_LINUX_DEFAULT="text"

Run **sudo update-grub**, reboot.

---

### Post by sisco311 on 2010-12-20
Welcome to the forums!

To disable GDM edit the file /etc/default/grub and replace **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"**, then generate a new Grub2 config file:
```
sudo update-grub
```

NOTE: You can delete the **quiet** option to make the boot process verbose and delete **splash** to disable the splash screen.

You can use mgetty to auto login to a virtual console. Install it (it's in the universe repo):
```
sudo apt-get install mingetty
```

Then edit /etc/init/tty1.conf to something like:
```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
**exec /sbin/mingetty --autologin USERNAME tty1 linux**
```

Of course, you have to replace USERNAME with your login name.

And finally, to auto start your application when you are logging in to vc1 (tty1) add something like:
```
if [[ $(tty) = /dev/tty1 ]]; then
  **command**
fi

```

to your ~/.bash_profile file.

Replace **command** with the command you want to run.

---

### Post by linusnorton on 2010-12-20
> **oldos2er said:**
> If you're using grub2, edit /etc/default/grub, change

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to

GRUB_CMDLINE_LINUX_DEFAULT="text"

Run **sudo update-grub**, reboot.

You win. Thank you, I did not see this suggested anywhere else.

---

