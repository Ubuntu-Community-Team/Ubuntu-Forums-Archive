---
title: "Problems seeing a HDD"
date: 2009-11-17
forum: General Help
---

### Post by milenixloerdi on 2009-11-17
Hi,

After trying Ubuntu within vista, I installed it clean (formatted on ext4 everything - I have 2 HDD connected - one is Maxtor, the other one is WDC 150 GB) on my Maxtor HDD, path /dev/sdb mount point /. The WDC drive has path /dev/sda1 and mount point /root.

After logging in Ubuntu, I can only see one of my hard drives - the Maxtor. In the directory dev no sda1 is present. Disc Utility recognises the 150GB WDC as "mounted", but I cannot simply see it.

I would appreciate some ideas of how to really "mount" my other HDD so that it shows.

Thanks

---

### Post by Giblet5 on 2009-11-17
You set aside a partition for /root?

Open a terminal window, enter the following command, and post the output inside a CODE block ('#' icon of the comment editor)

```
sudo fdisk -l
```

---

### Post by mithun.kamath on 2009-11-17
Are you able to see your hard drives in "Places" ?
Are you getting any authentication window?

---

### Post by milenixloerdi on 2009-11-17
> **Giblet5 said:**
> You set aside a partition for /root?

Open a terminal window, enter the following command, and post the output inside a CODE block ('#' icon of the comment editor)

sudo fdisk -l[/code]


Hi Giblet thanks for trying to help.

When I started the command, this is what appeared:

```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b896ac1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18241   146520801   83  Linux

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd5bcd5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9964    80035798+  83  Linux

Disk /dev/sdc: 515 MB, 515768320 bytes
16 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 992 * 512 = 507904 bytes
Disk identifier: 0x000f3122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1005      497983+  82  Linux swap / Solaris
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(61, 254, 63) logical=(1004, 0, 62)
Partition 1 does not end on cylinder boundary.
/dev/sdc2            1005        1016        5664+  82  Linux swap / Solaris
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(62, 0, 1) logical=(1004, 1, 1)
Partition 2 has different physical/logical endings:
     phys=(62, 179, 52) logical=(1015, 7, 45)
Partition 2 does not end on cylinder boundary.
```

---

### Post by milenixloerdi on 2009-11-17
> **mithun.kamath said:**
> Are you able to see your hard drives in "Places" ?
Are you getting any authentication window?

No, I can't. I have no premissions to enter /root (it has a little x next to the folder)

---

### Post by Giblet5 on 2009-11-17
> **milenixloerdi said:**
> Hi Giblet thanks for trying to help. I do not understand what do you mean by "post the output inside a CODE block ('#' icon of the comment editor)". Can you please tell me more when you can...thanks!

Open a terminal window (Applications -> Accessories -> Terminal)

Enter ```
sudo fdisk -l
``` and hit the Enter key.

Use your mouse to scroll to the top of that command's output, and left-click at the begiining of the text. Holding the left mouse button down, drag the cursor down the page to highlight all of the output. Release the left mouse button. Right-click the selected text and select "Copy" from the menu that pops up.

Click the "New Reply" button at the bottom or top of this web page. The Comment Editor will appear. Click the '#' icon at the top of that editor. Hit the Shift+Ins keys on your keyboard. Click the "Submit Reply" button below the comment editor.

---

### Post by milenixloerdi on 2009-11-17
Thanks, Im sorry I didnt get what you mean initially...I'll post it here again:

```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b896ac1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18241   146520801   83  Linux

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd5bcd5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9964    80035798+  83  Linux

Disk /dev/sdc: 515 MB, 515768320 bytes
16 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 992 * 512 = 507904 bytes
Disk identifier: 0x000f3122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1005      497983+  82  Linux swap / Solaris
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(61, 254, 63) logical=(1004, 0, 62)
Partition 1 does not end on cylinder boundary.
/dev/sdc2            1005        1016        5664+  82  Linux swap / Solaris
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(62, 0, 1) logical=(1004, 1, 1)
Partition 2 has different physical/logical endings:
     phys=(62, 179, 52) logical=(1015, 7, 45)
Partition 2 does not end on cylinder boundary.
```Basically, I would like to use this other HDD to copy my /home folder so that in case something goes wrong, I can re-install ubuntu on the Maxtor drive and just copy/paste the "home" folder. Thanks

---

### Post by Giblet5 on 2009-11-17
OK. That's what I needed.

Open a terminal window and enter the following commands:

```
sudo mkfs /dev/sda1
sudo mount /dev/sda1 /mnt -text
cd /home
sudo bash ## DANGEROUS! ENTER COMMANDS EXACTLY! USE COPY/PASTE!
tar cf - . | (cd /mnt ; tar xf -)
exit  # BACK TO SAFE USER MODE
```

That set of commands formatted /dev/sda1 and mounted it at the /mnt directory. Then it copied all folders and files from /home to /mnt. Let's verify this:

Enter ```
ls -l /home
ls -l /mnt
```

The listings should match, aside from the top directory names.

If so, then execute ```
rm -fr /home/*
sudo umount /dev/sda1
sudo mount /dev/sda1 /home -text
sudo gedit /etc/fstab
```

That block of commands removed the old /home files, mounted the disk on top of the /home directory, and started the gnome editor on a file that we need to edit to make this automated from now on.

Scroll to the bottom of gedit's window.

At the bottom, add a blank line, then paste this line at the bottom:

```
/dev/sda1  /home  ext3  noatime,auto  0  2
```

Now save the file and exit gedit.

In the terminal window, run the following command:

```
df
```

The last drive listed should be mounted on /home and there should be a lot of free disk space available.

Log off. Log in.

You're all set.

---

### Post by milenixloerdi on 2009-11-17
Thanks Giblet5. Im proceeding with care - is this message normal? 
```
hristo@Home:~$ sudo mkfs /dev/sda1
[sudo] password for hristo: 
mke2fs 1.41.9 (22-Aug-2009)
/dev/sda1 is mounted; will not make a filesystem here!
hristo@Home:~$ sudo mount /dev/sda1 /mnt -text
mount: unknown filesystem type 'ext'
hristo@Home:~$ cd /home
hristo@Home:/home$ 

```

Im continuing and this appeared (files are still being copied)

```
root@Home:/home# tar cf - . | (cd /mnt ; tar xf -)
tar: ./hristo/.google/desktop/a1_sock: socket ignored
tar: ./hristo/.google/desktop/a3_sock: socket ignored
tar: ./hristo/.google/desktop/a4_sock: socket ignored
tar: ./hristo/.google/desktop/a2_sock: socket ignored
tar: ./hristo/.cache/ubuntuone/log/syncdaemon.log: file changed as we read it

```

I hope all works fine :)

---

### Post by Giblet5 on 2009-11-17
You said that /dev/sda1 was not mounted.

It *was* mounted.

Where?

```
df
```

will tell you. Post the output here.

No, it's not OK to proceed with these directions when what you told me is wrong.

---

### Post by milenixloerdi on 2009-11-17
> **Giblet5 said:**
> You said that /dev/sda1 was not mounted.

It *was* mounted.

Where?

```
df
```will tell you. Post the output here.

No, it's not OK to proceed with these directions when what you told me is wrong.


Im sorry I didnt get it. The command is still copying information....can I stop it safely?

I cannot type "exit" yet...

---

### Post by Giblet5 on 2009-11-17
Hit Ctrl+C.

---

### Post by milenixloerdi on 2009-11-17
Thanks. This is what I get when "df":

```
^C
root@Home:/home# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             78779268  50309280  24468200  68% /
udev                   2058748       324   2058424   1% /dev
none                   2058748       220   2058528   1% /dev/shm
none                   2058748       196   2058552   1% /var/run
none                   2058748         0   2058748   0% /var/lock
none                   2058748         0   2058748   0% /lib/init/rw
/dev/sda1            144221592    208740 136686812   1% /boot
/dev/sdd1              1956564    290492   1666072  15% /media/28D43B75D43B447A
root@Home:/home#
```

---

### Post by Giblet5 on 2009-11-17
You set aside 135GB for /boot. In your original post, you called it /root...

Is this a new install?

If so, I would reinstall from scratch and use /dev/sda1 for /home (format it). I would delete /dev/sdb1 and create a new 64GB partition as / (format it). Just leave the unused space unused. You'll come up with a use for it eventually.

If not, run the following command and post the output (it will complain about a file, ignore that and wait for it to display a number)

```
sudo du -sm /home
```

---

### Post by milenixloerdi on 2009-11-17
> **Giblet5 said:**
> You set aside 135GB for /boot. In your original post, you called it /root...

Is this a new install?

If so, I would reinstall from scratch and use /dev/sda1 for /home (format it). I would delete /dev/sdb1 and create a new 64GB partition as / (format it). Just leave the unused space unused. You'll come up with a use for it eventually.

If not, run the following command and post the output (it will complain about a file, ignore that and wait for it to display a number)

```
sudo du -sm /home
```


Thanks! Do I use ext3 or 4 while formatting? Do I assign some space for "swap"? I have 2 HDD - on which one - /home or / shall I do the installation? Thanks...and sorry I have mucked up with this /boot... The big drive is set as "bootable" at the moment.

---

### Post by Giblet5 on 2009-11-17
Some like ext4 others like ext3.

I think ext4 has better overall performance.

The installation process will take care of making bootable what needs to be bootable. Ubuntu doesn't care about the active partition flag anyway. It boots from the master boot record of the first disk drive.

---

### Post by milenixloerdi on 2009-11-17
Ok, thank you a lot! I will reinstall tonight.

---

### Post by milenixloerdi on 2009-11-17
Hi again,

After re-formatting and re-installing + updating Ubuntu in the way you mentioned, I still cannot see all my drives in "Places". Both HDD (WDC 150GB ext4 and  Maxtor 82GB 64GB ext4 Filesystem + 18GB Unallocated Space) are reported as mounted (using Palimpset Disk Utility to see these things). I also appear to have an "ASAP" drive (516MB) that I could not erase (created within vista, asus mb) - it appears as an USB drive, and a Floppy Drive (which I do not physically have on my computer).


```
hristo@Desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             61519876   2452756  55942080   5% /
udev                   1547788       304   1547484   1% /dev
none                   1547788       116   1547672   1% /dev/shm
none                   1547788        84   1547704   1% /var/run
none                   1547788         0   1547788   0% /var/lock
none                   1547788         0   1547788   0% /lib/init/rw
/dev/sda1            144221592    193572 136701980   1% /home
```What is the best way to proceed in order to be able to see the hard-drives in "Places" in a similar way to when I was trying Ubuntu as an installation within windows?

Thanks

---

