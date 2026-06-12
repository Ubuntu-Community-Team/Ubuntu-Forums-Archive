---
title: "Advice for a death USB memory stick"
date: 2012-04-20
forum: General Help
---

### Post by esbrinartot on 2012-04-20
Using an Ubuntu live USB my USB got damaged. (without doing nothing)

I've tried to use gparted, fdisk, fsck and testdisk but there is a huge problem.

None of the described software detect the memory stick plugged in the usb port So it's completely impossible to try to apply any of the mentioned possible solutions.

Anyone can give me some advice? Is there anything that I that can try to recover my USB memory stick?

---

### Post by ajgreeny on 2012-04-20
> **esbrinartot said:**
> Using an Ubuntu live USB my USB got damaged. (without doing nothing)

I've tried to use gparted, fdisk, fsck and testdisk but there is a huge problem.

None of the described software detect the memory stick plugged in the usb port So it's completely impossible to try to apply any of the mentioned possible solutions.

Anyone can give me some advice? Is there anything that I that can try to recover my USB memory stick?
Plug it in then use command ```
dmesg | tail
```
That will show the last 10 lines of the dmesg output which may contain the system's detection of the usb drive.  If nothing shows that looks like the flash drive, it may simply have failed with age or use, or perhaps be plugged into a failing usb socket.

---

### Post by esbrinartot on 2012-04-20
> **ajgreeny said:**
> Plug it in then use command ```
dmesg | tail
```
That will show the last 10 lines of the dmesg output which may contain the system's detection of the usb drive.  If nothing shows that looks like the flash drive, it may simply have failed with age or use, or perhaps be plugged into a failing usb socket.

I paste the content of the command you told me. As you could see seems to detect the USB drive. Anyone know what else I could test?


[   77.701202] hda-intel: spurious response 0x4011:0x0, last cmd=0x1f8100
[   77.701219] hda-intel: spurious response 0x0:0x0, last cmd=0x1f8100
[   77.701240] hda-intel: spurious response 0x0:0x0, last cmd=0x1f8100
[   77.814819] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.260034] wlan0: no IPv6 routers present
[  171.280061] usb 1-5: new high speed USB device using ehci_hcd and address 7
[  171.433661] scsi5 : usb-storage 1-5:1.0
[  172.467050] scsi 5:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[  172.468148] sd 5:0:0:0: Attached scsi generic sg6 type 0
[  174.235215] sd 5:0:0:0: [sdf] Attached SCSI removable disk

---

### Post by CharlesA on 2012-04-20
```
sudo fsck /dev/sdf1
```

---

### Post by esbrinartot on 2012-04-21
> **CharlesA said:**
> ```
sudo fsck /dev/sdf1
```

the result that i obtain with the command

sudo fsck /dev/sdf1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: No such file or directory while trying to open /dev/sdf1
Possibly non-existent device?

if i try 
sudo fsck /dev/sdf

fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: No medium found while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I've also tried

sudo e2fsck -b 8193 /dev/sdf

with next result:e2fsck 1.41.14 (22-Dec-2010)
e2fsck: No medium found while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


and then

sudo e2fsck -b 8193 /dev/sdf1
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: No such file or directory while trying to open /dev/sdf1
Possibly non-existent device?

---

### Post by CharlesA on 2012-04-21
It's likely the device is hosed. Have you tried a different PC to rule that out?

---

### Post by esbrinartot on 2012-04-21
> **CharlesA said:**
> It's likely the device is hosed. Have you tried a different PC to rule that out?

I don't know what you mean with hosed. My native language is not english.

Anyway I've tried other computers and other different OS. And the result is always the same and I have the same message errors

---

### Post by CharlesA on 2012-04-21
Yeah, the drive is dead.

---

### Post by esbrinartot on 2012-04-21
> **CharlesA said:**
> Yeah, the drive is dead.

Ubuntu killed mu USB.

I think that Ubuntu is the guilty.

Well anyone is in untested I inform that the funeral will take place tomorrow in Spain.

As a punishment for Ubuntu I promise that I will never install it in another computer

---

### Post by CharlesA on 2012-04-21
> **esbrinartot said:**
> Ubuntu killed mu USB.

I think that Ubuntu is the guilty.

Well anyone is in untested I inform that the funeral will take place tomorrow in Spain.

As a punishment for Ubuntu I promise that I will never install it in another computer
Your OS cannot kill your USB stick. It's likely it just wore out.

I've had a couple like that.

---

### Post by esbrinartot on 2012-04-22
> **CharlesA said:**
> Your OS cannot kill your USB stick. It's likely it just wore out.

I've had a couple like that.

Why an OS can't Kill an USB stick?

I really think is because of Ubuntu but maybe I'm wrong.

I seen other post in other websites from other people that they also had the same problem..

They say USB killed by Ubuntu.

Well I guess I will never know the real reason. MAybe was too old.

---

### Post by CharlesA on 2012-04-22
> **esbrinartot said:**
> Why an OS can't Kill an USB stick?

It doesn't modify the hardware itself. If you plugged it into a box running Windows and it doesn't see it, it means the drive is bad. I had a brand new USB drive keep disconnecting when I was copying files no matter the OS or the USB port used. It still "works" but I'm not bothering with putting files on it because it's so touchy.

> I really think is because of Ubuntu but maybe I'm wrong.

I seen other post in other websites from other people that they also had the same problem..

They say USB killed by Ubuntu.

Link?

---

### Post by cyncicle on 2012-04-22
My condolences - it sounds like you were close. ;)

Charles is correct - there's nothing specific to Ubuntu (or any other OS) that could or would kill a flash drive in normal use.

---

### Post by esbrinartot on 2012-04-22
> **cyncicle said:**
> My condolences - it sounds like you were close. ;)

Charles is correct - there's nothing specific to Ubuntu (or any other OS) that could or would kill a flash drive in normal use.

The burial has been done today. I assumed his death. We have shared nice experiences together. What a pity.

Well Isn't it possible that an over voltage caused the death of my USB?

As you know some linux distributions use open drivers and haven't been designed by the manufacturer. And of course this could be a reason to create an over-voltage. Notice that in most of the hardware the temperatures are higher in Linux than Windows.

---

### Post by coldraven on 2012-04-22
I bought a shockproof and waterproof USB stick and it died in three weeks. How? It did not like being in my pocket, when I sat down it got slightly bent. The connection between the circuit board and the plug is the weak link.

---

### Post by Ericle on 2012-04-30
Like others have mentioned your usb is most likely dead since it cant be recognized by any pc.

Before you gave up you may want to look at your usb drive manufacturer to see if they have any firmware or repair tool.

You would also try this free application which restore usb drive to its original factory states.
[www.pendrivelinux.com/restoring-your-usb-key-partition]("http://www.pendrivelinux.com/restoring-your-usb-key-partition")

install the software on both windows and ubuntu to see if one of them works.

Make sure you try your drive on different computers. I had a drive perfectly working on my Dell laptop but not on my Thinkpad with identical OS.

As stated many times already, if you can't manage to get your drive mounted, none of these tricks will work either.

Good luck

---

