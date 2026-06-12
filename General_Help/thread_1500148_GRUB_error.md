---
title: "GRUB error"
date: 2010-06-02
forum: General Help
---

### Post by RamboJesus on 2010-06-02
Ok folks so this is my problem and it is due to a fiarely large oversight on my part. I would really appreciate some help

I dual boot windows xp and ubuntu 9.10 UNR on my asus1005ha Netbook

What happened : I deleted the ubuntu partition and the swap partition through windows xp using Disk management.

Whats happening now : When I power on my netbook grub says the following 

GRUB loading.
Error: no such partition
grub recovery>

anytime I attempt to input any sudo command it says unknown command which makes sense considering the partition no longer exists well, can anyone help me I would much appreciate it.

Edit : Yes I do know what a liveUSB is and I suppose I could use it...

---

### Post by Neill_R on 2010-06-02
Okay I have fixed this on my system several times What version of Windows are you running? What I do have done in the past is to boot from my Windows 7 repair disk and get to a command prompt where I type 

bootrec /FixMbr

and then reboot removing the repair CD \

and I am back booting into windows 7

Then you can reinstall Ubuntu if you wish

---

### Post by RamboJesus on 2010-06-02
I am running windows XP

And the problem is I cant use a windows XP repair disk because its a netbook I am however in the process of making a LiveUSB after that I can take it from there I think, mainly I was wondering if there was any commands I could use to boot windows instead of grub.

---

### Post by yetiman64 on 2010-06-02
To boot Ubuntu you'll need grub, but grub will find XP and put an entry in its menu for you automatically.

Edit: I am assuming your to reinstall ubuntu of course.

---

### Post by RamboJesus on 2010-06-02
> **yetiman64 said:**
> To boot Ubuntu you'll need grub, but grub will find XP and put an entry in its menu for you automatically.

Edit: I am assuming your to reinstall ubuntu of course.

I'm aware I need grub to boot ubuntu but my problem is that grub isn't booting... and I tried a ubuntu liveusb and it doesn't recognize anything. I can't even boot bios it automaically boots grub well fails to boot grub...

---

### Post by smellyman on 2010-06-02
Well the files to boot grub reside on your ubuntu partition which you deleted.

Only way I can think to fix is what has been mentioned.  You have to boot with the xp cd and fix mbr or reboot with Ubuntu live cd/usb and reinstall ubuntu...

---

### Post by yetiman64 on 2010-06-02
> and I tried a ubuntu liveusb and it doesn't recognize anythingOk I see how that's a hassle, will think on it a bit more. Again I assumed a live usb would recognize your machine and work ok. Have done live usb installs myself before including with dual booting.  What OS / methods are you using to build the live usb? As this info may help someone to help you out as well.

---

### Post by RamboJesus on 2010-06-02
> **yetiman64 said:**
> Ok I see how that's a hassle, will think on it a bit more. Again I assumed a live usb would recognize your machine and work ok. Have done live usb installs myself before including with dual booting.  What OS / methods are you using to build the live usb? As this info may help someone to help you out as well.

Ok I just realized that I deleted he ubuntu partition AND the swap space partition which contained grub which it the partition grub is attempting to refer to... And attempting a live usb of UBUNTU NBR 10.04 doesn't work, would 9.10 work? which is what I had on my netbook.

---

### Post by yetiman64 on 2010-06-02
Do you by any chance still have a 9.10 live usb? As it seems you have managed to install it successfully before. I hate to have to say this as I generally prefer clean installs over upgrades, but if you do have a 9.10 live usb you may want to consider an online upgrade to 10.04 (but do note I've seen a few threads on upgrade problems here lately - as usually happens). Something to consider though.

---

