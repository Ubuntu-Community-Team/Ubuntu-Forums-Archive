---
title: "Asus eeepc 1101HA Recovery option killed 9.10"
date: 2010-03-12
forum: General Help
---

### Post by bwestover on 2010-03-12
I have an eeepc 1101HA with NBR 9.10 dual boot with XP Home

I have been using this configuration successfully for months, after quite a bit of work fixing the sound issues, wifi issues and video issues. It still has a standby issue, but its liveable and Im quite happy with its performance for such an inexpensive machine.

I tried to boot to XP today, and I must have picked the recovery partition by mistake out of the grub menu. It loaded "windows pre-execution environment" and then asked me if i wanted to run recovery. I told it to cancel before it did anything, or so I thought.

It only had 10-15 seconds, so whatever it did couldn't have been much.

When it rebooted I got this error.
```

GRUB loading.
error: no such partition
grub rescue>

```

I booted to a usb stick with the 9.10 live environment, and ran fdisk

```


>sudo fdisk /dev/sda -lu

  Device  Boot     Start         End    Blocks   Id  System
/dev/sda1 *           63    64597364  32298651    7  HPFS/NTFS
/dev/sda2      302246910   312496379   5124735   1c  Hidden W95 FAT32 (LBA)
/dev/sda3      312496380   312576704     40162+  ef  EFI  (FAT-12/16/32)
/dev/sda4      64597365    302246909 118824772+  15  Unknown

```

I believe sda4 is my missing Ubuntu partition and sda1 is windows xp. I don't know what the other two are.

Does anyone know what I can do to recover this partition?

---

### Post by bwestover on 2010-03-15
Update: I booted to a USB stick and tried to mount what I believe to be my ext4 Ubuntu partition, but I got this error.

```

sudo mkdir /mnt/recover
mount -t ext4 /dev/sda4 /mnt/recover
mount: wrong fs type, bad option, bad superblock on /dev/sda4 

```What am I doing wrong? Is there a way to recover the data from this partition?

---

### Post by nateman7097 on 2010-03-28
Mine did the exact same thing last night for no reason. I know now that there is no way to recover my ubuntu, but I would like to know if there is a way to prevent this from happening again? Other than the obvious answer of just not using windows.

---

### Post by bwestover on 2010-03-29
Well, I'm going to be removing that partition from Grub so I can't accidentally select it.

I'm not sure how to do this on Karmic since the change to Grub2 has moved some of the config files.

Time to learn something new!

So did you accidentally end up in the Eeepc recovery program like me? Or did yours just go off on its own?

Your problem might be different if not, since that definitely is what caused it for me. I never did get any responses here, and all normal recovery options for the partition information failed.

I ended up deleting the SDA4 partition where my ubuntu install used to be, and reinstalling Ubuntu onto it. The windows partition and the Eeepc recovery partition were not affected, and windows started working again normally after Ubuntu and Grub2 were isntalled again.

Then I had to do all the other customizations that make this machine bearable under Ubuntu

---

### Post by helmingstay on 2010-06-02
Yup.  Me too.  Wow that sucked.  Bye bye XP.  Bye bye all my efforts.

Does this qualify as a bug?  And in what?  Methinks grub should not add that partition to the grub menu.

-x

---

### Post by bwestover on 2010-06-02
I think the installer scans for valid partitions, and then tries to detect what they are and adds them to the menu. This can be very convenient and even crucial for people doing dual boot. Then you can go back and take it out if you want.

I think the bug here is definitely in the Asus recovery utility. Simply because I chose to boot the recovery option doesn't mean it should IMMEDIATELY destroy an extended partition, with no confirmation.

Also to be clear on what happened to me. I didn't lose XP... I just lost the extended partition that held grub and Ubuntu, leaving the machine unbootable and ubuntu unrecoverable.

I reinstalled Ubuntu, and now the machine boots and I got access back to XP as well.

---

### Post by Alan Jack on 2010-06-21
Has anybody found a valid way of recovering data from a partition lost through this process?  I'd happily reinstall if I could only recover the photos in the lost partition.  :(

---

