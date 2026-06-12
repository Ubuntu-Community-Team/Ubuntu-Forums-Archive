---
title: "grub2 not timing out"
date: 2010-03-25
forum: General Help
---

### Post by imahussey on 2010-03-25
Hi all, I have a single OS, Karmic install that when booting just sits at the grub screen until I select a kernel. What I want to have happen is grub to timeout and select the most recent kernel version, which I thought would happen by default. 
here is my /etc/default/grub file

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

everything else is commented out.

From what I read about Grub 2 is that what I want to have happen is what should be happening from the way this file reads, specifically the line GRUB_TIMEOUT="10". It would be set to -1 to cause the menu to display until the user makes a selection.

---

### Post by andrewthomas on 2010-03-25
try and comment this line and see if that works

```
#GRUB_HIDDEN_TIMEOUT=0
```

---

### Post by Serpher on 2010-03-25
If you're just running that OS standalone you might want to change your GRUB_TIMEOUT from 10 to 0 for a faster boot.

---

### Post by imahussey on 2010-03-25
> **andrewthomas said:**
> try and comment this line and see if that works

```
#GRUB_HIDDEN_TIMEOUT=0
```

I commented out the line above like you mentioned and then ran the grub-update command, but this did not make any difference. Any other suggestions?

---

### Post by imahussey on 2010-03-25
Well this is why I come here to get my answers. I found a work around here [http://ubuntuforums.org/showthread.php?t=1361331&page=2]("http://ubuntuforums.org/showthread.php?t=1361331&page=2") from user meierfra. This is now working for me.

---

