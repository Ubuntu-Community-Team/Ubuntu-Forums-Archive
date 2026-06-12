---
title: "Undo a dual-boot?"
date: 2010-03-12
forum: General Help
---

### Post by CoolMaxUK on 2010-03-12
When I bought this computer, I decided to leave a small amount of the hard drive to Vista (which came pre-installed :@) just in case I was to ever need it.

Well, 6 months have passed and I am using Ubuntu 24/7 and have booted Vista.... Twice...

How do I revert this dual-boot leaving only Ubuntu? Ideally I would like to merge the Vista partition into the Ubuntu partition (if that's possible). And also remove the GRUB menu to save on boot time :D.

I have had a couple of bad experiences from messing around with partitions with different OSs installed and would not like to repeat those mistakes :S

Thanks!

---

### Post by 2hot6ft2 on 2010-03-12
Can you attach a screenshot of System > Administration > GParted
So we can see if there are any extended partitions and the drives layout?
Applications > Accessories > Take Screenshot
If you have that choose Grab Current Window

As far as Grub goes it should still be there but it will usually just count down like 3 seconds giving you a chance to access it if something were to get messed up that way you could still get into recovery mode or boot with another kernel.

---

### Post by CoolMaxUK on 2010-03-12
There you go! :D

EDIT: I might also want to delete the recovery section, is that ok?

---

### Post by 2hot6ft2 on 2010-03-12
Just to be clear. Are you wanting to get rid of sda2 and sda3 and expand sda5 to take up the space where sda2 and sda3 were?

What about the sda1? Personally I wouldn't even bother messing with it considering its size of 39.19MB

The screenshot helps because you have sda5 and your swap inside an extended partition. So it will affect the instructions on how to do it.

---

### Post by CoolMaxUK on 2010-03-12
Exactly right! I agree with you there, sda1 isn't worth it and I believe it might have some important start-up stuff there, so best leave it alone.

You say the GRUB won't be affected?

---

### Post by 2hot6ft2 on 2010-03-12
> **CoolMaxUK said:**
> Exactly right! I agree with you there, sda1 isn't worth it and I believe it might have some important start-up stuff there, so best leave it alone.

You say the GRUB won't be affected?
Well with just 1 operating system it should just countdown like
Grub Loading 3..2..1 then right into the OS
That gives you a chance to get into it if needed but you wont normally see the grub screen like you do now.

You'll be reinstalliing grub in case the UUID or sda# of linux changes.

---

### Post by 2hot6ft2 on 2010-03-12
Boot from the livecd.
Go to System > Administration > GParted
select sda2 and click on Delete
select sda3 and click on Delete

Click on Apply

When that finishes

Right click on linux swap and select swapoff.
Right click on sda4 and select unmount

Select sda4 and click on resize. (The extended partition)
Move the left side of the slider all the way to the left

Select sda5 and click on resize. (The Linux partition)
Move the left side of the slider all the way to the left

Click on Apply and have it make all changes. It will take a while to resize the partitions.

Look at what the linux partition is now sda number what?
Did it change?
If it did remember the number and use it in the next part. 

Once it's all done close GParted
Now to reinstall Grub for the new layout

Here assuming the Ubuntu partition is still sda5
Open terminal and run:
```
sudo -i

```
```
mount /dev/sda5 /mnt
```
```
grub-install --root-directory=/mnt/ /dev/sda
```
Close the terminal
Reboot removing the livecd in the process and you should be all set.

---

### Post by CoolMaxUK on 2010-03-12
Great! Thanks! Its 1am here, so I'll probably get back to you on how it goes tomorrow :).

What is the reason for doing this from the livecd? I'm not questioning your logic, its just that I'm fairly new to Linux and I want to learn this kind of stuff.

Thanks again :)

---

### Post by 2hot6ft2 on 2010-03-12
> **CoolMaxUK said:**
> Great! Thanks! Its 1am here, so I'll probably get back to you on how it goes tomorrow :).

What is the reason for doing this from the livecd? I'm not questioning your logic, its just that I'm fairly new to Linux and I want to learn this kind of stuff.

Thanks again :)
You can't resize or move a partition that is mounted which it would be if you were running the installed system. Plus you can't resize something that you're running (in use at the same time).

They are inside an extended partition and you can't do anything to it while it's locked. See the locks on the pic you took of GParted. sda4, 5 and 6 are locked.

G'night and welcome.

---

### Post by 2hot6ft2 on 2010-03-13
By the way once you boot into ubuntu after making the changes you should run
```
sudo update-grub
```

---

### Post by CoolMaxUK on 2010-03-13
Hi, I did as you said and successfully deleted and resized the partitions.

However, I rebooted and the grub screen shows no boot options. It says that if I press tab, a list of bash-like commands appear. I did that, but I don't know which command to use.

I tried boot, but it asks to specify the kernel. How do I do that?

I was using the latest kernel supported by ubuntu xx.xx.20.

---

### Post by 2hot6ft2 on 2010-03-13
The kernel is
linux-image-2.6.31-20-generic
But I'm sure there would be more to it than that. I don't know why it would give that message.

When it says Grub Loading... click on "e" on the keyboard to get to the grub screen and choose a kernel.

If that doesn't work boot the livecd and reinstall grub again
Using Ubuntu 9.10 livecd

Boot up ubuntu from the livecd,open terminal.:

First list your partitions so you have the info for the rest using
```
fdisk -l
```
Here assuming the Ubuntu partition is sda5
```
sudo -i
```
```
mount /dev/sda5 /mnt
```
```
grub-install --root-directory=/mnt/ /dev/sda
```
That should be it. Reboot removing the livecd in the process.

---

### Post by CoolMaxUK on 2010-03-13
I have done as you said from the terminal on the live-cd boot, rebooted and the boot option still doesn't appear on the grub screen.

I tried typing "e" but it says that is an invalid command. This is what I get on the grub menu:

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.

sh:grub>

If i run "sudo update-grub" from the livecd, will that work?

---

### Post by 2hot6ft2 on 2010-03-13
It's worth a shot. I'm looking to try and find the answer.
```
Reinstalling GRUB 2 from LiveCD
If you cannot boot from GRUB 2 and need to reinstall it, here is the simple method. For more details or for advanced options, refer to the Ubuntu community documentation here: Grub2 - Reinstalling GRUB 2:

    * Boot the 9.10 Karmic LiveCD to the Desktop.
    * Open a terminal - Applications, Accessories, Terminal.
    * Determine your normal system partition - `sudo fdisk -l` (That is a lowercase L)
    * If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
    * Mount your normal system partition:
      Code:

      sudo mount /dev/sdXY /mnt

          o Example: sudo mount /dev/sda1 /mnt
          o Note: The partition to mount is normally the partition on which Ubuntu was installed: sda1, sdb5, etc. If you have a separate /boot partition, use the device on which the /boot partition is located. Grub 2 works best when installed in the MBR of the drive to which BIOS boots. Also remember that you mount the partition (including the number) in this step, but you do not include the partition number when you run the "sudo grub-install" command later.
          o Note: GRUB 2 counts the first drive (X) as "0", but the first partition (Y) as "1"
    * Only if you have a separate boot partition:
          o
            Code:

            sudo mount /dev/sdXY /mnt/boot

            with sdXY being your /boot partition designation.
    * Reinstall GRUB 2:
      Code:

      sudo grub-install --root-directory=/mnt /dev/sdX

    *
          o Example: sudo grub-install --root-directory=/mnt /dev/sda
          o Note: Substitute the device on which Ubuntu was installed - sda, sdb, etc. Do not specify a partition number.
    * Unmount the partition:
      Code:

      sudo umount /mnt

    * Reboot.


``````
Booting from the Rescue Mode
At the grub rescue> prompt, accomplish the following actions to attempt to boot to the latest kernel:

    * ls This will display the known devices and partitions. From this information, the user must determine the device and partition on which the system is installed.
    * set Check the current settings. Note the prefix listing. If it is not pointing to the correct location:
          o set prefix=(hdX,Y)/boot/grub Examples: sda1 is (hd0,1), sdb5 is (hd1,5)
    * set root=(hdX,Y) X is the device/drive, starting with 0. Y is the partition, starting with 1. (Example: (hd0,1) is sda1. (hd3,5) is sdc5.
          o For Wubi installs, use: set root=(loop0)
    * ls /boot Inspect the contents. The user should see varioius kernels, initrd images and the grub folder. If not, use the ls command to inspect the device and attempt to find these files and folders. If necessary, set another device as root.
    * insmod /boot/grub/linux.mod Load the linux module. Without this module loaded, the user will receive an "Unknown command linux" message when trying to load the kernel.
    * linux /vmlinuz root=/dev/sdXY ro Load the linux kernel, substituting the correct designations for "X" and "Y" (example: sda1). The user will see a message showing the kernel has been loaded. (See graphic above)
          o Note: For Wubi installs within Windows, use this code: linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
    * initrd /initrd.img Load the initrd image. When pressing enter, the user may or may not see a message in the terminal. (See highlighted graphic above)
    * boot
More command line recovery options are available in the "Command Line & Rescue Mode" section of the Ubuntu Grub 2 community doc.

```
From the Grub 2 Guide in my sig. below.

---

### Post by CoolMaxUK on 2010-03-13
I followed that step by step and managed to boot! :D

I'm going to update the grub now and reboot to see if its back to normal.

EDIT: I rebooted and I get the same message. I'll try doing what you said from the livecd.

---

### Post by 2hot6ft2 on 2010-03-13
Oops, didn't read your post clearly enough. Keeping my fingers crossed. I don't understand why you're having problems it should be just that simple.

---

### Post by CoolMaxUK on 2010-03-13
I don't understand either. I can get it to boot from the grub recovery but can't seem to get it to boot that kernel by default.

I tried installing grub from my distro (not from the livecd) and it said it could not find a directory. I can't recall its name, but if installing again from the livecd fails, then I will specify its name.

Keeping my fingers crossed too...

---

### Post by 2hot6ft2 on 2010-03-13
> **CoolMaxUK said:**
> I don't understand either. I can get it to boot from the grub recovery but can't seem to get it to boot that kernel by default.

I tried installing grub from my distro (not from the livecd) and it said it could not find a directory. I can't recall its name, but if installing again from the livecd fails, then I will specify its name.

Keeping my fingers crossed too...
I'm not seeing anything that would be of any help in the grub 2 guide other than what I've already posted. You might want to take a look at it too. I'll start going thru the thread.:confused:

Might try booting to the 2.6.31-19 kernel and see if that will work.
If it does reinstalling the 2.6.31-20 kernel may solve it.

---

### Post by CoolMaxUK on 2010-03-13
That didn't work... I have just noticed that this isn't grub 2, its grub 1.97 beta4...

I'm going to try re-installing the kernel and doing a system update to see if that helps.

---

### Post by 2hot6ft2 on 2010-03-13
> **CoolMaxUK said:**
> That didn't work... I have just noticed that this isn't grub 2, its grub 1.97 beta4...

I'm going to try re-installing the kernel and doing a system update to see if that helps.
1.97 beta 4 is grub 2

---

### Post by CoolMaxUK on 2010-03-13
SUCCESS!! I changed the default kernel from star-up manager, reinstalled grub and updated it.

Thank you! :D

I think next time I install ubuntu, I will completely remove windows and keep a single boot install :P

---

### Post by 2hot6ft2 on 2010-03-13
> **CoolMaxUK said:**
> SUCCESS!! I changed the default kernel from star-up manager, reinstalled grub and updated it.

Thank you! :D

I think next time I install ubuntu, I will completely remove windows and keep a single boot install :P
Good job! I was about to throw some more options your way from page 12 of the thread Grub 2 Guide... That's a long thread and it started to look like a few options were starting to show up.

Congratulations
:guitar:
I don't know why you hit a snag it's usually pretty simple to do what you were wanting to do.

P.S. Mark this thread as solved, please... Using Thread Tools at the top of the thread.

---

