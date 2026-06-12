---
title: "no grub meu at boot"
date: 2010-10-07
forum: General Help
---

### Post by zuku on 2010-10-07
Hi, 
have problem with grub 2, boot menu doesn't appear at all.

I have lvm on my disks:
/dev/sda1 - /boot
/dev/vgroup/root - /
/dev/vgroup/swap - swap

and here is /etc/default/grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

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

pressing SHIFT during boot doesn't help too.

---

### Post by plucky on 2010-10-07
From [Here](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2) that is the default behaviour for single OS machines.

You need to change ```
GRUB_HIDDEN_TIMEOUT=0
``` to a value greater than 0 and then run ```
sudo update-grub
```

Good Luck

---

### Post by zuku on 2010-10-07
I've changed it, still the same.

---

### Post by d.atanasov on 2010-10-07
Did you try to look at /boot/grub/grub.cfg, which is the real grub menu at start.

---

### Post by SuperUserDO on 2010-10-07
Hi,
Use the ubuntu live cd to log on Ubuntu,open the terminal and use these codes
[HTML]sudo su[/HTML] 
then you have to find the partition where ubuntu is installed by this code(If you HDD is SATA)
[HTML]sudo fdisk -l /dev/sda[/HTML]
IF DATA HDD use this:
[HTML]sudo fdisk -l /dev/hda[/HTML]
you will get something like this picture:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171530&stc=1&d=1286453158[/IMG]
in that picture Ubuntu is installed on this partition "/dev/sda8" so i will mount this partition (where ubuntu is instaleed) by this code:
[HTML]sudo mount /dev/sda8 /mnt[/HTML] 
then fix the boot loader by this code:
[HTML]sudo grub-install --root-directory=/mnt/ /dev/sda[/HTML]
RESTART your computer.
Done.

---

### Post by zuku on 2010-10-07
as I previously said I have LVM configured
one regular partition /dev/sda1 is only mount for /boot 

my fdisk -l /dev/sda:


Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sda1   *           1          30      240943+  83  Linux
/dev/sda2              31      121601   976519057+  8e  Linux LVM


ok I will try reinstall grub from live cd.

---

### Post by oldfred on 2010-10-07
If you only have Ubuntu installed the default is not to show the menu as you normally do not need it. You can hold down shift from BIOS boot until menu appears.

---

### Post by zuku on 2010-10-08
haha still the same :/
I've done next steps:

from livecd:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

reboot system then
sudo update-grub
sudo grub-install --recheck /dev/sda

but still have NO Grub menu!

---

### Post by plucky on 2010-10-08
That is because it is the default behaviour when you have a single operating system on your machine and all you are doing is re-installing GRUB2 back to default.

You need to change the behaviour of GRUB.

Edit the /etc/default/grub and change ```
GRUB_HIDDEN_TIMEOUT_QUIET=true
``` to ```
GRUB_HIDDEN_TIMEOUT_QUIET=false
``` and then run ```
sudo update-grub
``` Reboot and see if that works.

It could also be the resolution of your moniter is not set correctly to display the boot menu,might be worth playing with ```
GRUB_GFXMODE=800x600
``` to see if it makes a difference.Just remember to run "sudo update-grub" when you make a change.

Good Luck

---

### Post by zuku on 2010-10-08
success ;)
problem resolved ;)

GRUB_HIDDEN_TIMEOUT= should be nothing here after the equal sign, then menu is always displayed

thank all of You for helping me.
greetings.

---

### Post by plucky on 2010-10-08
> **zuku said:**
> success ;)
problem resolved ;)

GRUB_HIDDEN_TIMEOUT= should be nothing here after the equal sign, then menu is always displayed

thank all of You for helping me.
greetings.

You can now mark the thread as **[Solved]** using Thread Tools at top of page.

Well Done

---

