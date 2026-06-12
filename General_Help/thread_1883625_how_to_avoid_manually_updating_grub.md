---
title: "how to avoid manually updating grub"
date: 2011-11-19
forum: General Help
---

### Post by nariknahom on 2011-11-19
Hi,

I have dual boot system with Ubuntu 11.10 (installed first) and Fedora 16. I have actually two problems.

[LIST=1]
[*]how to avoid manually running update-grub after a Fedora kernel update?
[*]after running update-grub, the kernel parameters passed by fedora are missing the grub conf file in ubuntu.

[UPDATED for clarity]
   For example: the grub on Fedora's boot/grub2/grub.conf contains
```
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.x86_64' --class fedora --class gnu-linux --class gnu --class os {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 65196b61-c48c-4bb8-b109-81fccceae1e6
    echo    'Loading Linux 3.1.0-7.fc16.x86_64 ...'
    linux   /boot/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=65196b61-c48c-4bb8-b109-81fccceae1e6 ro rd.md=0 rd.lvm=0 rd.dm=0  KEYTABLE=us quiet SYSFONT=latarcyrheb-sun16 rhgb rd.luks=0 LANG=en_US.UTF-8 
    echo    'Loading initial ramdisk ...'
    initrd  /boot/initramfs-3.1.0-7.fc16.x86_64.img
}
```

The same entry in Ubuntu's boot/grub/grub.conf shows as below
```
menuentry "Fedora release 16 (Verne) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 65196b61-c48c-4bb8-b109-81fccceae1e6
    linux /boot/vmlinuz-3.1.0-7.fc16.x86_64 root=/dev/sda2
    initrd /boot/initramfs-3.1.0-7.fc16.x86_64.img
}

```


[/LIST]

Please let me know if there is a solution.

Thanks.

---

### Post by ajgreeny on 2011-11-19
You maybe able to use the ubuntu grub instead of fedora's by first putting ubuntu grub onto the MBR with ```
sudo grub-install /dev/sda
``` from your ubuntu OS, then doing a similar action from fedora, but putting grub onto /dev/sda#, where sda# is your fedora OS partition, not the MBR.  If you do that, running update-grub in fedora will not change the grub configuration that is actually being used by the system

I have no idea how to do that from fedora, but presumably it will be a similar command, though fedora uses LVM partitioning by default, and that could possibly mean that fedora's grub is broken.   However, as long as ubuntu's grub works as it should, you will still be able to boot both OSs.

---

### Post by nariknahom on 2011-11-19
My current configurations is already as you suggested.

---

### Post by ajgreeny on 2011-11-19
So if your fedora grub is not on the MBR, but in a partition, and not therefore used at boot time, why does that cause you a problem;  the machine will be booting from the ubuntu grub.

Perhaps I am missing something important here, though if so, I don't quite see what at the moment?

---

### Post by Bobhuber on 2011-11-19
> **nariknahom said:**
> Hi,

I have dual boot system with Ubuntu 11.10 (installed first) and Fedora 16. I have actually two problems.

[LIST=1]
[*]how to avoid manually running update-grub after a Fedora kernel update?
[*]after running update-grub, the kernel parameters passed by fedora are missing the grub conf file in ubuntu.
[/LIST]

Please let me know if there is a solution.

Thanks.

If you change the Fedora Kernel and you are using Ubuntu's grub (which is what you  are saying) in the MBR to boot the system then you will have to manually update grub from the Ubuntu system in order to boot into Fedora after a Kernel update. I'm not following the second question at all.The two systems are separate. The grub config file if you are using Ubuntu's grub is located in Ubuntu and has nothing to do with Fedora other than giving you access to the other system.

---

### Post by oldfred on 2011-11-19
See this thread with the same issue on Fedora.

 [SOLVED] grub2 dual boot problem
[http://ubuntuforums.org/showthread.php?t=1883585](http://ubuntuforums.org/showthread.php?t=1883585)

---

### Post by beew on 2011-11-19
I may be missing something, but in Fedora you can choose not to install grub at all, that way there will be no chance of mixing up. This is what I do in my Ubuntu-Fedora dual boot system. Yes, you do have to update grub manually in Ubuntu after you have a Fedora kernel upgrade.

---

### Post by drs305 on 2011-11-19
I'm not sure this is the best solution, but if you want to keep Grub 2 installed but 'turn off' Grub 2 to prevent it from updating:

You can either make one or more of the scripts in /etc/grub.d unexecutable so it runs but doesn't activate the scripts, or 
You can run the following commands to disable update-grub. Note: I don't use Fedora.

To disable 'update-grub' :
```
sudo dpkg-divert --rename --add /usr/sbin/update-grub  # changes name to update-grub.distrib
sudo ln -s /bin/true /usr/sbin/update-grub # runs /bin/true as update-grub so no errors generated

```

To re-enable 'update-grub' :
```
sudo rm /usr/sbin/update-grub  # Remove link if you created one.
sudo dpkg-divert --rename --remove /usr/sbin/update-grub # Re-enable 'update-grub' 

```

---

### Post by nariknahom on 2011-11-20
> **beew said:**
> I may be missing something, but in Fedora you can choose not to install grub at all, that way there will be no chance of mixing up. This is what I do in my Ubuntu-Fedora dual boot system. Yes, you do have to update grub manually in Ubuntu after you have a Fedora kernel upgrade.

Do you mean I need not have selected 'install boot loader' while installing Fedora?

---

### Post by nariknahom on 2011-11-20
I have updated my original query to make the second part more clear. 
This second part is a more annoying issue than running update-grub manually.

---

### Post by drs305 on 2011-11-20
> **nariknahom said:**
> I have updated my original query to make the second part more clear. 
This second part is a more annoying issue than running update-grub manually.

This is the same issue presented in another thread. I provided a method of altering one of the Ubuntu Grub scripts to add "apci=off" to any kernel starting with "Fedora". 

You could do the same thing with an even longer string of kernel options.

Here is the thread. See Post #6:
[http://ubuntuforums.org/showthread.php?t=1883585]("http://ubuntuforums.org/showthread.php?t=1883585")

---

### Post by beew on 2011-11-23
> **nariknahom said:**
> Do you mean I need not have selected 'install boot loader' while installing Fedora?

Exactly. If you want Ubuntu to control boot just uncheck the box "install boot loader to" when installing  Fedora.  But after you install Fedora you have to boot into Ubuntu to run sudo update-grub, and same everytime you have a kernel update in Fedora. I have been dual booting Ubuntu with Fedora since Fedora 14, never install a boot loader for Fedora.

---

