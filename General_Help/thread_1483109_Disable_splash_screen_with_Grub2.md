---
title: "Disable splash screen with Grub2"
date: 2010-05-14
forum: General Help
---

### Post by walterbyrd on 2010-05-14
I am using 10.04, which uses Grub2, and I can not even find the menu.lst file, or whatever it's called now.

---

### Post by drs305 on 2010-05-14
Grub2 uses a completely different file structure. There are now lots of sites that describe the differences. Here are a couple, and there are some extra links in my signature line.

[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by bigbaraboom on 2010-05-20
Hi I don't mean to hijack the thread, but I'm having a similar issue. I've read about grub2, but the behavior i'm experiencing is very odd considering the changes I have made.
First thing I always did on a clean Ubuntu install is edit menu.lst so that I could see the boot steps text. As grub2 is now considered "better" that grub legacy, my goal is to achieve the same result. For some reason it is not working. These are contents of /etc/default/grub
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset noplymouth"
#GRUB_CMDLINE_LINUX="text"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

When booting, I get the Grub menu (in 800x600 resolution), as soon as I select the kernel of choice, the resolution switches to default (something very large and unreadable). I tried many different configurations (including GRUB_GFXPAYLOAD_LINUX=keep), as well as **lots** of different numbers. 
My native resolution is 1366x768 on a Dell Inspiron 1545 notebook, and while it would be nice to have that at boot I would be perfectly ok with something lower, as long as it's readable. I never made the switch to Karmic, but in Jaunty I had vga=0x0318 at the end of the kernel line (in menu.lst) working perfectly good.

---

### Post by Nythain on 2010-05-20
i followed this guide

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

almost to a tee, except i removed the quiet and splash of course... now i have a wonderful 1600x1200 24bit virtual terminal

---

### Post by bigbaraboom on 2010-05-20
That seems to fix the resolution and messy display of the boot text.

However, if I remove "quiet", the first steps ([1.xxxxx,...,3.xxxxx])are still displayed in default resolution. Following [3.xxxxx] it switches to the value given in GRUB_GFXMODE. Keeping "quiet" hides the first steps and starts out after [3.xxxxx]. Is it possible to have the first steps displayed in the same resolution passed to GRUB_GFXMODE?

On another note, when removing "splash", do you still need this pipe?
```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```

---

