---
title: "Random, Constant Fan(like) Noise - Laptop"
date: 2011-05-16
forum: General Help
---

### Post by user1397 on 2011-05-16
So I just bought a new laptop, I've had it for about 3 weeks now.  Here are the basic specs:

-15" screen
-core i3 330M
-4gb ram
-intel HD graphics
-5400rpm 320gb hard drive (sata)

Ever since I've first turned it on I've noticed that it makes a certain noise at a sort of constant pattern.  It'll do it for a few seconds, then stop for a minute or two, then do it again.  This happens pretty much the whole time it is turned on.

Now it sounds like a fan that cranks itself up excessively for short bursts, or it could be the hard drive (I don't really think it is the HD, but then again I don't know what a HD sounds like since I haven't heard one since the pentium III days...).

Other than this, which is actually more of an auditory annoyance, the computer runs flawlessly.

Question is, what could be causing this, and is there a way to stop it?

---

### Post by Hedgehog1 on 2011-05-16
Here is a likely solution to bring the fan under control:

To improve the function of the laptop fan using 'current' grub options:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by user1397 on 2011-05-16
Thanks hedge, I'm gonna try this when I get home.  I forgot to mention I dual boot this laptop with windows 7, and the problem also occurs in windows.  Any idea on how to fix it in windows?

Thanks in advance.

---

### Post by Hedgehog1 on 2011-05-16
> **ubuntuman001 said:**
> Thanks hedge, I'm gonna try this when I get home.  I forgot to mention I dual boot this laptop with windows 7, and the problem also occurs in windows.  Any idea on how to fix it in windows?

Thanks in advance.

No yet - I have not taken the time to make the fan in the windows side of my dual boot work better.  If I spent more time there, I know I would make the effort...  By the Ubuntu side just screams, so I really don't use the windows side that much any more...

***The Hedge***

:KS

---

