---
title: "crisis, i broke grub"
date: 2011-02-04
forum: General Help
---

### Post by Mallachar on 2011-02-04
so I was trying to edit grub because I wanted to remove a bunch of the old linux kenerels, and I didnd't have permision to edit the file, so I asked on another forum how to get permison and the guy had me to an rm function.

well to my surprise that deleted my grub fril found it etc/default/

is there anyway to get it back or to un remove?

---

### Post by dh04000 on 2011-02-04
Into the terminal, type:   sudo apt-get install grub


That should fix your problem.

---

### Post by Mallachar on 2011-02-04
I did that, and it says 

Setting up grub (0.97-29ubuntu60) ...
mallachar@mallchar:~$

but I dont see the grub file there still...

---

### Post by dh04000 on 2011-02-04
I'm not an linux expert, so I can't tell you what that means. But, did the grub install command do anything? Did it download anything? Or did it just spit back out something along the lines of "you have the newest version installed already"?  <---- not actually what it says, but thats the gist.

If its installed already, try running:  sudo update-grub

Tell me what that spits out.

---

### Post by oldfred on 2011-02-04
It probably does not know you deleted something, so you may have to uninstall and reinstall.

These were the command from a chroot I have in my notes. Use this to get to sudo mode:
sudo -i
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

---

### Post by Mallachar on 2011-02-04
> **oldfred said:**
> It probably does not know you deleted something, so you may have to uninstall and reinstall.

These were the command from a chroot I have in my notes. Use this to get to sudo mode:
sudo -i
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda


So I got up to the apt-get install grub-pc grub-common and I get the following error

Not recplacing deleted config file /etc/default/grub

---

### Post by Mallachar on 2011-02-04
never mind it was slow to finish

its done now, bug the grub file is still missing...

---

### Post by JRV on 2011-02-04
Download the Rescatux disk from this site: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot this live CD and follow the prompts.

This is the easiest way I know of to fix Grub2.

---

### Post by coffeecat on 2011-02-04
> **Mallachar said:**
> never mind it was slow to finish

its done now, bug the grub file is still missing...

Is it /etc/default/grub that is missing? If so, here is a default one from Lucid/10.04:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
```Open gedit with root privileges with:

```
gksudo gedit
```Copy and paste the text above into gedit and save the file as /etc/default/grub. If you are running Maverick/10.10 post back. Tell us what version of Ubuntu you are running anyway. That Lucid version should work, but I can check to see if there is any difference in the Maverick one. After you have saved the /etc/default/grub file, run:

```
sudo update-grub
```I don't know whether that will solve all your problems but at least you will have a working /etc/default/grub.

---

### Post by Mallachar on 2011-02-04
Sorry got side tracked with school work for a moment

I am running 10.10

---

### Post by coffeecat on 2011-02-04
> **Mallachar said:**
> Sorry got side tracked with school work for a moment

I am running 10.10

Try the 10.04 one I posted anyway - from memory there's no significant difference - and let us know what happens. I'll boot into 10.10 within the hour to check and post back.

---

