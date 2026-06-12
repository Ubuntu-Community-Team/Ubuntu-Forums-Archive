---
title: "Re: problems after installation on AMD Athlon 64"
date: 2010-09-22
forum: General Help
---

### Post by newbemac on 2010-09-22
ME TOO.  I have been reading the posts for days with no luck  I have a toshiba L505D LS5002.  I HAVE INSTALLED 10.04 IN A DUEL BOOT WITH WIN 7.  however i can't get ubuntu to boot.

---

### Post by CharlesA on 2010-09-22
I split yer post from the original thread, since the original thread was talking about a different problem.

We'd need more info to narrow down what the problem is.

What happens when you try to boot Ubuntu?

---

### Post by newbemac on 2010-09-22
ok here goes.....
from the disk, (ubuntu 10-4.1 64 bit on a toshiba L505D LS5002 ) grafics card  AMD M860G WITH RAEDEON 4100.  I must place an X next to acpi=off, otherwise i get a black screen with many lines of letters and numbers.

once the disk boots up and start the install.  I selected to use the entire hard drive, the install was uneventful.  upon reboot i get a black screen of giberish just like above and the laptop freezes.
from terminal I type sudo fdisk -l and that shows:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ae68d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29747   238941184   83  Linux
/dev/sda2           29748       30402     5255169    5  Extended
/dev/sda5           29748       30402     5255168   82  Linux swap / Solaris

ubuntu@ubuntu:~$ from terminal  grub-install -v    shows  gnu grub 1.98-lubuntu7
windows 7 is now gone and ubuntu does not work.  any thoughts anyone?

thanks
tom

---

### Post by CharlesA on 2010-09-22
Try holding down shift when booting so that the grub menu comes up. select the first one and hit e to edit. Add "acpi=off" before quiet splash

---

### Post by newbemac on 2010-09-22
ok I hold down the shift key when booting, e for edit, and i addes acpi=off before the quiet spash.  the os boots at that point, thanks this is the closest i'v gotten in 4 days.  however..i have to do this every time i start up.     gotta be a better way
thanks for you help

---

### Post by CharlesA on 2010-09-22
Did it boot successfully?

Hit Alt+F2 and type this:

```
gksu gedit /etc/default/grub
```

Then look for the line that looks like this (it's around line 9):

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Change it so it looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="apci=off quiet splash"
```

Save it then hit Alt+F2, select the "run in terminal" check box and type in:

```
sudo update-grub
```

Hit enter and type in yer password, and after that window closes, reboot the machine. It should come up ok.

---

### Post by newbemac on 2010-09-23
Could not open location 'file:///home/tom/%5Bcode%5Dgksu%20gedit%20/etc/default/grub%5Bcode%5D'
Error stating file '/home/tom/[code]gksu gedit /etc/default/grub[code]': No such file or directory

this what appears!

---

### Post by newbemac on 2010-09-23
Could not open location 'file:///home/tom/%5Bcode%5Dgksu%20gedit%20/etc/default/grub%5Bcode%5D'
Error stating file '/home/tom/[code]gksu gedit /etc/default/grub[code]': No such file or directory
i did so and obtain an error messeage.  it seems there is no grub

---

### Post by CharlesA on 2010-09-23
D'oh! Forgot to close the code tag. Try it now.

---

### Post by newbemac on 2010-09-23
Ok I followed your instructions and saved the changes.  I closed down and got the purple screen with Ubuntu on it and watched the 5 dots change to red. system hung there and I had to hit the off button.  when I turned the machine ubuntu tried to boot and the screen displayed;

---

### Post by newbemac on 2010-09-23
I forced quit and went through the rebooting process.  went to terminal and checked the changes

 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=[COLOR="Yellow"]"apci=off quiet splash"[/COLOR]
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

was displayed.

---

### Post by newbemac on 2010-09-23
I forced quit and went through the rebooting process.  went to terminal and checked the changes

 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=[COLOR="Yellow"][COLOR="Red"]"apci=off quiet splash"[/COLOR][/COLOR]
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

was displayed.

---

### Post by newbemac on 2010-09-23
sorry for the repeats my bad

---

### Post by CharlesA on 2010-09-23
Please don't spam yer own thread with the same post.

If adding apci=off worked in the initial boot, it should work after updating grub.

Try hitting e and removing "quiet splash" and booting it to see if it displays any errors.

---

### Post by newbemac on 2010-09-23
i tried as instructed, does not boot unless hold shidt use e and place acpi=off before quiet splash.
thank you for all you help

---

### Post by CharlesA on 2010-09-23
I see the mistake. It was a typo on my part (again >.<)

It should be "**acpi=off**" not "apci=off"

Try correcting the error and running:

```
sudo update-grub
```

Then reboot.

For more info about Grub2, check out the thread [here]("http://ubuntuforums.org/showthread.php?t=1195275").

---

### Post by newbemac on 2010-09-24
i have re-installed windows 7, i give up.  thanks to all for your help.

i continue to use ubuntu on my main desktop and love it.  but this toshiba laptop does not seem to like linux

---

### Post by CharlesA on 2010-09-24
Use what works.

Best of luck with it. :)

---

