---
title: "Ubuntu wont show my USB flash drive Plz help"
date: 2010-12-30
forum: General Help
---

### Post by Mindswap1 on 2010-12-30
I really need to put my files onto this flash drive. Its brand new, but for some reason when I put it into my computer it doesn't detect it. I'm freaking out right now. The USB i have is a PNY USB Flash Drive Attache. Plz help!

---

### Post by mikewhatever on 2010-12-30
What's the output of the **sudo fdisk -l** command?
I suppose you could try mounting it manually with something like this:
```
sudo mount /dev/sdb1 /mnt
```

---

### Post by Mindswap1 on 2010-12-30
After putting in the command sudo fdisk -l I got the following. 


```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da282

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29255   234983424   83  Linux
/dev/sda2           29255       30402     9212929    5  Extended
/dev/sda5           29255       30402     9212928   82  Linux swap / Solaris
```

And I tried manually mounting it, and got the following. 

```
mount: special device /dev/sdb1 does not exist
```

---

### Post by karthick87 on 2010-12-30
Are you sure that you plugged-in your USB??I mean plug-in your USB and then type,
```
 sudo fdisk -l
```

---

### Post by Mindswap1 on 2010-12-30
> Are you sure that you plugged-in your USB??I mean plug-in your USB and then type,

You mean like put it into the usb port right? Yeah I did that.

---

### Post by Zzl1xndd on 2010-12-30
Silly question, but have you confirmed that the thumb drive actually works? Its a long shot but it could just be a defective one.

---

### Post by Mindswap1 on 2010-12-30
Yeah its detects my ipod, and psp just fine. :/ thnaks for the suggestion anyway :) I really need to get this to work.

---

### Post by sammiev on 2010-12-30
Your USB flash drive maybe defective. Have you tried it in another computer? GL :)

---

### Post by Zzl1xndd on 2010-12-30
> **Mindswap1 said:**
> Yeah its detects my ipod, and psp just fine. :/ thnaks for the suggestion anyway :) I really need to get this to work.

I didn't mean the USB port, but the actual drive. Has the drive been tested with another PC?

---

### Post by Mindswap1 on 2010-12-30
Yeah I plugged it into my sisters Windows 7 computer, and it works just fine. I really don't want to go back to windows. Please help!

---

### Post by mikewhatever on 2010-12-30
How about the output of the following:

```
dmesg | tail
```

Just replug the flash drive before running the command.

---

### Post by Mindswap1 on 2010-12-30
Hey Mike I plugged in my usb, and ran the command you told me to, and got the following. 

```
[ 2009.589044] usb 2-5: device descriptor read/64, error -62
[ 2009.868073] usb 2-5: new low speed USB device using ohci_hcd and address 4
[ 2010.048064] usb 2-5: device descriptor read/64, error -62
[ 2010.332062] usb 2-5: device descriptor read/64, error -62
[ 2010.612032] usb 2-5: new low speed USB device using ohci_hcd and address 5
[ 2011.021147] usb 2-5: device not accepting address 5, error -62
[ 2011.197086] usb 2-5: new low speed USB device using ohci_hcd and address 6
[ 2011.604036] usb 2-5: device not accepting address 6, error -62
[ 2011.604068] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 2023.781765] [UFW BLOCK] IN=eth0 OUT= MAC=00:21:97:c4:cd:a5:c0:3f:0e:87:78:48:08:00 SRC=94.236.150.241 DST=192.168.1.3 LEN=77 TOS=0x00 PREC=0x00 TTL=111 ID=47020 PROTO=UDP SPT=18459 DPT=51413 LEN=57
```

Once again thanks so much for trying to help me :). I can't thank you enough. Your very kind.

---

### Post by karthick87 on 2010-12-30
What version of ubuntu you are using?

---

### Post by Mindswap1 on 2010-12-30
I am using Ubuntu 10.10 Maverick Meerkat. 32 bit.

---

### Post by Mindswap1 on 2010-12-30
Any more ideas? I really need this by today :/ because I need to put school documents onto it. Plz help.

---

### Post by Mindswap1 on 2010-12-30
Someone helped me get it to work :). All I did was plug it into the usb port on the back of the desktop, and it got recognized.

---

### Post by sammiev on 2010-12-30
> **Mindswap1 said:**
> Someone helped me get it to work :). All I did was plug it into the usb port on the back of the desktop, and it got recognized.

Hi Mindswap1, did you have it plugged into the keyboard as I have seen strange stuff from this before. So you now have it going with the USB port on the back of the computer? Great to hear that! GL :)

---

### Post by TeoBigusGeekus on 2010-12-30
> **Mindswap1 said:**
> Someone helped me get it to work :). All I did was plug it into the usb port on the back of the desktop, and it got recognized.
Get yourself a powered usb hub so that you don't have to always plug your flash drive to the back of your pc (just make sure that the hub _is_ plugged to the back).

---

### Post by invalid penguin on 2011-07-20
I have the same problem. I have a tested and working (on windows system) usb flash drive and usb mouse that do not work or even register on the three USB ports on my ubuntu OS laptop.

I get the following output for sudo fdisk -l and dmesg | tail and sudo mount /dev/sdb1 /mnt:

stephen@stephen-laptop:~$ sudo fdisk -l
[sudo] password for stephen: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
stephen@stephen-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
stephen@stephen-laptop:~$ dmesg | tail
[ 7310.082085] ehci_hcd 0000:00:13.2: port 7 reset error -110
[ 7310.082262] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 7310.286076] ehci_hcd 0000:00:13.2: port 7 reset error -110
[ 7310.286225] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 7310.490078] ehci_hcd 0000:00:13.2: port 7 reset error -110
[ 7310.490221] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 7310.694077] ehci_hcd 0000:00:13.2: port 7 reset error -110
[ 7310.694217] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 7310.694220] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[ 7310.694233] hub 1-0:1.0: unable to enumerate USB device on port 7
stephen@stephen-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
stephen@stephen-laptop:~$ dmesg | tail
[ 7548.308058] usb 2-3: device descriptor read/64, error -62
[ 7548.592029] usb 2-3: device descriptor read/64, error -62
[ 7548.872035] usb 2-3: new full speed USB device using ohci_hcd and address 23
[ 7549.052028] usb 2-3: device descriptor read/64, error -62
[ 7549.336117] usb 2-3: device descriptor read/64, error -62
[ 7549.616023] usb 2-3: new full speed USB device using ohci_hcd and address 24
[ 7550.024023] usb 2-3: device not accepting address 24, error -62
[ 7550.200023] usb 2-3: new full speed USB device using ohci_hcd and address 25
[ 7550.608022] usb 2-3: device not accepting address 25, error -62
[ 7550.608069] hub 2-0:1.0: unable to enumerate USB device on port 3
stephen@stephen-laptop:~$ ^C
stephen@stephen-laptop:~$ sudo mount /dev/sdb1 /mnt
mount: special device /dev/sdb1 does not exist
stephen@stephen-laptop:~$ 

Any help would be appreciated.

---

