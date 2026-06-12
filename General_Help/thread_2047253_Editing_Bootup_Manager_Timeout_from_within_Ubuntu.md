---
title: "Editing Bootup Manager Timeout from within Ubuntu"
date: 2012-08-24
forum: General Help
---

### Post by Heum91 on 2012-08-24
Alright, so as some of you probably already figured, I was stupid enough to set Ubuntu as the main OS, and the timeout to zero (after reading 30 seconds earlier NOT TO DO THAT). So now I boot into Ubuntu and all is fine, except there is no way for me to access Windows.
Now, I've done my googlin', and I know people say that you'd need a Windows Fix CD of some kind to do something about that. Thing is, the CD-booting (and USB-booting) option is disabled, and the BIOS is locked by a password which I don't have, and that cannot be reset through traditional battery-juggling. I've tried.
The bright side of the equation of course, is that this being wubi, I actually have access to the windows files. So I figure, somewhere in there there must be a configuration file of some kind with some zero in it that I should be able to change to 30... right?
Or did I really screw this up for good?
(OS: Ubuntu 12.04 and Windows 7 32bit Enterprise)

EDIT: I should mention, Grub cannot help me here. This is because Ubuntu and Windows are installed on the same partition. Wubi does that.

---

### Post by Bucky Ball on 2012-08-24
Welcome. Hit shift after the BIOS screen. That will take you to the grub menu. Choose Windows. CD shouldn't be required. 

If that all works, we can make the menu pause at boot permanently (if it doesn't then there's another issue).

Open a terminal (Applications>Accessories>Terminal) and paste in this command:

```
sudo nano /etc/default/grub
```At the top of that screen you should see something like this:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=10**
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```Make yours look like that then hit control+x, 'y', then type:

```
sudo update-grub
``` ... Then type exit to exit the terminal. Reboot and see if it stuck.

---

### Post by Heum91 on 2012-08-24
That doesn't work to well, as Windows is not listed. I believe this is because they're installed on the same partition, as wubi does.

---

### Post by Bucky Ball on 2012-08-24
Ah, thanks for mentioning that! I've no idea, then. Please edit your first post and add that information to help others. 

Good luck. ;)

---

### Post by black veils on 2012-08-24
how strange, you installed using wubi, yet windows doesnt show in grub boot loader.

perhaps following [this]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") could help us help you, paste the link in a reply here.

---

### Post by bcbc on 2012-08-24
There's no way that I'm aware of other than a Win7 repair CD or install DVD. 
There should be an override to reset the BIOS password but it might involve opening up the machine.

Boot-repair doesn't fix that. Grub won't work either.

I don't think anyone's gone and done file comparisons to see exactly where the timeout is set in win7 and whether you can poke it - in XP it was easy. It would certainly save a large number of people who've done the same thing you did.

---

### Post by bcbc on 2012-08-24
> **black veils said:**
> how strange, you installed using wubi, yet windows doesnt show in grub boot loader.

Grub bypasses Windows when it's a Wubi install (in /etc/grub.d/30_os-prober). The change was made due to this problem because it looks as though you can boot Windows from the Wubi grub, but in fact you need the Windows Boot Manager to boot Windows and once you bypass that and boot directly into the Wubi install, you are stuck.

---

### Post by Heum91 on 2012-08-25
> **bcbc said:**
> I don't think anyone's gone and done file comparisons to see exactly where the timeout is set in win7 and whether you can poke it - in XP it was easy. It would certainly save a large number of people who've done the same thing you did.

My thoughts exactly

EDIT: This topic is not relevant to me any more, as the HDD was replaced and Windows reinstalled, due to some other, not related issue. I still think the quote above rings true, though.
(Also, somewhat off-topic, I personally would not recommend anyone installing Ubuntu through Wubi, as I experienced the resulting OS to be grotesquely sluggish (waiting for up to a full minute for as simple a task as opening a regular folder). That OS was not the Ubuntu I used to know. Installing it properly now.)

---

