---
title: "Grub2"
date: 2011-08-25
forum: General Help
---

### Post by oloapota on 2011-08-25
I've just installed Ubuntu on my laptop, alongside windows 7
I want windows 7 to be the default OS at startup

I've tried to change that setting with both Startup manager AND Grub customizer.

Both kind of work, in the sense that I've managed for instance to change the seconds it takes to start the default OS

HOWEVER, the default OS is still Ubuntu, even though I've selected windows 7 as the default OS in both softwares

Can you help?
thanks

---

### Post by lmarmisa on 2011-08-25
What is your version of Ubuntu?

---

### Post by Quackers on 2011-08-25
If you are using Ubuntu 11.04 it's possible that neither SUM or Grub Customizer works with that version of grub. You may need to change things manually.
Have a look at section 5 below

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by lmarmisa on 2011-08-25
I recommend the save default option of GRUB2. This option will automatically set the last selected OS from the menu as the default OS on the next boot. I like to use this option.

Open a terminal and type this command:

```

gksudo gedit /etc/default/grub

```Then edit the lines marked in blue:

```

 If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

[COLOR=Blue]GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true[/COLOR]
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
...

```Save & Quit.

Finally type this command:

```

sudo update-grub

```

---

### Post by oloapota on 2011-08-25
> **lmarmisa said:**
> I recommend the save default option of GRUB2. This option will automatically set the last selected OS from the menu as the default OS on the next boot. I like to use this option.


Thanks for the input
I tried first to select this option through the GUI (Grub customizer), and it worked

Have a nice day,
Paolo

---

