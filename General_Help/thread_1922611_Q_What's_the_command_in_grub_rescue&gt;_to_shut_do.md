---
title: "Q: What's the command in grub rescue&gt; to shut down or restart?"
date: 2012-02-09
forum: General Help
---

### Post by madeoforanges on 2012-02-09
Hi,

I've been trying remove Ubuntu and I'm trying to install an alternative OS (ie. Apple) and I keep on getting this:

[http://imgur.com/YfuLe](http://imgur.com/YfuLe)

I don't know what else to do! I tried pressing buttons, restarting, and shutting down my system numerous times... and to the point of re-installing Ubuntu to return to its normal state until the terminal screen shows up again. The only thing that boots properly is using Ubuntu's LiveCD. I tried booting from the USB and CDROM drive, but the my computer would skip to Ubuntu's boot to terminal screen.

I spent well over 5 hours on this. I really need help on this, it's driving me crazy and ruining my brand new computer.

PS: The only suspect I can remember is when I held F12 accidentally instead of F11 because I wanted to boot to BIOs. After that, everything went downhill from there. In addition, I have an ASUS USB-N13 wireless adapter and I removed it when I restarted my computer and terminal error still came up.

Honestly, this is scaring me, I want Ubuntu out!

-oranges :(

---

### Post by khaj_vah on 2012-02-09
1. You can not install mac OSX.
2. It wont ruin.
3. Try putting windows disk and boot from that and install windows... 

YEah, one more question: how many partitions do you have and what kind of partitions(ext, NTFS ...)?

---

### Post by elliotn on 2012-02-09
just boot into liveCD and run gparted then format your drive, then restart with your Windows CD in the drive and boot, then install windows... its easy, it has nothing to do with ubuntu

---

### Post by madeoforanges on 2012-02-09
@khaj_vah I formated it to ext4.

@elliotn But why is it doing this? It has to be Linux because when I google'd it, it directed me to Linux related postings. If there is a chance to use Ubuntu without the terminal error, how can I fix it?

I'll try that and I'll report back.

---

### Post by khaj_vah on 2012-02-09
> **elliotn said:**
> just boot into liveCD and run gparted then format your drive, then restart with your Windows CD in the drive and boot, then install windows... its easy, it has nothing to do with ubuntu

I didnt really know that you can run gparted from livecd

Anyway make sure to format to NTFS to be able to install windows

---

### Post by haqking on 2012-02-09
> **madeoforanges said:**
> Hi,

I've been trying remove Ubuntu and I'm trying to install an alternative OS (ie. Apple) and I keep on getting this:

[http://imgur.com/YfuLe](http://imgur.com/YfuLe)

I don't know what else to do! I tried pressing buttons, restarting, and shutting down my system numerous times... and to the point of re-installing Ubuntu to return to its normal state until the terminal screen shows up again. The only thing that boots properly is using Ubuntu's LiveCD. I tried booting from the USB and CDROM drive, but the my computer would skip to Ubuntu's boot to terminal screen.

I spent well over 5 hours on this. I really need help on this, it's driving me crazy and ruining my brand new computer.

PS: The only suspect I can remember is when I held F12 accidentally instead of F11 because I wanted to boot to BIOs. After that, everything went downhill from there. In addition, I have an ASUS USB-N13 wireless adapter and I removed it when I restarted my computer and terminal error still came up.

Honestly, this is scaring me, I want Ubuntu out!

-oranges :(

if its non apple hardware you will violate the EULA by installing MAcOSX on it anyways, and thats if you can get MacOSX on there working in the first place ;-)

If you can boot to Ubuntu Live CD then use gparted

---

### Post by madeoforanges on 2012-02-09
Makes sense.

I get:
```

error: no such partition.
grub rescue>
```

I only have an OS X Lion (I own a Mac), but not Windows, and that leaves me to resort to Ubuntu again... If this whole terminal error goes away, I might switch back.

---

### Post by nothingspecial on 2012-02-09
Violating Apple's EULA is not supported here.

If you want help with the Ubuntu error I can change the title of the thread or better still, why not start a new one with an appropriate title and I will lock this one.

---

### Post by madeoforanges on 2012-02-09
> **nothingspecial said:**
> Violating Apple's EULA is not supported here.

If you want help with the Ubuntu error I can change the title of the thread or better still, why not start a new one with an appropriate title and I will lock this one.

Sounds good to me: You can change the title.

Q: What's the command in grub rescue> to shut down or restart?

---

### Post by nothingspecial on 2012-02-09
Done.

---

### Post by madeoforanges on 2012-02-09
> **nothingspecial said:**
> Done.

Thanks for that.

The main question here is how can I prevent this terminal error from happening again?:
[http://imgur.com/YfuLe](http://imgur.com/YfuLe)

---

