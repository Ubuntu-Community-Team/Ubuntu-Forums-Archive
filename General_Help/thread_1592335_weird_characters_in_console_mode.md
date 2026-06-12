---
title: "weird characters in console mode"
date: 2010-10-10
forum: General Help
---

### Post by kung fu buntu on 2010-10-10
I'm getting a weird charset problem in a chroot'ed system that I kexec'ed into. It is especially noticeable in ncurses programs like aptitude, but it also noticeable in vim.
Since one picture is worth more than one thousand words: [http://www.uploadgeek.com/image-AE48_4CB1F6F6.jpg](http://www.uploadgeek.com/image-AE48_4CB1F6F6.jpg)

My locales are configured to en_US.UTF-8, I have choosen my keyboard layout with kbd-config while in the chroot before kexec'ing into it, I've passed the bootkbd= parameter to the kexec'ed kernel, and my TERM variable is set to "linux".
What is the problem?

I can't try xterm because this chroot system doesn't has X.

EDIT: I just noticed that the keyboard layout I selected is not working properly. All keys work fine except the ones that are specific to my country. Instead of ç I get a weird symbol.

Thanks


EDIT2: I kind of solved this, although it's still not a proper solution IMO:
Purge console-tools, install console-setup and kbd. Then
dpkg-reconfigure console-setup
dpkg-reconfigure keyboard-configuration
For proper keyboard at boottime:
dumpkeys | gzip > /etc/boottime.kmap.gz
and then update initramfs image

The only problem is that there is a glitch when booting into the system because the backspace key prints garbage (even though it deletes characters) on the console login menu

---

