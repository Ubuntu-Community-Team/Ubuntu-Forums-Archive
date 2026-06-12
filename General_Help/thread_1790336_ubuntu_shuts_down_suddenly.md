---
title: "ubuntu shuts down suddenly"
date: 2011-06-24
forum: General Help
---

### Post by lmp90 on 2011-06-24
sometimes when i'm using ubuntu it will suddenly shut down and display the following.
```
[33987.669983] btusb_intr_complete: hci0 urb f6866700 failed to resubmit (1)
[33987.670980] btusb_bulk_complete:hci0 urb ed6d2a00 failed to resubmit (1)
[33987.671978] btusb_bulk_complete:hci0 urb ed6d2800 failed to resubmit (1)
[33988.580551] legacy_resume(): scsi_bus_resume+0x0/0x60 returns 262144
[33988.580556] PM: Device 0:0:0:0 failed to restore async: error 262144
```i'm new to linux so i don't know what any of this means
any help would be appreciated.

---

### Post by heyandy889 on 2011-06-24
Ah. I have found a clue.

I fed your error message into Google. What I got out is that your error has something to do with Bluetooth. This makes some sense, because the error message begins with "btusb," meaning Bluetooth USB. 

Maybe try unplugging your Bluetooth mouse or headphones and rebooting?
Good luck!

---

### Post by lmp90 on 2011-06-25
I see. I don't have a bluetooth mouse, but I do have a bluetooth usb adapter i got for my ipod. i'll try, see if it works.

---

### Post by lmp90 on 2011-06-25
it did it again but this time it said:
```
fsck from util-linux-ng 2.17.2
/dev/sdb5: c;ean, 274056/2138112 files, 4771836/8544921 blocks
*Starting AppArmor profiles     Skipping profile in /ect/apparmor.d/disable: usr.bin.firefox
                                                                                      [ OK ]
*Setting sensors limits                                                         [ OK ]
Starting VMware services:
VMware USB Arbitrator                                  done
Virtual machine monitor                                done 
Virtual maching communication interface                done 
VM communication interface socket family               done 
Blocking file system                                   done
Virtual ethernet_
```see screenshots
i had music and it just kept skipping a part
i had to restart it

---

### Post by lmp90 on 2011-07-31
bump

---

### Post by lmp90 on 2011-08-13
bump

---

