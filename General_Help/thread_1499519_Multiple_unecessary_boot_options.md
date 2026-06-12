---
title: "Multiple unecessary boot options"
date: 2010-06-02
forum: General Help
---

### Post by Komputor on 2010-06-02
After installing Ubuntu 10.4 to my laptop, keeping my Windows Vista partition, Grub boot menu options read as follows:

GNU GRUB version 1.98-1ubuntu6
Ubuntu, with Linux 2.6.32-22 generic
Ubuntu, with Linux 2.6.32-22 generic(recovery mode)
Ubuntu, with Linux 2.6.32-21 generic
Ubuntu, with Linux 2.6.32-21 generic(recovery mode)
Memory test (memtest86+)
Memory test (memtest86+,serial console 115200)
Windows Vista (loader)(on /dev/sda2)

After installing Ubuntu Studio, I now have all of these crazy options:

GNU GRUB version 1.98-1ubuntu6
Ubuntu, with Linux 2.6.32-22 generic
Ubuntu, with Linux 2.6.32-22 generic (recovery mode)
Ubuntu, with Linux 2.6.32-21 generic
Ubuntu, with Linux 2.6.32-21 generic (recovery mode)
Ubuntu, with Linux 2.6.31-10-rt
Ubuntu, with Linux 2.6.31-10-rt (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+,serial console 115200)
Windows Vista (loader)(on /dev/sda2)

All of the Ubuntu options open Ubuntu Studio with all of my settings, no matter what.  Which is not a problem, just wondering if there is any way of having Grub recognize only one option for Ubuntu by doing some editing??  What's going on?

I notice that there is a different Linux kernel for each version of Ubuntu.  Studio does use a real time kernel, but as for the first two that appeared after initial installation?

Not sure what's going on.  If I installed Ubuntu, wouldn't it just use a single kernel?  If I installed Studio after UbuDesktop, wouldn't the kernel be overwritten?

It's a lot of questions, but I am VERY curious about this.  Thanks ahead!

---

### Post by kevin.krenz on 2010-06-02
There are multiple threads on similar topics right now about this, such as:

[http://ubuntuforums.org/showthread.php?t=1486692](http://ubuntuforums.org/showthread.php?t=1486692)

For general information about grub2, see:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Komputor on 2010-06-02
> **kevin.krenz said:**
> There are multiple threads on similar topics right now about this, such as:

[http://ubuntuforums.org/showthread.php?t=1486692](http://ubuntuforums.org/showthread.php?t=1486692)

For general information about grub2, see:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


Sorry Kevin, the first link does not answer my questions.  However the second link is a huge help.  But my question now is if I follow the guide in the second link, read #7 "Removing Entries from Grub2," will that harm my Ubuntu OS?  I know to backup all data before making any serious changes, but will removing one Linux kernel affect the others?  Or, do they all operate independently?  It seems the UbuStudio install either copied, or migrated my user name and passwords, and my whole file system structure.  Thanks for the help!

---

### Post by clhsharky on 2010-06-02
Komputor

The safest way I know to remove unwanted kernels is to use your default Package Manager.

Sharky

---

### Post by warri0r on 2010-06-02
Removing linux kernel wont affect anything unless u are left with no kernel to boot up :P they are simply modular, kernels wont migrate or copy anything, but just use the common settings tat is stored anyways check this,

[http://ubuntuforums.org/showthread.php?t=1498127](http://ubuntuforums.org/showthread.php?t=1498127)

---

### Post by James78 on 2010-06-02
Open Synaptic, and do a search for 2.6.32-21 and 2.6.31-10-rt, then do a purge, or complete removal of them, you can also do an advanced search for version 2.6.32-21 and 2.6.31 if that didn't find them all. When you completely remove them, old kernel links will be removed, update-grub will be invoked, and the unneeded kernel entries will be removed automatically.

---

### Post by Komputor on 2010-06-02
Thanks everyone!  I'll report back if there are any more issues :D

---

### Post by dino99 on 2010-06-02
more info looking the link below

---

### Post by Komputor on 2010-06-02
Ok, now when I search for 2.6.32-22, Synaptic shows I have "linux-headers-2.6.32-22;linux-headers-2.6.32-22-generic" with installed version of "2.6.32-22.33" for both.

Should I remove *both *or *one*?

---

### Post by jawilljr on 2010-06-02
The command below will remove all but the latest kernel:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs -p sudo apt-get -y purge
```

I got the above one liner from [here.](http://www.commandlinefu.com/commands/view/2456/purge-installed-but-unused-linux-headers-image-or-modules)

I added the -p option to verify the command.  It works in Karmic

When it is done do a "sudo update-grub" to remove the previous kernels from the boot menu.

Jerry

---

### Post by Komputor on 2010-06-02
> **jawilljr said:**
> The command below will remove all but the latest kernel:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs -p sudo apt-get -y purge
```I got the above one liner from [here.]("http://www.commandlinefu.com/commands/view/2456/purge-installed-but-unused-linux-headers-image-or-modules")

I added the -p option to verify the command.  It works in Karmic

When it is done do a "sudo update-grub" to remove the previous kernels from the boot menu.

Jerry

As I am not trying to remove all but the *latest* kernel, only all others than the real time one, I have used the Synaptic pkg mgr and Success!  Well, at least for 2.6.32-21.  When I rebooted, 2.6.32-22 was still there as an option, so I just ran Synaptic again, searched for -21, and ran the removal.  I got this from viewing the details afterwards to verify removal:
Code:
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinu.old
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
 you may need to re-run your boot loader[grub]

Any thoughts?  I don't want to reboot to a machine that can no longer boot, thanks!

---

### Post by Komputor on 2010-06-02
By the way, just did an update-grub and:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-10-rt
Found initrd image: /boot/initrd.img-2.6.31-10-rt
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda2
done

I should be fine right?
Thanks again!

---

### Post by James78 on 2010-06-02
No no no!! You removed the wrong kernel! I said do a search for 2.6.32**-21** AND 2.6.31-10-rt!! You should add the version of 2.6.32-22 that you removed back, and remove 2.6.31-10-rt completely, and if 2.6.32-21 is already gone, then you can skip that one (or if not, completely remove that too).

---

### Post by robert shearer on 2010-06-02
> **James78 said:**
> No no no!! You removed the wrong kernel! I said do a search for 2.6.32**-21** AND 2.6.31-10-rt!! You should add the version of 2.6.32-22 that you removed back, and remove 2.6.31-10-rt completely, and if 2.6.32-21 is already gone, then you can skip that one (or if not, completely remove that too).

Hey man, the op needs the rt kernel as he is using Ubuntu **Studio**.

To the op, it generally pays to have two kernels installed , the one you are using and an older one.(or in your case the 2.6.32-22 one as it is more current than the rt kernel which is not updated as often)

That way if you do something that makes your box un-bootable with the current kernel you can select to boot with the older kernel and fix things.

---

### Post by James78 on 2010-06-02
True. I usually just boot up a livecd though, but that way is faster/more efficient.

Either way, 2.6.32-22 should still be installed, and you can leave the rt kernel.

---

### Post by Komputor on 2010-06-02
James, Thanks for the concern, but Robert is right.  I just rebooted without the rt kernel and everything is running fine.  I will follow Robert's advice and install the other kernel.  Thanks all!

---

### Post by James78 on 2010-06-02
> **James78 said:**
> True. I usually just boot up a livecd though, but that way is faster/more efficient.

**Either way, 2.6.32-22 should still be installed,** and you can leave the rt kernel.Maybe you didn't see that, I added it later. :) That is the latest kernel for regular Ubuntu, so it would be a great candidate.

---

### Post by Komputor on 2010-06-02
> **James78 said:**
> Maybe you didn't see that, I added it later. :) That is the latest kernel for regular Ubuntu, so it would be a great candidate.

Thanks :D  :guitar:

---

### Post by sunewbie on 2010-10-09
You can either remove the old grub entries via Synaptic Package Manager, or a much easier way is to do it via [Ubuntu Tweak]("http://ubuntu-tweak.com/"). (I tried version 0.5.6)

Firstly, go to Ubuntu Tweak, download and install the software.

Once you have Ubuntu Tweak installed, you will find it under the System Tools menu.

Click on it, and once it's loaded select Package Cleaner, click on Unlock in the bottom right-hand corner & enter your password when prompted.

Then click on Clean Kernels, now you will see a list of old kernels that you no longer need. Click Cleanup and the old grub entries will be removed and it will keep only the newest version installed.

Source: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9421333](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9421333)

I tried it and it works. Ubuntu tweek is a good software with gui interface.

---

