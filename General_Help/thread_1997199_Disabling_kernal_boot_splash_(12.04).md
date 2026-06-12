---
title: "Disabling kernal boot splash (12.04)"
date: 2012-06-04
forum: General Help
---

### Post by sundays211 on 2012-06-04
Hi,
I have previously managed to remove the bulk of the Ubuntu 12.04 boot splash screen (by removing the "quiet splash" line in the grub configuration file), but the purple splash screen still lingers on for around 5-10 seconds after selecting the entry from the bootloader, hiding many of the initial kernel verbose. 

Any ideas?

---

### Post by idoitprone on 2012-06-05
> **sundays211 said:**
> Hi,
I have previously managed to remove the bulk of the Ubuntu 12.04 boot splash screen (by removing the "quiet splash" line in the grub configuration file), but the purple splash screen still lingers on for around 5-10 seconds after selecting the entry from the bootloader, hiding many of the initial kernel verbose. 

Any ideas?
```

sudo update-grub 
```? did you run it?

---

### Post by satish_j on 2012-06-05
> **sundays211 said:**
> Hi,
I have previously managed to remove the bulk of the Ubuntu 12.04 boot splash screen (by removing the "quiet splash" line in the grub configuration file), but the purple splash screen still lingers on for around 5-10 seconds after selecting the entry from the bootloader, hiding many of the initial kernel verbose. 

Any ideas?

same at my side.if you get the answer to it,do mention the solution in the forum..
BTW,'update-grub' did not helped..

---

### Post by idoitprone on 2012-06-05
> **satish_j said:**
> same at my side.if you get the answer to it,do mention the solution in the forum..
BTW,'update-grub' did not helped..

i am just here to make sure you remove a common error of not updating grub.cfg file

---

### Post by sundays211 on 2012-06-05
> **idoitprone said:**
> ```

sudo update-grub 
```? did you run it?
Yes, I have run update-grub, which successfully removes the usual loading process (where it displays the dots changing from purple to white) and replaces it with part of the verbose loading. 

However, I still have the purple screen remaining for around 10 seconds before going into the verbose, and trying to remove this seems to be a lot more difficult than removing the 'quiet splash' parameters

---

### Post by sundays211 on 2012-06-05
After a bit of digging, I've found that uncommenting ```
GRUB_TERMINAL = "console"
```  in the grub configuration file does seem to remove the splash instantly after leaving the boot menu. 
But it also brings a string of problems of its own, such as not allowing a decent screen resolution of the boot menu and removing any customization whatsoever. So it's not really the answer I'm looking for, nor I'm sure is it the answer many readers would want.
Still, it's something.

---

### Post by cann on 2012-07-18
I usually change these lines in my grub config to get standard VGA for my servers.

```

nano  /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
#GRUB_TERMINAL=console
#GRUB_GFXMODE=640x480

```

to 

```

# GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_TERMINAL=console
GRUB_GFXMODE=640x480

```

And then run update-grub.
of course you could set whatever resolution you want with GRUB_GFXMODE.

---

### Post by jpka on 2012-11-07
> **sundays211 said:**
> After a bit of digging, I've found that uncommenting ```
GRUB_TERMINAL = "console"
```  in the grub configuration file does seem to remove the splash instantly after leaving the boot menu. 


Thank you, it is very helpful and work for Ubuntu Server 12.04.1. Brings back to native 80x25 text mode OS immediately. While tons of other solutions like "nomodeset"s just not work. Thank you for saving people's eyes! :KS :KS :KS :KS :KS

---

