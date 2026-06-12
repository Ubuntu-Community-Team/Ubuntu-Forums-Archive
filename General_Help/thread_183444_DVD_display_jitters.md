---
title: "DVD display jitters"
date: 2006-05-28
forum: General Help
---

### Post by Timokl on 2006-05-28
Hi,

I failed to get a decent DVD playback on my Acer notebook (Aspire 5020 -- technical details: [http://www.acer.co.th/product/travelmate/aspire5020_/index.htm)](http://www.acer.co.th/product/travelmate/aspire5020_/index.htm)).

Playback using Xine is right now unbearable -- it feels like DVD playback on a 200 MHz machine.

Playback with MPlayer is far from perfect but bearable -- although I would not want to watch a whole movie with it.

I think it's a problem of the DVD-CDR drive (it's a Philipps SCB 5265). I activated DMA for this drive already, which made MPlayer more smooth but still not really usable.

I use Ubuntu 5.10 (32-Bit kernel), although there is an AMD Turion 64 CPU in the machine. (64 Bit kernel made too many problems for a newbie to Linux :-))

What can I do to get better DVD playback? Any idea is apreciated.

Regards,
Timo

BTW: DVD playback under Windows XP with the same notebook looks very nice. So, there should be a way to do the same with Linux, right? :p

---

### Post by lukew on 2006-05-28
[QUOTE=Timokl]Hi,

I failed to get a decent DVD playback on my Acer notebook (Aspire 5020 -- technical details: [http://www.acer.co.th/product/travelmate/aspire5020_/index.htm)](http://www.acer.co.th/product/travelmate/aspire5020_/index.htm)).

Playback using Xine is right now unbearable -- it feels like DVD playback on a 200 MHz machine.

Playback with MPlayer is far from perfect but bearable -- although I would not want to watch a whole movie with it.

I think it's a problem of the DVD-CDR drive (it's a Philipps SCB 5265). I activated DMA for this drive already, which made MPlayer more smooth but still not really usable.

I use Ubuntu 5.10 (32-Bit kernel), although there is an AMD Turion 64 CPU in the machine. (64 Bit kernel made too many problems for a newbie to Linux :-))

What can I do to get better DVD playback? Any idea is apreciated.

Regards,
Timo

BTW: DVD playback under Windows XP with the same notebook looks very nice. So, there should be a way to do the same with Linux, right? :p[/QUOTE]
Hi,

There is a section in the ubuntu wikki on this. Is DMA enabled on your dvd drive?

[https://wiki.ubuntu.com/RestrictedFormats#head-389f8b000408629ef4fbb99723cfe0133fe31e7e](https://wiki.ubuntu.com/RestrictedFormats#head-389f8b000408629ef4fbb99723cfe0133fe31e7e)

I hope this helpe.

Luke

---

### Post by Timokl on 2006-05-28
Hi Lukew,

[QUOTE=lukew]Hi,

There is a section in the ubuntu wikki on this. Is DMA enabled on your dvd drive?

[https://wiki.ubuntu.com/RestrictedFormats#head-389f8b000408629ef4fbb99723cfe0133fe31e7e](https://wiki.ubuntu.com/RestrictedFormats#head-389f8b000408629ef4fbb99723cfe0133fe31e7e)

[/QUOTE]

Thanks for your answer. DMA is turned on already for the DVD drive. 

See this one, but I am not sure about the last line's meaning:

```
timo@ubuntu:~$ sudo hdparm /dev/hdc
Password:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```

Sounds like something with the DVD region.

But i think there might be some problem with my dvd drive, as ripping audio with soundjuicer is also awfully slow (0,4x).

Bye,
Timo

---

### Post by lukew on 2006-05-29
[QUOTE=Timokl]Hi Lukew,



Thanks for your answer. DMA is turned on already for the DVD drive. 

See this one, but I am not sure about the last line's meaning:

```
timo@ubuntu:~$ sudo hdparm /dev/hdc
Password:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```

Sounds like something with the DVD region.

But i think there might be some problem with my dvd drive, as ripping audio with soundjuicer is also awfully slow (0,4x).

Bye,
Timo[/QUOTE]
You IO is only 16 bit, it should be 32 bit, you also dont have unmaskirq set to on.

If you are convinced it is not the cdrom why not opy the cab files onto your hd and run them from there. At least it can rule out your dvd drive.

I hope this sets.

Luke

---

### Post by crispy_420 on 2006-05-29
I had problems on my laptop too. I got frustrated and tried a different player. I eventually tried VLC. For me it player fine. No jerking or stuttering, like xine gave me. I had full menu support but the only downside was telling VLC when to look for the DVD drive.

---

### Post by Timokl on 2006-05-30
Hi Luke,

[QUOTE=lukew]You IO is only 16 bit, it should be 32 bit, you also dont have unmaskirq set to on.[/QUOTE]

How could I do that. Do I have to edit hdparm.conf? (Might be a RFM question, but I am not an experienced Linux user - yet. :mrgreen: )

[QUOTE=lukew]If you are convinced it is not the cdrom why not opy the cab files onto your hd and run them from there. At least it can rule out your dvd drive.[/QUOTE]

Actually, I think it **is** the DVD drive. 

Bye,
Timo

---

### Post by Timokl on 2006-05-30
[QUOTE=crispy_420]I had problems on my laptop too. I got frustrated and tried a different player. I eventually tried VLC. For me it player fine. No jerking or stuttering, like xine gave me. I had full menu support but the only downside was telling VLC when to look for the DVD drive.[/QUOTE]

I have VLC installed, too. But it gives me other headaches. :evil: 

Bye,
Timo

---

