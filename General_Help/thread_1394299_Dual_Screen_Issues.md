---
title: "Dual Screen Issues"
date: 2010-01-30
forum: General Help
---

### Post by nicangeli on 2010-01-30
Hello all,

I am trying to switch from Windows 7 to Ubuntu 9.10 but I am having trouble with getting dual screens set up properly.

My laptops resolution is: 1366 * 768
My second monitor's resolution is: 1920 * 1080

On the smaller monitor the mouse can go off the bottom of the screen so I cannot see it. This makes it difficult to click on anything on the panel at the bottom of the screen. This was a standard setting in Windows. Is there a way to make the cursor stay within the bounds of the smaller resolution on the smaller screen, and within the bounds of the bigger resolution on the larger screen? 

The second issue is with the second monitor. It is placed to the right of my laptop. On the far left of this screen there are always around 3px of the laptop's display showing. e.g. when nothing is open and I can see a few px of the top and bottom toolbar on the second monitor.

Can anyone help me with these issues? 

Thanks in advance.

---

### Post by chewearn on 2010-01-31
Please let us know the make/model of graphics processor in your laptop.

Or run this command to find out what Ubuntu has detected:
```
lshw -c display
```

To make it easier to read, post the output between [noparse]```
 
```[/noparse] tag.

---

### Post by nicangeli on 2010-01-31
```

  *-display               
       description: VGA compatible controller
       product: Radeon Mobility HD 3670
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:31 memory:d0000000-dfffffff(prefetchable) ioport:2000(size=256) memory:cfef0000-cfefffff memory:cfe00000-cfe1ffff(prefetchable)


```

Thanks

---

### Post by chewearn on 2010-01-31
Ah, the dreaded ATI graphics.  I'm not familiar with fixing ATI problem, have to defer to someone else, sorry.

---

### Post by audiomick on 2010-01-31
Hallo.
I am using nVidia, but I expect the "dead space" at the bottom of the laptop screen has the same explanation as it does in an nVidia Twin View setup.

You said
> My laptops resolution is: 1366 * 768
My second monitor's resolution is: 1920 * 1080


In order to cover the two monitors (in Twin View, at least) the video driver makes a single screen emcompassing the total width and the total height of the two monitors. In your case, that would mean a screen 3286 x 1080. Since the laptop monitor is only 768 high, there are 312 pixel rows on the screen that are outside the laptop monitor.

This can't be changed. On my (nVidia ! ) setup, on which both screens are always connected, I have put my panels on the larger screen. To do this, I had to de-expand them : right click on an empty part of the panel, properties, uncheck the expand box, move them to where I wanted, and re-expand. I have a "dead space" abouve and below my smaller screen, but it deosn't hinder me. Windows on the smaller monitor maximise to fit the monitor. Every now and then I lose the Menu bar on a window into the dead space at the top, and have to expand the window into the larger screen to get at it.

As far as your overhanging pixels go, I think that is really something ATI specific that I can't help with.

---

### Post by nicangeli on 2010-01-31
> **audiomick said:**
> 
This can't be changed. On my (nVidia ! ) setup, on which both screens are always connected, I have put my panels on the larger screen. To do this, I had to de-expand them : right click on an empty part of the panel, properties, uncheck the expand box, move them to where I wanted, and re-expand. I have a "dead space" abouve and below my smaller screen, but it deosn't hinder me. Windows on the smaller monitor maximise to fit the monitor. Every now and then I lose the Menu bar on a window into the dead space at the top, and have to expand the window into the larger screen to get at it.

Ok thanks, I had thought of this as a possible solution... it seems to work even if it is a little inelegant.

---

