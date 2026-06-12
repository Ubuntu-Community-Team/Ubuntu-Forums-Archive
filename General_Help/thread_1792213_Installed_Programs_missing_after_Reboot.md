---
title: "Installed Programs missing after Reboot"
date: 2011-06-27
forum: General Help
---

### Post by nosaj.08 on 2011-06-27
dear all
I'm newbie to ubuntu or linux ,,,so i has follow website article to create a Ubuntu 11.04 on a 4GB flash drive. And, i has use "EASEUS Partition Master Home Edition" create 2 partition on my USB flash drive (2GB MBR with ubuntu 11.04, 2GB data volume).
I has able to run my Ubuntu11.04 from USB and i was so happy and then start installed VLC player, Ubuntu Tweak, unrar programs. 
after those programs installed,  i reboot the Ubuntu then i encounter all installed programs were missing,,,,the O/S back to it's original state. 
How am i can installed programs in USB flash drive and keep it on USB flash drive.

Please help / advise !!!

TQ,nosaj

---

### Post by jerrrys on 2011-06-27
sounds like you missed this

[ATTACH]196144[/ATTACH]

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

more here

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by nosaj.08 on 2011-06-29
hi jerrrys,
i has follow your guide but still the VLC program was missing after i reboot the machine.

what should i do next ? pls help,,,,,

thnks,nosaj

---

### Post by nzjethro on 2011-06-29
By the looks of it, you need to lide the "Set a persistence file size..." slider along. By the looks of it, this is tha amount of space on the USB allocated to storing your changed settings. If that's set to 0, it won't save your settings (it won't have any space to!). What you plan on doing with your Live USB (i.e. without installing) will determine how much space you should allocate. If you're unsure, be safe and put allocate as much space as possible.

---

### Post by nzjethro on 2011-06-29
Also, apologies if this is an incredibly stupid observation, but I imagine your are using Ubuntu "Live" (i.e. trying Ubuntu by booting from the USB stick each time) rather than installing it.

Are you wanting to have Ubuntu actually installed on your computer, so that all the programmes you install and changes you make will be permanent? Or are you wanting to continue booting from a USB to "try Ubuntu out" without making parmanent changes to your computer?

---

