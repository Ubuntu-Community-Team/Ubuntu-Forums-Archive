---
title: "DMA all of a sudden disables and wont re-enable. Please help"
date: 2006-04-14
forum: General Help
---

### Post by LightsOut on 2006-04-14
I had DMA enabled on my dvd burner before. DVDs played perfect and i was abe to burn at the correct speeds. Today i put in a dvd and it starts playing all choppy and stuff. I figure all I needed to do was hdparm -d1 /dev/hdc and everything would be cool again. However when I tried to do it I get this error:

setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

Here's the output of hdparm /dev/hdc:
[root@localhost etc]# hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device




I googled around and i found that i might have to compile some things into my kernel. I dont see why this is needed since i had this working two days ago! I dont understand why DMA isnt enabled in the first place. Linux seems so far behind when it comes to simple things like DVD playback. Why in the hell would I want to watch and burn my dvds at 1x speeds? This should be one of those things that "work out of the box"!

---

### Post by Ramses de Norre on 2006-04-14
Did you try ```
**sudo** hdparm -d1 /dev/hdc
```
What's the content of /etc/hdparm.conf?

---

### Post by LightsOut on 2006-04-14
contents of hdparm.conf

/dev/hdc {
    dma = on
}

---

### Post by dcstar on 2006-04-16
[QUOTE=LightsOut]I had DMA enabled on my dvd burner before. DVDs played perfect and i was abe to burn at the correct speeds. Today i put in a dvd and it starts playing all choppy and stuff. I figure all I needed to do was hdparm -d1 /dev/hdc and everything would be cool again. However when I tried to do it I get this error:

setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
......[/QUOTE]
Check that your BIOS hasn't been reset to PIO only for that drive.

---

