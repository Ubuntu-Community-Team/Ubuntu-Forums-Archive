---
title: "Choppy DVD Playback"
date: 2006-04-04
forum: General Help
---

### Post by mohoso on 2006-04-04
apparently DMA mode is on already on my computer but the DVD playback still seems choppy!
is there any thing that can be done?

---

### Post by Hairy_Palms on 2006-04-04
we need more info to help, what video player are you using? 
whats the output of 
sudo hdparm /dev/hdb
assuming your dvd drive is hdb

---

### Post by barebones on 2006-04-04
I had this problem once, and it turned out that It was a dma issue. I have two drives, and I turned on dma via Automatix, but it only turned on the dma on the first of my drives (which is not my dvd player). If you have two different optical drives open up your /etc/hdparm.conf file and maker sure you have the entry
```
dma = on
```
present in the sections for both your drives. In my hdparm.conf, my two drives show up as /dev/cdroms/cdrom0 and /dev/hda.

---

### Post by rameez on 2006-04-11
I had the same problem i.e choppy dvd playback then I uncommented the dma=on section and it worked fine for one day but now the video is choppy again, can anyone help me with this?
Here is the output of sudo hdparm /dev/hdc
```

 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

---

### Post by albinoloverats on 2006-04-11
I had a similar problem, and solved it by adding the following to the end of /etc/hdparm.cong

```
/dev/hdc {
        dma = on
}
```

---

### Post by Blarion on 2006-04-11
Enable DMA

---

### Post by Syco54645 on 2006-04-11
[QUOTE=rameez]I had the same problem i.e choppy dvd playback then I uncommented the dma=on section and it worked fine for one day but now the video is choppy again, can anyone help me with this?
Here is the output of sudo hdparm /dev/hdc
```

 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```[/QUOTE]


run 
sudo hdparm -d1 /dev/hdc

that should enable dma for you.  of course you would have to do this every time, but it will at least let you know if you can enable dma (drive may be bad or something).

-Syco54645

---

### Post by rameez on 2006-04-15
thanks it worked

---

