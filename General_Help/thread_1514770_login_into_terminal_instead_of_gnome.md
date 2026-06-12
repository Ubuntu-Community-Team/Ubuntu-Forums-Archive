---
title: "login into terminal instead of gnome"
date: 2010-06-21
forum: General Help
---

### Post by DimitrisRHO on 2010-06-21
how can I login into terminal istead of gnome? will I be then able to log into terminal by typing startx?

---

### Post by happyhamster on 2010-06-21
- Boot until the login screen appears. Press ctrl-alt-F3 to enter a console. Login. Then stop gdm:

sudo service gdm stop

- Later, you can run:

sudo service gdm start

- to bring up the graphical login screen again, or just

startx

- to start x directly. Good luck.

---

### Post by S.R on 2010-06-21
Log in via "xterm". You can then start GNOME from the terminal via the command "gnome-session".

---

### Post by DimitrisRHO on 2010-06-22
> **happyhamster said:**
> - Boot until the login screen appears. Press ctrl-alt-F3 to enter a console. Login. Then stop gdm:

sudo service gdm stop

- Later, you can run:

sudo service gdm start

- to bring up the graphical login screen again, or just

startx

- to start x directly. Good luck.

thanks, that worked, but I want to make it always to login into console instead of gnome. 
you know how?

---

### Post by sisco311 on 2010-06-22
Edit the /etc/default/grub file and append the default kernel parameters with **text**:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **text**"
GRUB_CMDLINE_LINUX=""
...

```
then run:
```
sudo update-grub
```

To disable the splash screen remove the **splash** option. To make the boot process verbose remove the **quite** option.

---

### Post by DimitrisRHO on 2010-06-22
> **sisco311 said:**
> Edit the /etc/default/grub file and append the default kernel parameters with **text**:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **text**"
GRUB_CMDLINE_LINUX=""
...

```
then run:
```
sudo update-grub
```

To disable the splash screen remove the **splash** option. To make the boot process verbose remove the **quite** option.

great, this is what I was looking for, thanks a lot, it rocks :guitar:

this is a real linux login screen  \\:D/

---

### Post by sisco311 on 2010-06-22
> **DimitrisRHO said:**
> great, this is what I was looking for, thanks a lot, it rocks :guitar:

this is a real linux login screen  \\:D/

Cool!!!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

