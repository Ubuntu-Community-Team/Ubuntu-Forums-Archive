---
title: "Understanding Partitions"
date: 2009-09-07
forum: General Help
---

### Post by cambunctious on 2009-09-07
This is my first post and this looks like the right place to get help!

I installed Ubuntu Netbook Remix 9.04 on my Asus Eee 1005HA in the unallocated space on my hard drive for fun :).  Very cool!  But when I tried to hibernate, I got an error about the swap being too small.  I then read somewhere that the swap should be 2x your RAM so I fired GParted on the live CD (thumb drive) and took space from my Windows partition to grow the ext3 and the swap.  I think I got some errors here and had to try a few times before it worked.  Thank goodness Windows is still working fine but now when I start Ubuntu I see some Terminal lines (or whatever you call them) that didn't show before.  And when I try to hibernate, It says it can't find the swap at all.  Instead of trying to get the swap to work I would rather just start over.  I see four partitions.  I'm pretty sure they are Windows, ext3, and swap, but I don't know what the last one is.  It's 32MB and I think it might be the boot thing that shows the list of operating systems.

**Would it be safe to delete/format the last three partitions?**  What is the "right way" to uninstall Ubuntu?

Thanks in advance!

---

### Post by CatKiller on 2009-09-07
> **cambunctious said:**
> Instead of trying to get the swap to work I would rather just start over.  I see four partitions.  I'm pretty sure they are Windows, ext3, and swap, but I don't know what the last one is.  It's 32MB and I think it might be the boot thing that shows the list of operating systems.

**Would it be safe to delete/format the last three partitions?**  What is the "right way" to uninstall Ubuntu?

If you're using GRUB as your bootloader, it doesn't have its own partition; it (the first stage, anyway) goes in the Master Boot Record, with the other stages on normal partitions. So I think that other partition might be some kind of recovery partition. I've never used an Eee, so I don't know for sure that it has one, but that would be my guess.

Getting the swap for hibernate to work is probably only a case of editing two or three files. There's **/etc/fstab**, which is the **f**ile**s**ystem **tab**le file; this tells the system which partitions to mount when you boot the computer. Another is **/etc/uswsusp.conf**, which configures the **u**serspace **s**oft**w**are **susp**end; if your hardware supports hibernation then I don't think you need to do anything to the second file - it's for people whose hardware can't do it through hardware. The third file is **/boot/grub/menu.lst**. This contains boot options, including where the system should look for an image to resume from.

The first task is to update your fstab with the details of your new swap partition. ```
gksudo gedit /etc/fstab
``` will open the file for editing. You should see a line that looks like ```
UUID=5fc0504d-441e-41f0-a367-c0f9342e894e       none            swap    sw              0       0
```You need to change that UUID number so that it's the right one for your new swap partition. You can find out the UUID for your swap partition with ```
sudo vol_id -u /dev/sda*n*
``` where *n* is the partition number of your swap partition.

If you do ```
sudo swapon -a
``` once you've done this, you may find that it all just works because you have hardware support.

If not, then you'll need to edit the other two files.

```
gksudo gedit /boot/grub/menu.lst
``` will open that file for editing. Somewhere you may find a section that says something like ```
resume=UUID=5fc0504d-441e-41f0-a367-c0f9342e894e
``` This may be in the *defoptions* line (for setting the options for new kernels) as well as in the kernel lines for the existing boot options. Change this UUID number to the correct one, as you did in /etc/fstab.

```
gksudo gedit /etc/uswsusp.conf
``` will open the last file for editing. The *resume device =* line does what you'd imagine; sets the location for the image to be stored. You can specify the setting simply as /dev/sda*n* that you used before.

If that all doesn't work, you can feel free to reinstall anyway, safe in the knowledge that you've learned a bit more about how your computer works.

---

### Post by cambunctious on 2009-09-08
Thank you for replying!  I got stuck at /boot/grub/menu.lst.  I could not find the line you said to edit.

## e.g. defoptions=vga=791 resume=/dev/hda5

That isn't it, is it?

I looked at /etc/uswsusp.conf and it was blank!  Hibernate still doesn't work.  It seems like it does but when I turn the computer back on, Ubuntu does not resume.

This is what it says when Ubuntu starts:


...Assuming drive cache...
Reading files needed to boot
...
...failed to reset NO_REBOOT flag, reboot disabled by hardware.
...

I don't know how to get a log for this so tell please tell me how if you want to see that.

Also, you said that last partition might be a recovery partition.  Does this have something to do with my computer not coming with an XP reinstallation disk?

Thanks a lot for helping!

---

### Post by CatKiller on 2009-09-08
> **cambunctious said:**
> Thank you for replying!  I got stuck at /boot/grub/menu.lst.  I could not find the line you said to edit.

## e.g. defoptions=vga=791 resume=/dev/hda5

That isn't it, is it?

Well, that's the line that provides the example options that you might use in the line below it.

As an example, mine says

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=0x31B lapic resume=UUID=5fc0504d-441e-41f0-a367-c0f9342e894e elevator=deadline
```

(You don't need all of that; those are just the options that I've got.)

That's for *new* kernels; those are the options that will be automatically added when you install a new version of the kernel.

For existing versions, you're looking for a line that says something like

```
title           Ubuntu 9.04, kernel 2.6.28-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=f0f60ece-7b14-40b8-aca3-c985d66ceac9 ro quiet splash vga=0x31B lapic resume=UUID=5fc0504d-441e-41f0-a367-c0f9342e894e elevator=deadline
initrd          /boot/initrd.img-2.6.28-15-generic
```

(Again, you don't need all of that; it's just an example. The line in the middle, that starts with *kernel*, is the one you'd want to amend)

> 
I looked at /etc/uswsusp.conf and it was blank!  


Are you sure you typed it correctly?

It's possible that I needed to install something to get software hibernate to work; it was a long time ago that I set it up, and I might have just forgotten.

> 
Hibernate still doesn't work.  It seems like it does but when I turn the computer back on, Ubuntu does not resume.


Possibly you just need to put the right resume= bit in menu.lst for the hibernate to work like it did before.

 > This is what it says when Ubuntu starts:


...Assuming drive cache...
Reading files needed to boot
...
...failed to reset NO_REBOOT flag, reboot disabled by hardware.
...

I don't know how to get a log for this so tell please tell me how if you want to see that.


I'm afraid I don't know what that means. Sorry.

I think you can view the kernel boot messages with **dmesg**. There is a tool at System &#8594; Administration &#8594; Log File Viewer that will let you see most of the system logs.

> 
Also, you said that last partition might be a recovery partition.  Does this have something to do with my computer not coming with an XP reinstallation disk?

It would be that kind of thing, yes, although I've not used an Eee - or Windows XP for that matter - so I couldn't say for sure.

> Thanks a lot for helping!

We've not cracked it yet, but I think we're getting there :)

---

### Post by cambunctious on 2009-09-11
I'm still confused about what to do with menu.lst.  I attached it so you can look at it.  The other file that i said was blank actually doesn't even exist!  Why don't spell checkers like the word doesn't?!!!

Any more great ideas?

](*,)      :)

If not, how do I reinstall Ubuntu.  Will installing it normally remove the old installation?  Otherwise, we can try to fix it.  This is very interesting for me.

---

### Post by CatKiller on 2009-09-11
> **cambunctious said:**
> I'm still confused about what to do with menu.lst. 

You change the line that says ```
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3448121b-2487-491f-879f-5f282fc3788e ro quiet splash
```

to one that says ```
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3448121b-2487-491f-879f-5f282fc3788e ro quiet splash resume=UUID=<*whatever the UUID of your swap partition is*>
```

You can also optionally change the equivalent line that boots the 2.6.28-11-generic kernel and the ```
# defoptions=quiet splash
``` line if you want this change to affect other kernels.

> 
If not, how do I reinstall Ubuntu.  Will installing it normally remove the old installation?  Otherwise, we can try to fix it.  This is very interesting for me.

The same way you installed it before. As I understand it, you've already got the partitions set up how you want them so you can select "manually partition" and tell the installer to use your existing ext partition for / and your existing swap partition. Or you can nuke them and let the installer create new ones in the unallocated space.

---

### Post by cambunctious on 2009-09-11
Bingo!  Hibernation works and I don't get that message at startup anymore!

My original intent of getting Ubuntu was to have a faster alternative to Windows just to surf the web.  Ubuntu isn't exactly faster that Grease Lightning.  Do you know of a good, small, and fast Linux?  Thanks again!

---

### Post by CatKiller on 2009-09-11
> **cambunctious said:**
>  Ubuntu isn't exactly faster that Grease Lightning.  Do you know of a good, small, and fast Linux?

There are things that you can do to make Ubuntu itself more responsive. Installing CCSM and picking more appropriate Compiz settings is probably the easiest; the default animation settings are set far too long, which makes the whole system seem slow. Turning off things that you don't use, like bluetooth, helps a bit. There are lots of threads on this already.

LXDE is pretty light. I use that when I just want to get things done. It's in the repositories. You can pick whether you want to use Gnome or LXDE for that session from the login screen.

In terms of light environments, I've only used LXDE and Xubuntu (which I didn't like that much) but there are lots of threads on that, too.

---

### Post by cambunctious on 2009-10-24
I used your instructions with the last kernel update.

Thanks again Kitty Litter Killer!

---

