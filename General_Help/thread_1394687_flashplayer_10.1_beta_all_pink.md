---
title: "flashplayer 10.1 beta all pink"
date: 2010-01-30
forum: General Help
---

### Post by horseradish on 2010-01-30
Hi, I installed the new flashplayer beta 10.1 and the video is good except it is all a pink haze. It seems to have problems with colors.

Im presuming it is to do with a flashplayer installation problem, or could it be my video settings etc ? (eg perhaps my integrated video card can't take the strain ?)

Thanks

---

### Post by saturnblackhole on 2010-01-30
or it could be the fact that the plugin is beta :-\" , is this happening with every flash site or one in particular?

---

### Post by warfacegod on 2010-01-30
> **saturnblackhole said:**
> or it could be the fact that the plugin is beta :-\" , is this happening with every flash site or one in particular?

Have you tried other sites?

---

### Post by horseradish on 2010-01-30
Actually it does work on other sites. So far only youtube and BBC Iplayer are unwatchable. Apparently the new beta makes use of video accelaration on graphics cards, so perhaps my card isnt up to it. Sometimes I get a glimpse of the correct image and the colors are spectacular. Also the colors are very vivid on the sites that work correctly. I also noticed my computer works fullscreen on BBC Iplayer (with color problem) whereas before it was too much for it.

---

### Post by warfacegod on 2010-01-30
> **horseradish said:**
> Actually it does work on other sites. So far only youtube and BBC Iplayer are unwatchable. Apparently the new beta makes use of video accelaration on graphics cards, so perhaps my card isnt up to it. Sometimes I get a glimpse of the correct image and the colors are spectacular. Also the colors are very vivid on the sites that work correctly. I also noticed my computer works fullscreen on BBC Iplayer (with color problem) whereas before it was too much for it.

This sounds like two bad options to me. If it were me, I'd revert back to the older Flash.

---

### Post by warfacegod on 2010-01-30
May be look to see if there is a better video driver.

---

### Post by horseradish on 2010-01-30
> **warfacegod said:**
> May be look to see if there is a better video driver.

my VGA seems to be

VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

Do you know which driver I would choose ?

---

### Post by warfacegod on 2010-01-30
I'm on VIA's site right now. Can you post this ```
sudo lshw
``` I only need the display section. Example:

```
       *-display
                description: VGA compatible controller
                product: NV34M [GeForce FX Go5200 64M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:c1000000-c1ffffff memory:e0000000-e7fff
```

---

### Post by warfacegod on 2010-01-30
I need to know which OS you are using as well.

---

### Post by horseradish on 2010-01-31
> **warfacegod said:**
> I'm on VIA's site right now. Can you post this ```
sudo lshw
``` I only need the display section. Example:



```
*-display UNCLAIMED
                description: VGA compatible controller
                product: KM400/KN400/P4M800 [S3 UniChrome]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:d8000000-dbffffff(prefetchable) memory:dc000000-dcffffff memory:dd000000-dd00ffff(prefetchable)

```

I am using Ubuntu 9.10

---

### Post by warfacegod on 2010-01-31
The VIA site doesn't seem to have a driver for your card and the S3 Graphics site is down. Try that site later maybe. You'll be searching for "S3 UniChrome". In the mean time, I'm off to sleep.

[http://www.s3graphics.com/]("http://www.s3graphics.com/")

---

### Post by horseradish on 2010-01-31
ok thanks.

---

### Post by warfacegod on 2010-01-31
The S3 site still refuses to open. It might be time to consider going back to the older Flash.

---

### Post by horseradish on 2010-01-31
> **warfacegod said:**
> The S3 site still refuses to open. It might be time to consider going back to the older Flash.

I managed to download the S3 driver yesterday before the site went down. I don't know how to install it though

---

### Post by warfacegod on 2010-01-31
Are you using a laptop?

---

### Post by horseradish on 2010-01-31
Pc

---

### Post by warfacegod on 2010-01-31
Then I urge you to go get a cheap nVidia card. One of my friends is telling me that S3 has virtually no support at all. I'm not sure they exist anymore and it's likely that the driver you downloaded is the one you are already using that Ubuntu installed.

---

### Post by horseradish on 2010-01-31
I had uninstalled the flash installer. Now I put it back and everything seems to be working. Not sure what version is being used now, or if it switched depending on capability. I have 10.0 and 10.1 in my firefox addons.

---

### Post by warfacegod on 2010-01-31
Is it behaving itself?

---

### Post by t12121 on 2010-02-21
I had the same issue with a nvidia 4400ti graphics under 10.1 pink haze under ubuntu 9.10.  10.0 works fine. Maybe its just my card is so old.

---

