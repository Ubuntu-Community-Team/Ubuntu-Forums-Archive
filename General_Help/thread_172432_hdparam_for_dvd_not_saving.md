---
title: "hdparam for dvd not saving"
date: 2006-05-08
forum: General Help
---

### Post by PapaWiskas on 2006-05-08
I have done the below, and it used to work.  But lately it seems my dma settings are not being saved for some reason.  I have done nothing to my system other than the ubuntu updates that come out.

I also edited my hdparam.conf to reflect /dev/dvd even though that is not how my drive is listed, it is listed as hdc.

Anyone have any thoughts?

===========================

To enable DMA, you need to use the hdparm command and the configuration file hdparm.conf.
These instructions assume that you are trying to enable DMA on hdc, usually the CD-rom drive.

1.
See the what the settings are on /dev/hdc
sudo hdparm /dev/hdc
2.
If you get a line like using_dma = 1 (on), DMA is already enabled. Skip to step 4 to see if it has been enabled at boot time.
3.
Enable DMA on /dev/hdc
sudo hdparm -d1 /dev/hdc
4.
You have now enabled DMA for the drive. However, in order for the settings to be automatically applied at boot there you need to edit the /etc/hdparm.conf} script. To do this use this command: sudo gedit /etc/hdparm.conf

Add the following to the end of your hdparm.conf

/dev/hdc {
dma = on
}

---

### Post by Ramses de Norre on 2006-05-08
I just noticed my dma was turned off too.. Anyone with an explanation/solution?

---

### Post by PapaWiskas on 2006-05-09
Just a small, polite bump.:)

---

