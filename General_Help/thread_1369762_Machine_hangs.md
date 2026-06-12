---
title: "Machine hangs"
date: 2010-01-01
forum: General Help
---

### Post by antobobin on 2010-01-01
Dear Sir/Madam,

I have a Acer Extensa 7630EZ with Windows XP installed. I have installed Ubuntu 9.0 under windows. When I start Ubuntu, a screen appears having various options. For example:
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic recovery mode
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic recovery mode
and so on...
Earlier I used to log on to Ubuntu using the first option above (Ubuntu, Linux 2.6.31-16-generic). This is the one that is usually highlighted.
But since a few days when I choose this option, the machine hangs with the following message:
"(5,320342) Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (8.2)"
So I switched off the computer and tried other options above to log on. I finally succeeded using "Ubuntu, Linux 2.6.31-14-generic" option.
Could anyone tell me what is the problem?

Thanks,
antobobin

---

### Post by dhillonv10 on 2010-01-01
See what happens is that when your kernel updates, you don't remove the previous kernel. Here's how to do that [1]. But I suggest not doing that because you aren't able to login using the newer kernel, you should file a bug report [2]

[1] [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

[2] [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by antobobin on 2010-01-02
Dear [dhillonv10]("http://ubuntuforums.org/member.php?u=915368")
Thanks a lot for the immediate reply. I have reported the bug as per your suggestions.

---

### Post by john newbuntu on 2010-01-02
I would suggest opening synaptic (system->admin->synaptic package manager).  Search for "linux image".  Look for Linux image 2.6.31-generic.  Right click it and mark it for reinstall and then hit apply. Then after a reboot, try using that kernel.

---

### Post by antobobin on 2010-01-03
Dear john newbuntu,

I tried your suggestion. After restart the following command line appears:
sh: grub>

I can no more get into Ubuntu.

I do not know how to proceed. Help!!!!

---

### Post by john newbuntu on 2010-01-03
You are at the Grub prompt.  Open the given link and search for the string "Using CLI to Boot".  Please follow the instructions 1 through 4 to get your system ready.
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Briefly, the commands you type may be something (but not exactly) as follows:
grub>ls
    now this may show (fd0), (hd0), (hd0,1), (hd0,2)...
   
    Then do 'ls' on each of those partitions to see which one has the "boot" directory
grub>ls -l (hd0,1)/
      Note (hd0,1) is the same as sda1.  When this command is run, you
      should see the /boot directory. If not try another partition
grub>ls -l (hd0,2)/
      If you find /boot here, then:
   grub>set root=(hd0,2)
   grub>linux /vmlinuz root=/dev/sda2 ro quiet splash
   grub>initrd /initrd.img
   grub>boot

---

### Post by antobobin on 2010-01-04
Thanks for the guidance.

After several combinations (loop0 and sda2) as you will see below, I managed to boot.

I used the following CLI to boot:

sh grub>set root=(loop0)
sh grub>linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
sh grub>initrd /initrd.img
sh grub>boot

And I was successful in the boot process and accessed Ubuntu desktop.
But after I shutdown and restarted, once again only the grub CLI appears. The kernel page does not appear. So every time I have to tediously type the above commands and wait for the execution.
Could you please tell me how the kernel page can appear once again so that I may choose from it?

---

### Post by john newbuntu on 2010-01-04
The next time you login to Ubuntu type:
sudo update-grub2
and see if your problem goes away.

---

### Post by antobobin on 2010-01-05
I really appreciate the trouble you take to answer my queries.

I tried sudo update-grub2 after login.  The following is what took place.
[IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///tmp/moz-screenshot-3.png[/IMG]
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sda2
done

But when I restarted Ubuntu, the kernel page still does not appear.
What must I do further?

---

### Post by antobobin on 2010-01-05
Meanwhile...,

I read some earlier posts and tried the following:

System>Administration>Synaptic Package Manager and installed startupmanager.

That did the trick. Now I am able to get the Grub kernel page selection menu at the startup.

I hope this works with others too who have similar problems.

Thanks

---

