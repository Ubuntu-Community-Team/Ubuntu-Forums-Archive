---
title: "fsck from util-linux-ng 2.16"
date: 2010-02-03
forum: General Help
---

### Post by helianthus on 2010-02-03
When I boot into recovery mode I get

fsck from util-linux-ng 2.16
/dev/sda1: clean, 148044/217728 files, 630631/869510 blocks

And then it stops. Booting into normal mode results in an endless hang. I'm not sure what the error means, or how to fix it.

I'm running Ubuntu Netbook Remix on a Dell Mini 9.

---

### Post by hatapota on 2010-02-18
I am having exactly the same problem. Yesterday (the 2nd time I've ever used this computer!) synaptic package manager wanted to upgrade some things (I don't remember what), then asked to reboot the computer, and it's not switched back on since then.

Has anyone else come across this? I really don't know what to do. Any help would be very much appreciated!

---

### Post by ZarlacMing on 2010-02-24
I'm having the same problem when booting my freashly installed Ubuntu 9.10.
While booting in normal mode the system hangs when showing the Ubuntu logo and when booting in recovery mode if hangs after showing "fsck from util-linux-ng 2.16".

---

### Post by Vevmesteren on 2010-03-01
This is absolutely terrible, same thing happened to me this last night. Help? Can't boot in recovery or full mode. 

Where did Ubuntu go?

---

### Post by High_Noonan on 2010-03-03
Same here from a Lenovo X61 tablet.

Are we any closer to a solution?
I am seeing older reports of this issue, but they are on netbooks and such.

Kind of hard to convince the girlfriend to go "Linux" (read: "Ubuntu Linux") with a show stopper like this occurs during the conversation! BWAHAHAHAHAHAHAHAHHAHAA

---

### Post by da1337ninja on 2010-03-24
I'm having the same problem. At first I thought it was my SSD drive but no I think it's a firmware/software thing... I post an update if I get it to work.

---

### Post by dcstar on 2010-03-24
> **helianthus said:**
> When I boot into recovery mode I get

fsck from util-linux-ng 2.16
/dev/sda1: clean, 148044/217728 files, 630631/869510 blocks

And then it stops. Booting into normal mode results in an endless hang. I'm not sure what the error means, or how to fix it.


It is not any sort of "error", it is simply a message from something that ran correctly.

The problem is that whatever is **supposed to follow it** is not running or starting.

---

### Post by dert on 2010-03-26
> **dcstar said:**
> It is not any sort of "error", it is simply a message from something that ran correctly.

The problem is that whatever is **supposed to follow it** is not running or starting.

That's encouraging!  The next logical question is, **_how do we fix it_**?  I'm another in the long line of people suffering from this.  As I'm very new to linux, I have nothing in my "toolbox" to help make the boot go.  Help me make it go please!

Oh, I filed a bug report on this too because this behavior is unacceptable.  I googled the issue all night and tried no less than a dozen suggestions but nothing worked.  As we speak I'm reinstalling everything from scratch...I had a dual boot drive too which just makes this a crying shame.  If I get the same behavior, I have no choice but to eliminate Ubuntu from my list of Linux distros with which to create my new drive.  That would be a Greek tragedy.

---

### Post by hatapota on 2010-03-26
Sorry to hear you're having this problem too. It happens because the computer reboots before the updated packages have all installed - seems like a trigger asking to reboot comes too early in the process.
 
It is possible to fix this problem but it's really complicated and involves knowing a lot more about linux/ubuntu than I do - my brother fixed it for me but I wouldn't be able to tell you exactly what he did. I know that he got the update to finish and then it worked perfectly, but to do that he had to a lot in the command line in order to a) figure out what had happened, then b) try to connect to the internet to be able to finish the update.
 
Sorry not to be more help - hopefully something will come of the bug report as it's a really nasty problem.

---

### Post by ckeilloh on 2010-04-18
I am using Karmic Koala on a HP compaq nc8430 This has happened to me too and is incredibly annoying. If my laptop decides to finish booting (i.e. getting past the fsck from util-linux-ng 2.16 etc. screen), I can log on but both my processors operate constantly at around 90% load for no apparent reason making anything else run slowly or crash altogether.

This came after an update this morning that seemed to hang for a long time during this process. Is there any way to rollback an update?

Edit: Opening update manager and pressing check I am asked for my super user password before it shows me any available updates. After entering my password it gets stuck downloading the last file in "Downloading Package Information" for a long time. This update does not take effect as every time I check for updates this update is downloaded for me repeatedly.

---

### Post by rogerlburns on 2010-04-19
FSCK hangs at 90% on my PC running Ubuntu 9.10. esc works before it reaches 90%, but if I reboot FSCK starts all over again. It always hangs at 90%. 
What can be done to fix this.

---

### Post by Pabbajati on 2010-04-23
I've just had the same problem on my Dell Inspiron 6000 laptop with Ubuntu 9.10. I'm a 3 month newby to Linux and had a similar start up   problem a few months ago ending up with re-installing from scratch which was rather frustrating.  Has been working fine since then (about a month).

In addition I got:

"/ dev/sda1 : clean," and then the  number of 'files' and 'blocks' followed by:

"(check in 3 mounts"

I got out of it with CTRL ALT DELETE which took me to the boot screen where I selected the first option and Ubuntu started up ok.  

Would be good to know what the message means so if anything needs to be done I can do it again.  I installed the firewall last night, but it booted up ok this morning.

---

### Post by ZarlacMing on 2010-05-22
I'm not compleatly sure but I think I resolved this problem by editing the /boot/grub/grub.cfg file. Just add noapic at the two lines like below, the word is marked with red color inside the code block. You could try it:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, med Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set 3e108b82-c4fb-4ae5-9840-9fe041901c19
        linux   /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=3e108b82-c4fb-4ae5-9840-9fe041901c19 ro   quiet splash [COLOR="red"]**noapic**[/COLOR]
        initrd  /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.32-22-generic-pae (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set 3e108b82-c4fb-4ae5-9840-9fe041901c19
        echo    'Läser in Linux 2.6.32-22-generic-pae ...'
        linux   /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=3e108b82-c4fb-4ae5-9840-9fe041901c19 ro single [COLOR="Red"]**noapic**[/COLOR]
        echo    'Läser in initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###
```

In order to boot so you can edit the file you have to press the 'e' key while the grub menu is showing and add **noapic** to the /boot/vmlinuz... line and then press the 'x' key to boot.

---

### Post by yiun on 2010-10-08
I had the same problem, and solved it by updating (sudo apt-get upgrade) via SSH. This required of course a configuration of SSH before the error occur.

Maybe its also possible to run an update via Rescue-Mode or LiveCD with 'chroot'

Hope it helped :)

---

### Post by w9caf on 2011-01-18
It seems there are many causes of this problem. In my case, I added a new disk, edited /etc/fstab but forgot to run mkfs. When I rebooted I got the "fsck from util-linux-ng" and a partially hung system. I tried the other solutions mentioned here and in other forums. None of them worked. I later found a bug report that asked the poster to hit "s" to skip any devices in fstab that failed to mount. That did it for me. The system finished booting.

Hope this helps.

---

