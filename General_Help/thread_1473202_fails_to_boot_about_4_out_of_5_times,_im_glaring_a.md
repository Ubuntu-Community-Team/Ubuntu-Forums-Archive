---
title: "fails to boot about 4 out of 5 times, im glaring at plymouth."
date: 2010-05-05
forum: General Help
---

### Post by earthpigg on 2010-05-05
Well, i think it's plymouth.

my computer fails to boot about 4 out of 5 times. i get a blinking underscore in the upper left corner (_), and nothing else.

when it DOES boot, the words 'plymouth' and 'error' and a bunch of other stuff flash by the screen very quickly, no pretty graphical plymouth ubuntu logo displays, and i get to the login screen. i have an ssd, so that takes all of about two heartbeats... way to fast to read (it would appear ubuntu has achieved it's goal of booting fast, unfortunately for me :P ).

i took a break from ubuntu for a while because 9.04 did not support my i7 mobo well - probably because it was newer than the 4th month of 2009 (understandable, and why we have rolling release distros). i strongly doubt it is a hardware issue, as i haven't had any hardware issues in the past and this appeared *exactly* upon my first install of ubuntu 10.04 a few days ago. i've reinstalled twice since then (yup, verified install media integrity).

i haven't found any pattern as to what causes the issue through the various reinstalls.

1) which log file(s) should i be looking at? i'm pretty sure it's past bios when i get to the blinking cursor issue -- my keyboards backlighting turning off/back on has always been my little indicator that bios is done, and OS has taken over.

2) any specific software i could install that would definitively log failed boot attempts?

3) any way to disable plymouth and replace it with something else? google has yielded negative results to that question ( [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531331](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531331) ) but maybe someone knows something i dont.

4) any other advice or suggestions?


edit:

take a look at this, in /etc/init/plymouth-splash.conf

```
# plymouth-splash - Show the splash screen
#
[B][I]# plymouth must be started ASAP to avoid racing with gdm, but the splash
# screen can't be spawned until our framebuffer is available.  Wait for the
# video device to be available before showing the screen, or, if udevtrigger
# finishes without finding any video devices, bring up the fallback text
# interface.[/I][/B]
# We also *should* wait for the filesystem to be up because of the libraries
# being used from /usr/lib, but this would cause a circular dependency if
# any interaction at all is required for mounting a filesystem; so these libs
# need to be moved to /lib instead.et

description	"Userspace bootsplash"

start on (started plymouth
          and (graphics-device-added PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))

exec /bin/plymouth show-splash
```

think that may be related? recall the ssd

edit 2:

and this:

[https://lists.ubuntu.com/archives/lucid-changes/2009-December/001486.html](https://lists.ubuntu.com/archives/lucid-changes/2009-December/001486.html)

>    * debian/initramfs-tools/conf-hooks.d/plymouth:
     - Always enable the framebuffer for now, on the SSD model we end up
       crashing X while faffing with the splash screen; it's better to just
       delay it for now.


[https://launchpad.net/ubuntu/lucid/+source/plymouth/+changelog](https://launchpad.net/ubuntu/lucid/+source/plymouth/+changelog)

>   * Added initramfs conf that enables the framebuffer and plymouth unless
    the root disk is on SSD.  The rationale is that SSD-based systems get
    to the point where we can start plymouth in the real system just as


---

### Post by GSF1200S on 2010-05-05
Xubuntu 10.04 only booted once before this issue happened for me. I appended 
```
nomodeset
```
to the following line in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
so that it looked like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Then I ran:
```
sudo update-grub
sudo update-initramfs -u
```

You can also try omitting quiet and splash as well if you still have issues (remember to run the two update commands again). Im using v86d to render plymouth with VESA which allows plymouth to work without (mostly) the flashing underscore. Heres the URL that worked for me:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

If you have an intel chip, use:
```
i915.modeset=0
```
instead of:
```
nomodeset
```
which is what I use for my nvidia card. Im not sure what would work for an ATI card.

Good luck.. If its any consolation, Arch Linux is currently not even booting with Nvidia drivers enabled (on my system; have to !nvidia in the modules line if youre familiar with arch), so lucid isnt alone in the issues :(

---

### Post by earthpigg on 2010-05-05
actually... arch is what i am migrating from, back to ubuntu.

> If you have an intel chip, use:
Code:

i915.modeset=0

an intel CPU, or intel integrated video?

i have an intel i7 cpu, and nvidia gts 250 video.

---

### Post by GSF1200S on 2010-05-05
> **earthpigg said:**
> actually... arch is what i am migrating from, back to ubuntu.



an intel CPU, or intel integrated video?

i have an intel i7 cpu, and nvidia gts 250 video.

Sorry for the lack of clarification ;) If you have an Nvidia GPU, use nomodeset. By intel chip, I meant intel graphics device.

Going to edit that post now in case it confuses others.

Let me know if it works please...

---

### Post by k3lt01 on 2010-05-05
> **GSF1200S said:**
> If you have an intel chip, use:
```
i915.modeset=0
```
instead of:
```
nomodeset
```
which is what I use for my nvidia card. Im not sure what would work for an ATI card.Well, if I may just interject a little here, a Dev told me to put i915.modeset=1 and that worked for me.

---

### Post by earthpigg on 2010-05-05
> **GSF1200S said:**
> Let me know if it works please...

i absolutely will, next time i restart.

first, i must finish watching a show on hulu and then finish downloading the [humble bundle]("http://ubuntuforums.org/showthread.php?p=9239481#post9239481") :D

---

### Post by GSF1200S on 2010-05-05
> **earthpigg said:**
> i absolutely will, next time i restart.

first, i must finish watching a show on hulu and then finish downloading the [humble bundle]("http://ubuntuforums.org/showthread.php?p=9239481#post9239481") :D

Haha, cool..

To the guy who responded with 'i915.modeset=1' that is interesting. In another thread a guy tried i915.modeset=0 and it worked for him (as well as for others trying after him)- thats where I got it from as I have no experience with intel cards. Ill keep that in mind if I see any other intel users who have an issue... What intel gpu do you have?

---

### Post by dino99 on 2010-05-05
if things goes wrong with plymouth: remove/purge it then reinstall

if graphic driver is well activated ( ie nvidia-current into system admin hardware driver) that means the problem is not there.

sudo dpkg --configure -a

install gconf-cleaner and use it

---

### Post by k3lt01 on 2010-05-05
> **GSF1200S said:**
> Haha, cool..

To the guy who responded with 'i915.modeset=1' that is interesting. In another thread a guy tried i915.modeset=0 and it worked for him (as well as for others trying after him)- thats where I got it from as I have no experience with intel cards. Ill keep that in mind if I see any other intel users who have an issue... What intel gpu do you have?Mine is an Acer laptop setup with an Intel 855. 

This is my original [Bug Report]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379") on the issue. It may help if you could point others you come across to it.

n.b. Plymouth was crap in Pre-Alpha, Alpha 1, and Alpha 2. It worked from Alpha 3 on right through to the Lucid RC, with a slight hiccup when the 2.6.32-21 kernel was released in testing (thus the bug report). Now we are in a public release Plymouth has stopped working properly again but I can still boot easily with that setting. It's just a shockingly bitsa looking thing now.

---

### Post by GSF1200S on 2010-05-05
> **k3lt01 said:**
> Mine is an Acer laptop setup with an Intel 855. 

This is my original [Bug Report]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379") on the issue. It may help if you could point others you come across to it.

n.b. Plymouth was crap in Pre-Alpha, Alpha 1, and Alpha 2. It worked from Alpha 3 on right through to the Lucid RC, with a slight hiccup when the 2.6.32-21 kernel was released in testing (thus the bug report). Now we are in a public release Plymouth has stopped working properly again but I can still boot easily with that setting. It's just a shockingly bitsa looking thing now.

Ive got it bookmarked now.. If I see any others with the problem Ill let them know about it :) 

I went in at Beta 2 on Lucid, but it never worked for me. Eventually I got it working using v86d (rendering with vesa). I still have a few underscore flashes right at first, but otherwise it looks fine. I usually leave it disabled though as I prefer to see the kernel do its thing..

Thanks for the info :)

---

### Post by earthpigg on 2010-05-05
it seems to be working, by the way. 3 boots in a row.

thanks!

---

### Post by GSF1200S on 2010-05-05
> **earthpigg said:**
> it seems to be working, by the way. 3 boots in a row.

thanks!

I just found out today why Arch would not boot: the 195 drivers and the kernel version Arch is using causes a conflict when the computer has 2 video cards (unfortunately for me)- works fine otherwise :(

Glad its working for you now :)

---

### Post by earthpigg on 2010-05-10
thread marked as **unsolved**.

after following the directions above, in post #2, i rebooted and it booted fine.

after that, the problem presented again: it took several reboots before booting and, when it did, presented some plymouth error messages.

and it happened again, the next few times i rebooted or attempted to reboot.

so, i verified that /etc/default/grub still had:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

ran the next two command, and rebooted again.

and once again, booted perfectly on first attempt.

until the next reboot, again, when the problem came back.

so, as it stands, i can shut down and be guaranteed a perfect startup... as long as i run:

> sudo update-grub
sudo update-initramfs -u

before shutting my computer down or restarting it, every single time.

i have not tried this yet:

> You can also try omitting quiet and splash as well if you still have issues (remember to run the two update commands again). 

---

### Post by earthpigg on 2010-05-11
bump

problem persists, and tried this:

> i have not tried this yet:

[QUOTE]Quote:
You can also try omitting quiet and splash as well if you still have issues (remember to run the two update commands again). [/QUOTE]

---

### Post by Danijz on 2010-07-07
I have exactly the same problem with my Ubuntu 10.04 and Nvidia. has anyone found a solution yet??

---

### Post by earthpigg on 2010-07-07
no, but i don't think it is plymouth. i keep trying to remember to write down the error message i see when the boot process halts, but am just in the habbit of rebooting now. tsk tsk on me.

something about USB, but i suspect that error message is misleading, as i tried unplugging every USB device except a keyboard. tried alternative keyboard. problem persisted.

---

