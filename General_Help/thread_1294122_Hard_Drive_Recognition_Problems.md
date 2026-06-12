---
title: "Hard Drive Recognition Problems"
date: 2009-10-17
forum: General Help
---

### Post by tom.swartz07 on 2009-10-17
Hi All,

Im in the process of trying to install Karmic to my system and triple boot with Windows Vista, Jaunty, and now Karmic. 
Ideally, Karmic would install in the 51.31GB unallocated space after sda5, avoiding any problems with the 4 primary partition limit. 
[IMG]http://lh4.ggpht.com/_tORug_uHNu4/Stp5OS9I08I/AAAAAAAAAIs/5IW6Ctq5LBA/s800/Screenshot--dev-sda%20-%20GParted.png[/IMG]

Both Vista and Jaunty work perfectly fine, but for some reason, when I run the Live CD, or try to install the OS on my system, the hard drive is not detected.

When the live cd begins the preload- and normal messages about bootup appear (at least on my system, cpu bits not cleared by bios, etc) there is another message that appears. 

```
ata1: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t4
ata1: SErr: {HostInt handshk}
```
At the end of the first line, *T4*, it counts down to 1; in total the error messages appear 5 times then it quickly says: "EH pending after 5 tries, giving up" and it finishes booting to the desktop. 
I should also note that just before each of the "tries" the disk activity light flashes but from that point on, it stays lit continuously. 

Ive looked in the BIOS settings to try and enable an ATA usage, as per some other threads, but there was no such command in my BIOS.
The system is a Dell Inspiron 1521 with AMD Turion 64 Dual Core. 4GB RAM. The drive is a brand new Western Digital Scorpio Blue, 320GB; I just installed it last weekend and this is the first problem I've had with it. As I said before, it is listed in the BIOS under the hardware page, but there is no option to edit the ATA or AHCI use.

Anyone able to provide insight to this?
Im unable to decipher the error code, but I feel that it is the main reason that I cannot access the drive. Any help would be greatly appreciated. 

Thanks!
Tom

---

### Post by tom.swartz07 on 2009-10-18
bump

---

### Post by Luis Macias on 2009-11-08
.

---

