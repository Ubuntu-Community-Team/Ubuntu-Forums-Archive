---
title: "Grub default miscalculation in 11.04"
date: 2011-05-05
forum: General Help
---

### Post by alphacrucis2 on 2011-05-05
I notice that 11.04 Natty has changed the grub boot menu such that older kernels are stored in a submenu under an older kernels menu item. This seems to cause either grub or startupmanager to miscalculate which is the default. For example I have just two linux kernels plus a windows OS. Setting windows to be the default via the startupmanager sets

```
GRUB_DEFAULT=6
```

in /etc/default/grub.

This ends up /boot/grub/grub.cfg as a line that reads:

```
set default="6"
```

When I reboot I find the GRUB is defaulting to the first menu item. If I manually edit the line in /etc/default/grub to read

```
GRUB_DEFAULT=5
```

and then ```
sudo grub-update
```

Then grub boots with the last entry (windows) as the default.

So it looks like grub doesn't count items in sub menus whereas startupmanager does so sets a wrong value. Not sure if it is grub or startup manager that is in the wrong here.

---

### Post by drs305 on 2011-05-05
I wrote a guide on the Grub 1.99 (Natty) submenu stucture. 

If you want to always use the latest Linux kernel, things are pretty easy. If you want to use one of the older kernels or another OS, it gets a bit trickier (as you have discovered).

Read about how the menuentries are now counted in this thread:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316")

Hint: There's a lot of stuff that will probably make your head spin. Go directly to the **Example** and read the other stuff only if you can't figure it out.  ;-)

---

### Post by alphacrucis2 on 2011-05-05
> **drs305 said:**
> I wrote a guide on the Grub 1.99 (Natty) submenu stucture. 

If you want to always use the latest Linux kernel, things are pretty easy. If you want to use one of the older kernels or another OS, it gets a bit trickier (as you have discovered).

Read about how the menuentries are now counted in this thread:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316")

Hint: There's a lot of stuff that will probably make your head spin. Go directly to the **Example** and read the other stuff only if you can't figure it out.  ;-)

Thanks. The new method makes a lot of sense. I guess the problem is that the startupmanager program hasn't caught up with the change. I note now that someone has already reported in launchpad. I disagree with their conclusion though. They are blaming grub whereas I think startupmanager is at fault.

[https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/775292](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/775292)

---

### Post by drs305 on 2011-05-05
StartupManager has limited capabilities when it comes to Grub 2.

There is a newer GUI grub manager called Grub Customizer which was created for Grub2. It's a great app for those that don't like manually editing the configuration files.

I haven't checked to see how it handles the submenus - it's on my list of ToDo's when I finish my vacation. I did write a guide about how to install and use it. See the "Customizer" link in my signature line.

---

### Post by alphacrucis2 on 2011-05-05
I will give GRUB Customizer a try. Cheers

---

