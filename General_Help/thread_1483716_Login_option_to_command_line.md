---
title: "Login option to command line"
date: 2010-05-14
forum: General Help
---

### Post by dcb97470 on 2010-05-14
Does anyone know how?  I want to add the command line option to the login to.  So, I have Gnome, KDE and command line.

Dean

---

### Post by patchwork on 2010-05-14
Rather than trying to add a command line session, you can use CTRL ALT F2 to drop into the command line.

---

### Post by dcb97470 on 2010-05-14
Well, there are times that I want to run all from cmd line.

Dean

---

### Post by patchwork on 2010-05-14
CTRL ALT F2 (not to be confused with ALT F2) will drop you to a tty session, leaving the X server.  If I understand you correctly, this is what you are looking for.



EDIT:  To re-enter the GUI mode, you can press CTRL ALT F7

---

### Post by BoneKracker on 2010-05-15
I don't use ubuntu, but you can probably find a way to boot into a non-graphical mode, completely avoiding the need to start up the X server (and other services you might not want while in cli mode).

The normal way to handle this is via runlevels.

As I understand it, you guys boot into runlevel 5 by default, and it's configured to be a graphical runlevel.

Try booting into runlevel 3 or 4 instead.

All you need to do is append 3 or 4 to the end of the kernel boot line.



During bootup, tell grub you want to edit the boot line, and just stick a 3 on the end (actually a space and then the numeral 3).

If you're going to boot into a non-graphical level frequently, you might want to create a grub menu option that permanently includes that bootline (with the 3 or 4 on the end).

If it turns out that runlevel 3 (or 4) doesn't have a service running that you need (it probably has networking, but it might not, for example, have sound), you can just add whatever services you need to the runlevel.

I would refer you to the distro-specific documentation for your init system (or you might call it an "rc system").

There are many other things you can configure via bootline options:
[http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch10.html](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch10.html)

---

### Post by patchwork on 2010-05-15
> As I understand it, you guys boot into runlevel 5 by default, and it's  configured to be a graphical runlevel.

Try booting into runlevel 3 or 4 instead.

All you need to do is append 3 or 4 to the end of the kernel boot line.

Believe it or not, Ubuntu boots into run level 2 and stays there (unless in single user mode).

```
kevin@lucid:~$ runlevel
N 2

```

---

### Post by BoneKracker on 2010-05-15
Oh.  That's unusual.  :p

Anyway, it doesn't matter.  Booting into a non-graphical runlevel is the best way to do this.  Same thing applies.  Try booting into runlevel 3 and see what happens.

Ubuntu may also have some internal "dynamic runlevel management" capability that would allow you to boot into a logical equivalent of a different runlevel even though you're technically still in runlevel 2 as far the underlying sysvinit system knows (my distro calls them "softlevels").

If booting into runlevel 3 doesn't work, I'd refer to the documentation for the init system.  It may already be configured to provide this via a bootline option such as "nox".

---

### Post by dcb97470 on 2010-05-19
ok, I still need help with this.  Is there a way to add a cmdline option to the grub or cmdline runlevel to grub?

Dean

---

### Post by BoneKracker on 2010-05-19
> **dcb97470 said:**
> ok, I still need help with this.  Is there a way to add a cmdline option to the grub or cmdline runlevel to grub?

Dean

Yes.  However, I don't use grub2, like you Ubuntuans do, so you'll have to get help from one of your fellow Ubuntuans.  You need to go into the /boot directory and edit a file.  If you have a separate /boot partition (which you probably don't), then you'd have to mount the /boot partition first.

I think there would be two possible approaches:

_a) The preferable approach _will allow the system to automatically (each time you run the update-grub script) create an updated menu entry for you containing the runlevel parameter at the end of the bootline. This is possible, but a more advanced task than the alternative approach (b) below.  I think it would require editing of the file /boot/grub/grub.d/10_linux.  I can't help you with it because I don't know what exactly is in that file.  I believe update-grub is a Debian thing.

The bottom line is that this file contains configuration information used by the update-grub script to create a number of grub menu entries.  I believe this is done for each kernel that is currently installed.  You want it to create one additional menu entry.  You should be able to simply duplicate the section pertaining to the primary menu entry (the "normal" one, not the rescue shell or whatever), adding the additional parameter (the runlevel number) to the end of the bootline.  I don't know what that "10_linux" file looks like, but you must change it such that, when update-grub runs, it produces an additional menu entry within the automatically-generated file /boot/grub/grub.cfg.  As an example, if your primary menu entry in /boot/grub/grub.cfg looked like this:```

menuentry 'Ubuntu, with Linux 2.6.32-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 444539ba-ab9e-4028-94f5-c1a86b5ec7c1
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=444539ba-ab9e-4028-94f5-c1a86b5ec7c1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
```
Then the additional menu entry (automatically created by 'update-grub' in /boot/grub/grub.cfg as a result of your edits to /boot/grub/grub.d/10_linux) would look identical except for the addition of the runlevel number at the end of the bootline:```

menuentry 'Ubuntu CLI Mode, with Linux 2.6.32-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 444539ba-ab9e-4028-94f5-c1a86b5ec7c1
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=444539ba-ab9e-4028-94f5-c1a86b5ec7c1 ro   quiet splash 3
	initrd	/boot/initrd.img-2.6.32-16-generic
}
```[B]
Note the addition of the numeral '3' after the bootline parameters 'quiet' and 'splash'.[/B]

This is probably trivial to achieve, but I don't know for sure because I myself don't have that 10_linux file, don't use grub2, and don't use an 'update-grub' script.

_b) The alternative approach_ would be simply creating a file in /boot/grub/grub.d containing the information necessary for the menu option (e.g., "40_custom").  This file would be static (would not be updated automatically by the update-grub script.  Therefore, when you upgrade your kernel, you'd have to go in and edit the script so it has the name of the new kernel instead of the old.  This process is probably documented and should be easier for somebody to walk you through.

Sorry that I personally can't give you more on this.  You can get some information here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

**Hopefully an advanced Ubuntu user will jump in here and help you with the details.** :)

---

### Post by new_tolinux on 2010-05-19
> **dcb97470 said:**
> ok, I still need help with this.  Is there a way to add a cmdline option to the grub or cmdline runlevel to grub?

Dean
Yes. I added the word "text" at the end of the line (without quotes) and it boots in command-line mode.

You can even startx after you're logged on if you need to.

---

### Post by BoneKracker on 2010-05-19
There you go.  That's like the "soft" runlevels I was referring to earlier.  You can probably use that, or you can use a number (and they may not mean exactly the same thing -- one may have services running the other doesn't -- you'd have to consult Ubuntu init system documentation).

To apply that to what I just posted above, you'd simply put 'text' where I had '3'.

**If an advanced Ubuntu user could review those suggested modifications to /boot/grub/grub.d/10_linux, and provide some insight on specifically what changes would be required (beyond my generalities), that would still be helpful to the OP.**

---

