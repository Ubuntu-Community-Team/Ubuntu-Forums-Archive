---
title: "Karmic Grub2 Multi Boot HELP!"
date: 2009-11-01
forum: General Help
---

### Post by Pauly BC on 2009-11-01
Help! Help! A Karmic Koala has taken Windows hostage!

I had my computer dual-booting between XP and Vista, when I installed Karmic, Grub 2 was successfully implemented but I need to edit the list:

1. I know this may make you barf in your mouth just a little, but my family needs to have Vista as the default OS and Ubuntu as an option. How do you edit Grub 2 to move Vista to the top of the list?

2. Grub2 recognized the Vista bootloader with options, if you scroll down to Windows, then it offers you  a second menu with XP or Vista, how to I edit the Grub list to offer: 1. Vista; 2. Ubuntu; 3. XP.

Is there a graphical editor available for Grub2?

Thanks,
Pauly

---

### Post by Giblet5 on 2009-11-01
Edit /etc/default/grub.

Change "GRUB_DEFAULT" value from 0 to the word saved.

```
GRUB_DEFAULT=saved
```

Now run these commands *exactly*:
```
sudo grub-update
sudo install-grub `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

That will make whatever was booted last the default for subsequent boots. Or, you can change it to a hard-coded value for whatever you want to run and do the last two steps. I use saved.

---

### Post by louieb on 2009-11-01
There is some command line help in configuring grub2 including how to set the default option take a look  [IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")

The one you want is: [grub-set-default]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-set-default") - tell GRUB which OS title you want to be highlighted by default


The one thing you can't do with GRUB is offer 3 choices if 2  of them are Microsoft products. All grub can do is pass control to the Windows boot loader. Reason being is the way Microsoft  sets up multi booting at install time. 

You will have to live with Grub passing control to the Vista boot loader. 
Tech stuff: [Multibooters, Pictures here worh 1000+ words]("http://www.multibooters.co.uk/multiboot.html")

---

### Post by Pauly BC on 2009-11-02
> **Giblet5 said:**
> Edit /etc/default/grub.

Change "GRUB_DEFAULT" value from 0 to the word saved.

```
GRUB_DEFAULT=saved
```Now run these commands *exactly*:
```
sudo grub-update
sudo install-grub `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```That will make whatever was booted last the default for subsequent boots. Or, you can change it to a hard-coded value for whatever you want to run and do the last two steps. I use saved.

I ran the first command successfully, but this is not exactly what I want to achieve so I have not installed the revised grub. I want Vista to always be the default, I will have to select an alternate to load Ubuntu. I'm also concerned about the hd0 section of the code as Ubuntu is on HD0 but the fourth partition, does that matter?

Here is the boot section of grub.cfg. I know in Jaunty all I had to do was move Vista Loader above Linux and viola!:

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e151d6aa-f72d-436b-8b92-xxxxxxxx
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e151d6aa-f72d-436b-8b92-xxxxxxxx ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e151d6aa-f72d-436b-8b92-xxxxxxxx
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e151d6aa-f72d-436b-8b92-xxxxxxxx ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0078e6xxxxxxxx
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by ranch hand on 2009-11-02
Check out the link in my sig.

The first three links on that post will probably have every thing you need.

Some of us have been playing with grub2 for some time now.

---

### Post by Pauly BC on 2009-11-03
Update:

I spent about an hour working on this last night and it was simply not working for me. Every command was done using sudo, I know that much...

I edited /etc/grub.d/00_headers to change the timeout from 10 to 5 sec but when I run update-grub then reboot, it still takes 10s. I also tried grub-mkconfig and grub-mkconfig-o and update-grub but still no luck at all! I then looked at /boot/grub/menu.lst and it shows timeout of 10, not 5. Same with /etc/grub.d/grub.cfg and also in thew default folder.

So to test it out I added a comment ## This is not working for me!!! into 00_headers, 10_linux and 30_os-prober, ran update-grub, grub-mkconfig and -o, and those comments were never copied into the grub files. Every time I run those in terminal, there is lots of information scrolling by in the display and no error messages so I expect it should work, but it does not work.

AUGH! I'm ready to give up on Grub 2. Period.

Can I use the alternate install DVD to load 9.10 with the previous version of Grub so all I have to do is edit /boot/grub/menu.lst and be done with this in 1 minute?

Is grub2 supposed to be the practical joke against newbies? Here's a boot utility that works but cannot be configured even when you follow the instructions, suckers!

Thanks

---

### Post by ranch hand on 2009-11-03
Try editing your time out in /etc/default/grub.

Then run update-grub and that will reset the timeout in /etc/grub.d/00_headers to what you want.

You are lucky you caught me just now.  I am on a 10.04 testing OS and having trouble setting my menu background. Just will not go from the default.  I'll get it one of these days.  My other 10.04 does it fine.

---

### Post by wildweathel on 2009-11-03
Ignore /boot/grub/menu.lst, grub2 ignores it, too.

The "right way" to set a timeout is to change it in /etc/default/grub, and then run update-grub.  Despite the fact that they're in /etc/, it's best to leave the /etc/grub.d/ scripts alone, with the exception of 40_custom.

Does that work?  

p.s:  Comments in the /etc/grub.d scripts will not be copied to /boot/grub/grub.cfg .  That's not how it works.  Basically, those scripts are scripts that make scripts. (**!**)  So, setting a variable in a grub.d script will not necessarily set a variable at boot.  Instead, you have to output a line that sets the variable.  Try /etc/defaults/grub first.  And, yes, I agree that grub2 is overcomplicated.  Either it needs really good docs before the release of Lucid, or Lucid install notes need to tell you how to set up grub-legacy with a /boot partition.  I get the feeling there will be lots of unhappy LTS sysadmins otherwise.

---

### Post by Pauly BC on 2009-11-03
Or they could make a graphical Grub2 editing utility for setting the basics like multi-boot, timeout, background, etc. Editing these scripts is like pulling teeth.

I will try the default files tonight and report back.

---

### Post by ranch hand on 2009-11-03
The developer for Start up Manager is supposed to be working on a version that can work with grub2.

---

### Post by Pauly BC on 2009-11-03
OK

I tried again this evening and found a weird error message embedded in the heap of output from grub-mkconfig-o. Something like 'Error Grub version not compatible with scripted command' so I thought that made no sense. I went into Sinaptic and removed all of grub from the software, then reinstalled Grub-pc, let it grab the libraries it wanted, during installation it compared the default files with those on HDD and I chose to keep the HDD.

After that I rebooted and it grabbed Vista as default in 5 seconds.

So that tells us that the commands listed in ranch hand's posts are correct and my installation had become confused.

Thanks!
Pauly

PS I still think Linux is better than Vista!

---

### Post by ranch hand on 2009-11-03
This does happen, particularly on upgrades.

---

### Post by rijnsma on 2010-11-08
> **ranch hand said:**
> The developer for Start up Manager is supposed to be working on a version that can work with grub2.

That's very nice. 
Do you think it's ready by now?

After a lot of problems with a multiboot system:
I went back to PCLOS 2010, ext3 and Grub1 and I have a no worry multiboot system of 6 partitions now with an Grub-MBR from PCLOS and a fine menu.lst.
If these destroy-Linux-pleasure incompatibillity-steps keep taking place I sooner or later could install simply M$ Windows and run (when I ever might need it) some Linux from Windows as a hobby. This is no good for Linux. I'm so sorry to say.

---

