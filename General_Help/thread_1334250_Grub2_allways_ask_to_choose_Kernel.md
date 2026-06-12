---
title: "Grub2 allways ask to choose Kernel"
date: 2009-11-22
forum: General Help
---

### Post by pjalegria on 2009-11-22
Hi

Every time i boot grub2 allways ask to choose kernel... how can i fix that?

Thanks

---

### Post by Rich_S on 2009-11-22
Edit your menu.lst file to remove the superfluous entries.
 
I usually just leave in the current and prior kernels (plus safe mode and memtest).

---

### Post by pjalegria on 2009-11-22
On karmic you dont have menu.lst...

---

### Post by lmarmisa on 2009-11-22
Check the parameters **GRUB_HIDDEN_TIMEOUT** and **GRUB_HIDDEN_TIMEOUT_QUIET** in the **/etc/default/grub **file

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="5"
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

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```If you have to change any parameter, type in a terminal

```
sudo gedit /etc/default/grub    #modify the parameters and save the file
sudo update-grub2
```Best regards,

Luis

---

### Post by pjalegria on 2009-11-22
Where my Grub config:


> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop pciehp.pciehp_force=1"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

Whats wrong???

---

### Post by lmarmisa on 2009-11-22
I see only a little difference (I changed 10 to 5 secs timeout):

**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop pciehp.pciehp_force=1"** # your version

**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** # my version

Regards,

Luis

---

### Post by pjalegria on 2009-11-22
I have changed /etc/init.d/rc CONCURRENCY=none to CONCURRENCY=shell, can it be the cause?

---

### Post by lmarmisa on 2009-11-22
Definitely, no!!.

Remember that Ubuntu is and will be free of charge. So it has to be completely independent of the currency that you select ;).

What do you mean with every time i boot grub2 allways ask to choose kernel?.

---

### Post by hal8000 on 2009-11-22
After running a synaptic update, sometimes a new kernel is loaded. In the past with jaunty for example the new kernel was added with a new grub stanza.

I think this has happened to pjalegria so we'll wait for his response.
I'm booting karmic from another linux distro using grub 1, as I dont like the new grub 2/

---

### Post by pjalegria on 2009-11-22
Whati mean is that every time i start, grub allways show me that menu when we have to choose the kernel, and if i dont choose anything it stays like that...

---

### Post by lmarmisa on 2009-11-22
So, there is a problem with the 10 seconds timeout. It isn't?

---

### Post by pjalegria on 2009-11-22
Yes... this very anoying, i need help please, i think this is a record fail

---

### Post by lmarmisa on 2009-11-22
Try to change 2 lines in the /etc/default/grb file.

Open a terminal and type

```

sudo bash
cd /etc/default
cp grub grub.old
gedit grub

```Modify these two lines:

**#GRUB_HIDDEN_TIMEOUT=0**

**GRUB_TIMEOUT="5"**

Save and exit.

Type this command in the terminal

```

update-grub2

```Restart the system and check if the problem is solved.

---

### Post by lmarmisa on 2009-11-22
It seems that other people have your same problem:
 
[http://ubuntuforums.org/showthread.php?p=8169691](http://ubuntuforums.org/showthread.php?p=8169691)

---

### Post by pjalegria on 2009-11-22
I found a solution :D

> That solution did not seem to work for me. However, I did find a solution that seems to work OK (and seems to be an alternate way to do something similar to your idea's end effect)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Under "13. Selected Problems" there's a little guide on commenting out a couple "recordfail" lines in /etc/grub.d/10_linux. I don't know what the risks are of doing this, but I would assume similar to the risks you listed for yours. Just posting this here in case another person stumbles across this thread searching for solution ideas.

Thanks guys

---

