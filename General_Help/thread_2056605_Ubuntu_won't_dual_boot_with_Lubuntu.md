---
title: "Ubuntu won't dual boot with Lubuntu"
date: 2012-09-11
forum: General Help
---

### Post by Joon Lee on 2012-09-11
I installed Lubuntu after Ubuntu, but when I start my computer back up, it went straight to the lubuntu login without showing the GRUB option menu for choosing which OS I wanted to boot.

---

### Post by tienlbhoc on 2012-09-11
go to terminal : sudo update-grub (or update-grub2)

---

### Post by Joon Lee on 2012-09-12
Ok thanks. I'll try that and get back to you on that (I'm away at the moment). The following question would probably be answered once I actually try what you suggested, but I ask to satisfy my curiosity: once I update GRUB, would that make Ubuntu the default boot or Lubuntu (though it wouldn';t matter to me which one)?

---

### Post by cortman on 2012-09-12
Whichever OS you installed last will be the default. You can change this though, there's a nice little utility called Startup Manager that can help. Info on that [here]("http://www.howtogeek.com/65974/how-to-easily-change-your-dual-booting-pcs-default-os/").
Also, you can get the GRUB menu by holding shift while it boots.

---

### Post by bhuvneshdave on 2012-09-12
I always suggest to use grub legacy to new bie b'coz it is easy to install and can be modified by editing /boot/grub/menu.lst file. so try to install grub legacy.

---

### Post by oldfred on 2012-09-12
Grub legacy has not been the standard in Ubuntu since 9.04. Early on a lot of us did not understand the new grub2 with 9.10, but now there is little reason to use grub legacy. Ubuntu modified its copy of grub legacy to work with ext4 and only grub2 works with many of the new formats, RAID, UEFI and others system related configurations. 
If you have an old system with grub legacy that works that is ok, but reverting to it is not recommended.

---

### Post by Joon Lee on 2012-09-12
I updated grub, terminal said it found Ubuntu 12.04 LTS, but, when I booted (even while holding shift and confirming the computer said "Starting GRUB" or something like that) it still went straight to Lubuntu.
So I updated GRUB2:

******@******:~$ sudo update-grub2
[sudo] password for ******: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda1
done

and got the same result as when I updated GRUB. I will now reboot again and see if it works.

---

### Post by Joon Lee on 2012-09-12
Still no success. After I updated GRUB, I rebooted, trying without and with holding Shift. The screen said "GRUB Launching" only when I held shift. After I updated GRUB 2, I rebooted, trying without and with holding Shift. The screen said "GRUB Launching" only when I held shift, as before. The GRUB Bootloader Menu did not appear during any of these attempts.
Help?

---

### Post by cortman on 2012-09-12
What is the ouptut of

```
cat /etc/default/grub
```

---

### Post by snowpine on 2012-09-12
No need to dual-boot Ubuntu and Lubuntu. They are the same operating system with different desktop environments (Unity vs. LXDE). From your Ubuntu system you can simply install the package **lubuntu-desktop** (or from Lubuntu install **ubuntu-desktop**) and then you can choose between Unity and LXDE from the login screen.

---

### Post by Joon Lee on 2012-09-12
******@******:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by Joon Lee on 2012-09-12
@Snowpine

Thanks for the information, but I would still like to see this effort through.

---

### Post by oldfred on 2012-09-12
Post the BootInfo report link that this creates:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Joon Lee on 2012-09-13
Thanks!
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1203268/](http://paste.ubuntu.com/1203268/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.


The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

I will now reboot and see if it works!

---

### Post by Joon Lee on 2012-09-13
It didn't.

---

### Post by oldfred on 2012-09-13
You are showing two installs. One is in sda1 and the other in sda8. You also have 3 swaps. 

I might try installing the grub from sda1 to the MBR and see it that boots.

---

### Post by Joon Lee on 2012-09-13
Thanks. How would I do that?

---

### Post by oldfred on 2012-09-13
Does Boot-Repair also offer to install that grub2 boot loader?

If not from liveCD.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda


# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by YannBuntu on 2012-09-13
Hello

Your GRUB is correctly installed, but is hidden.

Please try this:
**1)** (this is OldFred' suggestion of reinstalling the GRUB of Ubuntu)
run Boot-Repair, click "Advanced options", go to the "GRUB location" tab, select "OS to boot by default: sda1", apply. Indicate the new URL that will appear. Reboot and tell us if better.

**2)** run Boot-Repair, click "Advanced options", go to the "GRUB location" tab, select "OS to boot by default: sda6", go to the "GRUB options" tab, tick the "Uncomment GFXMODE" option, apply. Indicate the new URL that will appear. Reboot and tell us if better.

---

### Post by Joon Lee on 2012-09-13
As much as I would like to go through with this attempt, I just have lots of homework every day so I decided to just transfer all my files from Ubuntu to Lubuntu. I appreciate all of you help, however. Now, how would I go about uninstalling Ubuntu, leaving just Lubuntu?

---

### Post by cortman on 2012-09-13
First, **[SIZE=4]Back up your data.[/SIZE]**[SIZE=4][SIZE=2]

Then you can run

[/SIZE][/SIZE]```
sudo grub-install /dev/sda
```

from Lubuntu to install Grub to the MBR. Then open GParted in Lubuntu and delete the Ubuntu partitions. You can then boot from a live CD to expand your Lubuntu partitions to take advantage of the empty space.

---

### Post by Joon Lee on 2012-09-14
Thanks. I did, and will reboot tomorrow (get some sleep) and see how it works!

---

### Post by Joon Lee on 2012-10-23
I'm not sure if I should mark this solved...

---

### Post by oldfred on 2012-10-24
If it is working, you can mark it solved.

---

