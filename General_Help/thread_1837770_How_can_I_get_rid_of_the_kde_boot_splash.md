---
title: "How can I get rid of the kde boot splash?"
date: 2011-09-02
forum: General Help
---

### Post by lethu on 2011-09-02
Hello, I have recently moved to linux, I am using Kubuntu 11.04 and would like to remove the Kubuntu boot splash screen (blue one), but I have no idea how to proceed since apparently so many things have changed (grub,xorg,etc..) in ubuntu since last time I have had a linux OS, many years ago.

I want just the default linux boot screen with text and the [ok]'s, please can any kind soul show me how to do this?

<edit>I figured out how to do it, for anyone in the same situation here is how:

Open a terminal then type the following command:

sudo nano /etc/default/grub

then remove &#8220;quiet splash&#8221; from the GRUB_CMDLINE_LINUX_DEFAULT property, so that it shows like this:

GRUB_CMDLINE_LINUX_DEFAULT=""

Instead of this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Then save with "Ctrl+o" and quit "Ctrl+x"

Then run this command to update grub:

sudo update-grub

Voila.

One small issue remains though, even though the Kubuntu branded splash screen is gone now, I still get a blue screen during boot, any idea on how to remove this blue screen too please?

---

### Post by tbhatia4 on 2012-03-10
type this command in terminal

sudo dpkg-reconfigure gdm

and press enter on gdm
after completion reboot and it should be done

---

### Post by raja.genupula on 2012-03-10
[http://ubuntuforums.org/showthread.php?t=1603482](http://ubuntuforums.org/showthread.php?t=1603482)


[http://ubuntuforums.org/showthread.php?t=1470700](http://ubuntuforums.org/showthread.php?t=1470700)

---

### Post by tbhatia4 on 2012-03-10
i found this method to be more convenient than the one mentioned above

---

