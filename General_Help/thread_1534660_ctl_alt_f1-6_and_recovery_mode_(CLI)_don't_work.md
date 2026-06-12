---
title: "ctl alt f1-6 and recovery mode (CLI) don't work"
date: 2010-07-19
forum: General Help
---

### Post by lalop on 2010-07-19
Afraid I'm an utter newbie.  I'm using 10.04 64 bit.

I only noticed this after I tried to install the NVIDIA driver and all my ubuntu os'es blackscreened after restart.  Because I couldn't even access recovery mode, I ended up reinstalling ubuntu, overwriting the old root.

I thought the problem was due to the driver, but it's even now persisting.  I can run the terminal (within X?) but if I try ctl alt <F1-6>, the screen just freezes until I do ctl alt F7.  Furthermore, recovery mode still leaves a black screen after the initial loading text.  I need it to work before I attempt reinstalling the NVIDIA drivers again, as I don't want to reinstall the OS and all the programs.

Sometimes it feels like I can do stuff in recovery mode, like Ctl Alt Delete or sudo shutdown, but sometimes not.

Anyway to debug this?

Not sure if this is related, but grub also lists windows vista and windows recovery as the opposite  they should be (I thought my windows was completely screwed until I tried windows recovery).

Thanks.

---

### Post by towheedm on 2010-07-19
Well I'm using Karmic and a while back I had a similar problem where I could not access any of my VTE's.  Anytime I pressed Ctrl-Alt-F1-6 all I got was a black screen with a flashing underscore in the upper left corner of the screen.  Similarly, if I selected the recovery mode from the boot menu, I got the same thing.  I don't know if this is what you are describing.

In my case, after months of trying to figure it out, it turned out that I added the set gfxpayload=keep to my /etc/grub.d/00_header file.  It appears that the VTE's did not like this.  After removing it and updating grub.cfg, my VTE's were back with Ctrl-Alt-F1-6.  Recovery mode also worked after this.

Hope this helps you.

---

### Post by lalop on 2010-07-19
Fraid I don't have any  gfxpayload in my header.  (There's no flashing underscore for me either, just nothing =/).  My grub just got autoinstalled from Unetbootin's live usb.

---

### Post by towheedm on 2010-07-19
> **lalop said:**
> Fraid I don't have any  gfxpayload in my header.  (There's no flashing underscore for me either, just nothing =/).  My grub just got autoinstalled from Unetbootin's live usb.

The only thing I can think about right now is to check whether gfxpayload is included in the command list for the boot entries.  This happened to me after trying to compile grub from the experimental branch.  Probably I compiled it wrong, but it was installing the EFI modules for my nvidia card.  In this case, the gfxpayload was in the command list for all boot entries.  This caused me to boot to a completely black screen for any entry in the menu.  Don't know which nvidia card you have but I have an FX5200 Dell.

Removing the gfxpayload command allowed me to boot into recovery mode and reinstall grub from the repos.

---

### Post by lordskid on 2010-07-19
I had the same problem with karmic a few months back what I did was rather drastic...
reinstall

---

### Post by lalop on 2010-07-20
> **towheedm said:**
> The only thing I can think about right now is to check whether gfxpayload is included in the command list for the boot entries.  This happened to me after trying to compile grub from the experimental branch.  Probably I compiled it wrong, but it was installing the EFI modules for my nvidia card.  In this case, the gfxpayload was in the command list for all boot entries.  This caused me to boot to a completely black screen for any entry in the menu.  Don't know which nvidia card you have but I have an FX5200 Dell.

Removing the gfxpayload command allowed me to boot into recovery mode and reinstall grub from the repos.

Believe my NVIDA is [COLOR=#000000][FONT=Times New Roman][LEFT][FONT=arial]**NVIDIA® GeForce® 9300M**[/FONT][/LEFT][/FONT][/COLOR].

In /etc/grub.d/10_linux:

```
 if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
      cat << EOF
    set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi
```That's all I could find.  Should I remove the whole thing?

---

### Post by towheedm on 2010-07-20
> **lalop said:**
> Believe my NVIDA is [COLOR=#000000][FONT=Times New Roman][LEFT][FONT=arial]**NVIDIA® GeForce® 9300M**[/FONT][/LEFT]
[/FONT][/COLOR].

In /etc/grub.d/10_linux:

```
 if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
      cat << EOF
    set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi
```That's all I could find.  Should I remove the whole thing?

This will only be necessary if you have GRUB_GFXPAYLOAD_LINUX=someresolution set in /etc/default/grub.  You have several options here:

1.  Check if GRUB_GFXPAYLOAD_LINUX is in /etc/default/grub.  If so comment it out and run update-grub.
2.  Delete the 4 lines of code  from 10_linux.  Run update-grub and see if it helps.  It surely would not make it worst.
3.  At the grub boot menu, press 'e' to edit the highlighted entry.  Check if there's set gfxpayload=keep command iin the list.  If so, delete the line, reboot and see if it helps.  If so, then do 1 or 2 to make it permanent.
4.  At the grub boot menu, press 'c' to get the grub command line.  Check if any efi modules are loaded with the command 'lsmod'.  You only need the efi modules if you are using a Mac.

Can you say which version of grub you're using?  It's usually shown at the top of the grub boot menu.  Or from a Terminal enter 'grub-install --version'.  Try both methods, sometimes there's a discrepency between the two returned versions if the bootloader was not updated after installing a different version of grub.

---

### Post by lalop on 2010-07-20
> **towheedm said:**
> This will only be necessary if you have GRUB_GFXPAYLOAD_LINUX=someresolution set in /etc/default/grub.  You have several options here:

1.  Check if GRUB_GFXPAYLOAD_LINUX is in /etc/default/grub.  If so comment it out and run update-grub.
2.  Delete the 4 lines of code  from 10_linux.  Run update-grub and see if it helps.  It surely would not make it worst.
3.  At the grub boot menu, press 'e' to edit the highlighted entry.  Check if there's set gfxpayload=keep command iin the list.  If so, delete the line, reboot and see if it helps.  If so, then do 1 or 2 to make it permanent.
4.  At the grub boot menu, press 'c' to get the grub command line.  Check if any efi modules are loaded with the command 'lsmod'.  You only need the efi modules if you are using a Mac.

Can you say which version of grub you're using?  It's usually shown at the top of the grub boot menu.  Or from a Terminal enter 'grub-install --version'.  Try both methods, sometimes there's a discrepency between the two returned versions if the bootloader was not updated after installing a different version of grub.

1.98, both methods agree.  I tried options 1-3 (don't think there's any for 1 or 3), don't think I managed 4.  Still no luck, unfortunately.

---

### Post by towheedm on 2010-07-20
> **lalop said:**
> 1.98, both methods agree.  I tried options 1-3 (don't think there's any for 1 or 3), don't think I managed 4.  Still no luck, unfortunately.

Grub 1.98-1ubuntu5 or 6?
Are you using a PC or Mac?
What is unetbootin?

---

### Post by lalop on 2010-07-20
> **towheedm said:**
> Grub 1.98-1ubuntu5 or 6?
Are you using a PC or Mac?
What is unetbootin?

GNU GRUB 1.98-1ubuntu6
PC Vaio VGN-Z46SD
Live usb creator: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by towheedm on 2010-07-20
Try the following:

Downgrade grub.  Use the following command:
```
sudo apt-get install grub-pc=1.98-1ubuntu5 grub-common=1.98-1ubuntu5
```If you've manually modified any of grub's script files, back them up first.

During the install process, replace all script file with the package maintainer's version when asked.  Also install the bootloader to an MBR, ie: sda, sdb etc, NOT sda1,sda2,sdb1 etc.

NOTE:  Do not re-boot unless you were ask were to install the bootloader to.  If you were not asked, install it manually using:
```
sudo grub-install /dev/sda
```If this helps you've found the problem, namely GRUB.  If not, continue on.

Manually booting the kernel. Press 'c' at the boot menu and enter the following grub commands:

Assuming grub in on the first partition of the first drive, enter:
```
set root='(hd0,1)'
```where hd0 is the first drive, hd1 the second etc, and 1 is the partition number of the root partition.

Load the kernel, enter:
```
linux /boot/vmlinuz-version root=/dev/sda1 ro
```where version is the kernel version, 2.6.32-23-generic etc.  If you're not sure, press 'TAB' after 'vmlinuz-' and you'll get a list of all available versions.  If there is only one version, the command will auto-complete.
sda1 if root is on the partition 1 of th first drive.

Load the initramfs, enter:
```
initrd initrd.img-version
```where version should be the same as the kernel version.  If it's not, you may have problems.

Now boot the kernel using the command:
```
boot
```If the problem persist, then the kernel is at fault.  Try installing an earlier version of the kernel.

Let me know how it goes.

---

### Post by lalop on 2010-07-21
Just saw your new post.  I want to give an update on what I did before attempting your solution.  I tried reinstalling ubuntu to formatted drives twice.  The results were weird.  Some of this info might be useless.

The first time, I went straight to recovery mode, and it worked, albeit cut me off at a few of the command line prompts.  Then I went into normal mode, tried ctl alt f1 (didn't work), opened recovery mode, and it black screened again.

The second time, I again went straight to recovery mode.  It didn't work.  But when I went to normal mode, ctl alt f1 did work for once, coherently.  I did sudo shutdown now as a test, but this led to it hanging at some weird error: Cannot write bytes; broken pipe.  I had to power down.  From then on, neither recovery nor ctl alt worked.

So I'm not sure if it being able to work once in a blue moon is any good information, but there it is.

---

### Post by towheedm on 2010-07-21
Does your PC have a built-in diagnostic, or probably on a CD.  Run the tests several times looking for intermittent problems.  Try installing an earlier 64 bit kernel and since you've now done what you were avoiding, ie: re-installing, try installing Lucid 32 bit.  I believe on the Ubuntu site or somewhere I remember seeing where installing 64 bit Lucid was dis-couraged.

---

### Post by lalop on 2010-07-22
Edit: I think I managed a temporary fix.  What I did was set visual effects, under System-> Appearance, to None.

---

### Post by towheedm on 2010-07-22
Ok that's great.  So you did re-install the nVidia proprietary drivers.  I was of the impression you wanted to sort out the problem before re-installing the drivers, so I thought you were using the Nouveau driver.

---

