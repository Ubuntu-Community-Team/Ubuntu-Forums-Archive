---
title: "'Mount of root filesystem failed' after moving /usr"
date: 2009-11-18
forum: General Help
---

### Post by anyusername on 2009-11-18
Hi,

On my Eee PC 701, running Ubuntu 9.10 Remix, I followed the instruction on the page listed below to move my /usr folder to my SD card and all went well (seemingly). Everything that I installed went into the new /usr folder on the SD card, thus confirming that the move had worked. However, when I moved the old /usr folder elsewhere and rebooted I get the error message 'Mount of root filesystem failed.'. Any ideas on how to fix this?

[http://gkahla.net/blog/2009/02/13/sd-card-for-usr-on-dell-mini9/]("http://gkahla.net/blog/2009/02/13/sd-card-for-usr-on-dell-mini9/")

Thanks,

Carl

---

### Post by Giblet5 on 2009-11-18
Reinstall. Don't do that again.

/usr is a folder not to be trifled with and SD cards are guaranteed to fail REALLY fast, as compared with hard drives.

If you meet the braniac who came up with this idea, well, you know what to do.

---

### Post by anyusername on 2009-11-18
> **Giblet5 said:**
> Reinstall. Don't do that again.

/usr is a folder not to be trifled with and SD cards are guaranteed to fail REALLY fast, as compared with hard drives.

If you meet the braniac who came up with this idea, well, you know what to do.
Thanks, but I don't need to reinstall. Moving the old /usr folder back and removing the line added to/etc/fstab reinstates everything. However, this does not resolve the initial issue, as I need to free up space on the system drive - which is a 4Gb SSD device. I don't think that the SD card memory would be any less reliable than the SSD drive as they are both flash memory.

---

### Post by Giblet5 on 2009-11-18
> **anyusername said:**
> Thanks, but I don't need to reinstall. Moving the old /usr folder back and removing the line added to/etc/fstab reinstates everything. However, this does not resolve the initial issue, as I need to free up space on the system drive - which is a 4Gb SSD device. I don't think that the SD card memory would be any less reliable than the SSD drive as they are both flash memory.

SSD drives are much more reliable than SD cards.

The manufacturers of a 4G SSD will give you 6G of storage and a clever algorithm that spreads writes out over the full 6G. Sneaky! And it works. But the SSD will still fail sooner than a $40 320GB hard disk (which will work but reduce your on-battery runtime)

You might want to look at getting a bigger SSD. The prices are dropping really fast and no matter what you do, 4G will never be enough.

If like me, you're in frugal-mode, you can start removing packages that you don't need/use. eg, evolution, samba, etc., to free up space.

Using an SD card though...bad idea.

---

### Post by anyusername on 2009-11-19
Unfortunately, SSD drives are expensive compared to SD cards and I can't justify the spend. I was hoping that SD would be an acceptable solution as I have a couple of spares but the 'Mount of root filesystem failed' is stopping me from trying. My intention was to keep a backup on a second SD card, in case the main one died.

---

### Post by dcstar on 2009-11-19
> **anyusername said:**
> Hi,

On my Eee PC 701, running Ubuntu 9.10 Remix, I followed the instruction on the page listed below to move my /usr folder to my SD card and all went well (seemingly). Everything that I installed went into the new /usr folder on the SD card, thus confirming that the move had worked. However, when I moved the old /usr folder elsewhere and rebooted I get the error message 'Mount of root filesystem failed.'. Any ideas on how to fix this?

[http://gkahla.net/blog/2009/02/13/sd-card-for-usr-on-dell-mini9/]("http://gkahla.net/blog/2009/02/13/sd-card-for-usr-on-dell-mini9/")


And you did replace the "mmcblk0p1" with your own specific hardware, didn't you?

---

### Post by dcstar on 2009-11-19
> **anyusername said:**
> Unfortunately, SSD drives are expensive compared to SD cards and I can't justify the spend. I was hoping that SD would be an acceptable solution as I have a couple of spares but the 'Mount of root filesystem failed' is stopping me from trying. My intention was to keep a backup on a second SD card, in case the main one died.

Also, if the system does not detect and mount the SD card at boot up, it cannot use it for a System folder.

Better to put /home on the SD as that is only accessed at user logon.

---

### Post by anyusername on 2009-11-19
> **dcstar said:**
> And you did replace the "mmcblk0p1" with your own specific hardware, didn't you?
Hi,

Yes I did, mine is sdb1. Ubuntu reads the files fine from the SD card, so it knows the new location. To confirm this, if I install anything new, through synaptic, it now appears in the SD card /usr folder. Plus, if I remove the SD card then Ubuntu cannot open any applications. The problem only occurs at boot if I move the old /usr folder to a different location.

---

### Post by anyusername on 2009-11-19
> **dcstar said:**
> Also, if the system does not detect and mount the SD card at boot up, it cannot use it for a System folder.

Better to put /home on the SD as that is only accessed at user logon.
My computer certainly enables the SD card at boot as it appears as one of the devices I can boot from when I press ESC during boot. Wouldn't Ubuntu mount the card during boot, especially as /etc/fstab points to it?

The line added fstab is:

```
/dev/sdb1 /usr ext4 noatime 0 0
```

sdb1 is definitely the SD card.

---

### Post by anyusername on 2009-11-19
I've fixed the issue. It appears that it's necessary to have a /usr folder on the boot drive, even if there is nothing in it. To try this, I have renamed the original usr folder to usr.bak and created a new empty one.

These links helped;

[http://doc.ubuntu-fr.org/deplacer_repertoire_usr]("http://doc.ubuntu-fr.org/deplacer_repertoire_usr")
[http://ubuntuforums.org/showthread.php?t=1048874]("http://ubuntuforums.org/showthread.php?t=1048874")

There's still the issue of whether an SD card is up to the job though, or whether it's life will be too short.

---

