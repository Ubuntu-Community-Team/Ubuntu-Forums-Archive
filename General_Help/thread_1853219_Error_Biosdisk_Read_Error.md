---
title: "Error: Biosdisk Read Error"
date: 2011-10-01
forum: General Help
---

### Post by I'mNotGay on 2011-10-01
I pulled our old Sony Vaio desktop out of our basement that we haven't used for about a year because we got a new desktop, and plugged it in and played around with it for a while today. It was not used for a while, and was running Ubuntu because my dad accidentally formatted the C\ drive on it (It originally ran XP). Anyway, I was playing around with it, and it just stopped working. It froze up, and when I rebooted it, it said it was loading GRUB, but after a while, it would say "error: biosdisk read error". It then put on a "grubrescue>" prompter on, but after playing around with THAT, and rebooting a couple of times due to freezing, the prompter stopped showing up ,and it just won't boot. Any suggestions on how to fix it?

---

### Post by 2F4U on 2011-10-02
What version of Ubuntu are you running. Googling this error returned several results for some versions of Ubuntu from 2009/2010. You could try to install the newest version and see if it happens again.

---

### Post by I'mNotGay on 2011-10-02
It is running an Ubuntu version from '09. I'm not quite sure of the specifics. It won't let me boot from a system disk. It asks for a system disk, but it won't accept the disk that I originally used to install Ubuntu on the computer.

---

### Post by mörgæs on 2011-10-02
You could try to erase the hard drive completely using Killdisk.

[www.killdisk.com](www.killdisk.com)

---

### Post by Blasphemist on 2011-10-02
Please be specific when you say it just won't boot. Do you see the drive activity LED showing activity? Exactly what all is shown on the display? It should display some bios messages before it even hits the hard drive.

The grub> prompt that you mentioned was a sign that it did see the hard drive as it couldn't get to grub without reading the hard drive unless you do start booting a cd or usb. You should see a message about getting into setup (this is bios) and likely a message accessing a boot menu (where you could choose to boot cd or usb).

---

### Post by I'mNotGay on 2011-10-02
It takes me to a PCI Device Listing Grid, and I have tried using a boot disk, but it won't accept the original disk I used to put Ubuntu on the computer. I was actually going to put OS X Snow Leopard on it, so I really like that KillDisk idea.

---

### Post by I'mNotGay on 2011-10-02
Will the KillDisk work if I just boot the computer from the CD drive with the KillDisk disk in it?

---

### Post by Blasphemist on 2011-10-02
I've never used killdisk so I can't say. I would say that at this point you don't know that it will boot from any cd/usb from the sound of things. If you download and burn an ubuntu live cd you can verify that you can boot and you could use GParted from that to delete the existing partitions and install ubuntu if you want. I don't know what it would take to load lion on it, or even if you could.

---

### Post by mörgæs on 2011-10-03
> **I'mNotGay said:**
> Will the KillDisk work if I just boot the computer from the CD drive with the KillDisk disk in it?

Did you read the link I posted?

---

