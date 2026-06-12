---
title: "Issues booting isos from flash drive with grub2"
date: 2010-05-28
forum: General Help
---

### Post by josephellengar on 2010-05-28
I'm trying to make a sort of "toolkit" flash drive using grub2 but I am running into some problems.  For some reason, every entry below gives me the error "you must load the kernel first" when I try to boot it.  I have checked in the grub command line and it appears that grub sees my flash drive as the first drive when booting.  This is what my grub.cfg looks like.

```

#Clonezilla v1.2.5-17 ====================================================================================================================

menuentry "Clonezilla 32" 
{
	set isofile="/boot/isos/clonezilla32.iso"
	loopback loop $isofile 
	linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile 
	initrd (loop)/live/initrd.img
}

menuentry "Clonezilla 64" 
{
	set isofile="/boot/isos/clonezilla64.iso"
	loopback loop $isofile 
	linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile 
	initrd (loop)/live/initrd.img
}

#gparted v0.5.2-9 ========================================================================================================================

menuentry "gparted" 
{
	set isofile="/boot/isos/gparted.iso"
	loopback loop $isofile
	linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
	initrd (loop)/live/initrd.img
}

#Ubuntu v10.04 downloaded 5/27/10 ========================================================================================================

menuentry "Ubuntu 32" 
{
    set isofile="/boot/isos/ubuntu32.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 64" 
{
    set isofile="/boot/isos/ubuntu64.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by josephellengar on 2010-05-28
Further information:  I tried adding a line that said
```

insmod iso9660

```
to each entry and that didn't help.  I also checked the filenames within the isos and those are accurate as portrayed in my grub.cfg.  Also, I coped these entries from the sites:
[http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)
[http://clonezilla.org/clonezilla-live/livehd.php](http://clonezilla.org/clonezilla-live/livehd.php)

They are copied line for line except for removing the setroot=hdx because in this case, as I am booting from a flash drive, the flash drive starts as the root, and it just doesn't work.  I am positive the flash drive is okay, as I got clonezilla to boot once, and then lost my grubcfg and had to remake it and now it's not working.  Any help would be much appreciated.

---

### Post by dino99 on 2010-05-28
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by josephellengar on 2010-05-28
> **dino99 said:**
> [http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

Thank you for the response but I have used that page for a while with the exact same results: "must load kernel first" and that was with copying their configuration file line for line.

EDIT: I just checked and the exact wording is "error: you need to load the kernel first"

---

### Post by dino99 on 2010-05-28
i've googled around but dont find clear solution:

 when you run "sudo grub-mkconfig" then "sudo update-grub"

you might watch at logs and .xsession-errors before and after each command to see whats newly logged

---

### Post by josephellengar on 2010-05-28
> **dino99 said:**
> i've googled around but dont find clear solution:

 when you run "sudo grub-mkconfig" then "sudo update-grub"

you might watch at logs and .xsession-errors before and after each command to see whats newly logged

Well, I don't use those commands because I am running this grub off of a flash drive and those commands are only relevant to the grub that is running on the computer.  But I just ran them and there were no errors.  But thank you for the help.

---

### Post by josephellengar on 2010-05-28
Just reformatted drive and reinstalled grub with the same .cfg that I posted above.  Same results.  I'm really running out of ideas.  I have looked at a ton of sample cfg files and they all look the same as mine.  Could this have something to do with my hardware or something?  It really should be working.

---

### Post by dino99 on 2010-05-28
Ranch hand have great experience with grub2, so try to pm, or look at my link below

---

### Post by josephellengar on 2010-05-28
> **dino99 said:**
> Ranch hand have great experience with grub2, so try to pm, or look at my link below

Yeah, I already have looked at that link, which was very helpful.  Thank you.  How do I pm a user?

---

### Post by dino99 on 2010-05-28
> **rossholley said:**
> Yeah, I already have looked at that link, which was very helpful.  Thank you.  How do I pm a user?

click on his avatar, then into user cp, goto send message (left column), or post a comment about one of its latest message on the forums

---

### Post by kansasnoob on 2010-05-28
I'm glad to see you're still working on this :)

I had previously suggested Portable Linux but I just tried creating a Peppermint persistent Live USB using that from Lucid and couldn't install Portable Linux:

[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

Didn't work in Karmic either, but it did work in Jaunty, but still it's just not a truly viable option anymore :(

So, I've been trying to learn some new tricks and started trying to parse through the **Booting LiveCD and Other ISOs**  section of this:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I'm far from having it anywhere nearly worked out so maybe you can actually help me. Sometimes inquisitive minds can help each other find a solution :)

BTW drs305 is usually very good about responding to questions in that thread.

---

### Post by josephellengar on 2010-05-28
Well I don't know if it's my hardware or what, but the iso toolkit drive just isn't working.  Is it possible that I could extract each iso into its own directory and then boot from there?  Does anybody know what a grub.cfg entry would look like if I were to do that?

---

### Post by josephellengar on 2010-05-28
> **kansasnoob said:**
> I'm glad to see you're still working on this :)

I had previously suggested Portable Linux but I just tried creating a Peppermint persistent Live USB using that from Lucid and couldn't install Portable Linux:

[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

Didn't work in Karmic either, but it did work in Jaunty, but still it's just not a truly viable option anymore :(

So, I've been trying to learn some new tricks and started trying to parse through the **Booting LiveCD and Other ISOs**  section of this:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I'm far from having it anywhere nearly worked out so maybe you can actually help me. Sometimes inquisitive minds can help each other find a solution :)

BTW drs305 is usually very good about responding to questions in that thread.

thanks for the suggestion.  I went ahead and posted a link here in that thread.

---

### Post by ranch hand on 2010-05-28
I am happy to see this too.  There  are a few ISOs that this works with.

I have given up and hope you figure it out.

---

### Post by kansasnoob on 2010-05-28
> **rossholley said:**
> thanks for the suggestion.  I went ahead and posted a link here in that thread.

If you find an answer it would benefit all of us :)

I've been fairly busy so my time is limited but I'd love to see a really solid solution for this.

---

### Post by ranch hand on 2010-05-28
We fooled with this back in 9.10 testing.  I saved a bunch of grub2 threads because at the time documentation was scarce on any of it.  These two dealt with that issue (loopback).

[http://ubuntuforums.org/showthread.php?t=1295506](http://ubuntuforums.org/showthread.php?t=1295506)

[http://ubuntuforums.org/showthread.php?t=1243182](http://ubuntuforums.org/showthread.php?t=1243182)

They may give you a hint or stop you from making the same mistakes.  I hope they have some value in your quest.

I really think it is just a lack of the right "hook" being in the ISO.  You may be able to edit that so that it is there.

---

### Post by josephellengar on 2010-05-28
I made some progress.  I've been working on this entry:

```

menuentry "Ubuntu 32" 
{
    loopback loop /boot/isos/ubuntu32.iso 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/isos/ubuntu32.iso noprompt
    initrd (loop)/casper/initrd.lz
}

```

Which gives the kernel error mentioned above

and I figured out that if I change it to this:

```

menuentry "Ubuntu 32" 
{
    loopback loop /boot/isos/ubuntu32.iso 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/isos/ubuntu32.iso noprompt **--**
    initrd (loop)/casper/initrd.lz
}

```

instead it gives an invalid magic number error.  Any idea what that is?

EDIT:  I got those errors backwards.

---

### Post by NUboon2Age on 2010-05-28
The tool [**MultiBoot**]("http://ubuntuforums.org/showthread.php?t=1495947") referred to in by the link in my signature below may be of interest to you for setting up a bootable flash drive with one or more .isos on it.

---

### Post by josephellengar on 2010-05-28
All right, I gave up.  I just used the solution here: [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

It has all of the utilities I could ever want or need.  But thanks everybody for all the help.  I'm marking this thread solved.

---

### Post by ranch hand on 2010-05-28
Well, can't say I blame you but I am bummed.

All  I wanted to do is boot the ISO from an exisiting Ubuntu installation and be able to try it and install from it.  This, theoretically is possible but practically it is not because the ISO needs to be built with a very slight modification.

You would think that Ubuntu, the first distro to use grub2, would be the first to offer this on their ISO but it hasn't happened yet.

Thanks for your informative thread.  I will be keeping this one too.

---

### Post by josephellengar on 2010-05-28
> **ranch hand said:**
> Well, can't say I blame you but I am bummed.

All  I wanted to do is boot the ISO from an exisiting Ubuntu installation and be able to try it and install from it.  This, theoretically is possible but practically it is not because the ISO needs to be built with a very slight modification.

You would think that Ubuntu, the first distro to use grub2, would be the first to offer this on their ISO but it hasn't happened yet.

Thanks for your informative thread.  I will be keeping this one too.

My goal as well.  Oh well, I'll probably post about it in the brainstorm or something.

---

### Post by fermulator on 2010-10-27
So there is no solution here?

I want to be able to create this "utility USB" from existing USB installation.  pendrive / multiboot solutions seem to only work from a liveCD, or Windows. ??

---

