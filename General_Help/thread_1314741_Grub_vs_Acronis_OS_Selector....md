---
title: "Grub vs Acronis OS Selector..."
date: 2009-11-04
forum: General Help
---

### Post by Himself2007 on 2009-11-04
Hello

On this computer I have Windows XP and Ubuntu 9.10.
Because Ubuntu is new for me, i'm still not ready to have it as my default OS.
For now XP should be my default OS and Ubuntu...my "learning project".

Actually on Computer startup, Grub (Version 1.97 beta 4) is offering me the choice of OS selection.
And it has Ubuntu as the default OS, with a countdown.
I know we can select Ubuntu or XP from here, anyway.

Question #1 : I could continue using Grub if I could change de default OS to be Windows XP.
                      And manually select Ubuntu if I want to.
                      So how can I change the default OS here in GRUB?
                      The reason is to have needed default OS startup with only computer power ON switch.

Question #2 : I could install Acronis OS Selector from their Disk Director suite.
                      I used it for a long time and it works fine.
                      This solution have its advantage of offering to select default OS we prefer.
                      But Grub would be useless.
                      It's still gonna work if I leave it but the startup time increases for nothing as the process is redondant.
                      And illogical if I previously chose to have XP on startup because I have to re-select XP again.
                      So how can I have Grub to not execute after execution of OS selection after Acronis OS selector?

Luc

PS. I wish I was clear! I know...:neutral:

---

### Post by Giblet5 on 2009-11-04
The default OS is determined by GRUB_DEFAULT in /etc/default/grub.

The default is 0 (first menu entry).

If Windows is the 4th menu item, then GRUB_DEFAULT=3 will make it boot Windows by default.

0
1
2
3

But that's retarded because the moment a new kernel is released, item #3 will no longer point to Windows: a new linux kernel was added above it, plus a recovery version of that kernel, so #3 will point somewhere that you did not intend...

I use GRUB_DEFAULT=saved and it will simply boot whatever I booted last.

Once you make the change, install the changes via ```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

---

### Post by Himself2007 on 2009-11-04
> **Giblet5 said:**
> The default OS is determined by GRUB_DEFAULT in /etc/default/grub.

The default is 0 (first menu entry).

If Windows is the 4th menu item, then GRUB_DEFAULT=3 will make it boot Windows by default.

0
1
2
3

But that's retarded because the moment a new kernel is released, item #3 will no longer point to Windows: a new linux kernel was added above it, plus a recovery version of that kernel, so #3 will point somewhere that you did not intend...

I use GRUB_DEFAULT=saved and it will simply boot whatever I booted last.

Once you make the change, install the changes via ```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

Hello Giblet5

Thanks for fast reply!
Interesting suggestion!
Your idea of configuring Grub..."simply boot whatever I booted last" is very interesting.
So doing your suggested code lines will produce that result?
Can you confirm please?
Thanks

Luc

---

### Post by Giblet5 on 2009-11-04
> **Himself2007 said:**
> Hello Giblet5

Thanks for fast reply!
Interesting suggestion!
Your idea of configuring Grub..."simply boot whatever I booted last" is very interesting.
So doing your suggested code lines will produce that result?
Can you confirm please?
Thanks

Luc

First, you'll have to set the configuration: ```
sudo gedit /etc/default/grub
```

GRUB_DEFAULT is near the top. Change:

GRUB_DEFAULT=0

to

GRUB_DEFAULT=saved

Then save the file and exit gedit.

Now enter the commands to install the changes: ```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

(You'll want to use copy/paste with that last command - the quote syntax is important and non-obvious.)

---

### Post by Himself2007 on 2009-11-04
Giblet5

Gee I don't believe this.
It works and works perfectly!
Short and sweet.
I will even try to shorten the countdown time.
With all questions I've been answered for the last 24 hours in the forum I think I went much further in understanding the terminal and Synaptic PM.
Thanks very much for your help Giblet5.
You've been very helpful!

Luc

---

