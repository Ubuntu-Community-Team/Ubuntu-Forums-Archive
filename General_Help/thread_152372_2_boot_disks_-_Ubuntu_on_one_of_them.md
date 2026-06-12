---
title: "2 boot disks - Ubuntu on one of them"
date: 2006-03-29
forum: General Help
---

### Post by AndyOB on 2006-03-29
Hi,
I downloaded and installed Ubuntu yesterday (I am brand new to Linux).
I have two identical SATA 200GB HDD and didn't want to overwrite my Windows disk as I didn't know which it was at the time, so I just unplugged one (and fortunately my guess was correct - it was the Windows one). I installed Ubuntu on a partition on my remaining drive, and all went well.

Unfortunately, when I reconnect the windows drive, and make the Ubuntu drive my primary in the BIOS, it gets a little way into loading then says unable to findd /dev/sda3 which I am pretyt sure is the name of the partition where Ubuntu lives. any suggestions on how to fix this? Am thinking I'll have to reinstall with the Windows drive connected, now that I know which one it is.

---

### Post by ispmarin on 2006-03-29
Hello there. AndyOB, this is the thing: when you disconnect one of your harddrives, the BIOS sets the address of the hd as primary. When you put it together with the other hd, the BIOS (I guess) is putting the Ubuntu drive as secondary, even if you put on the BIOS as primary. You are in a confortable situation: you can install safely Ubuntu on the second HD - Ubuntu, on installation, should detect windows on the other harddisk and put it to boot. So try a shot and install Ubuntu with the windows HD connected.

---

### Post by AndyOB on 2006-03-29
Gracias Snr. Marin.
The drives are SATA not IDE, so I am not sure how the bios assigns priority. Previously I have had the option of booting up with :

SATA0 = SAT0 and SATA1 = SATA1 

                       OR

SATA0 = SATA1 and SATA1 = SATA 0

This effectively allows me to swap which drive has been seen as the "boot" drive. I was hoping not to have to reinstall but I think I will give that a go and report back tomorrow....

---

### Post by ispmarin on 2006-03-29
You can try another thing: when grub is booting, hit the letter "e" and tries to change /dev/sda3 to /dev/sdb3... or something like that. Then hit "b", and sees what happens.

---

### Post by AndyOB on 2006-03-31
Well, I tried last night and it installs fine but I am a little unsure about where to put the GRUB boot loader. 

I am reluctant to stick it on my WindowsXP drive's MBR, because I don't know how easy it is to remove GRUB if at a later stage I get rid of Ubuntu. I tried installing it to /sdb3 (3rd partition on my second drive which is ubuntu) and it comes up with an error on GRUB boot that....*trying to remember as I didn't write it down* "Can't find Dev(1,2)" or something like that

Is the boot partition of the "second" drive going to always be partition number 0? or is it 1?

will keep playing around I think....

---

