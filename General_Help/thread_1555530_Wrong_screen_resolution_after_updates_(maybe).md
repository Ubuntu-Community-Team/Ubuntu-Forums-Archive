---
title: "Wrong screen resolution after updates (maybe)"
date: 2010-08-18
forum: General Help
---

### Post by Tank90 on 2010-08-18
Hi all!

Yesterday two things happened:

1. I installed updates using the Update Manager
2. I started playing Hedgewars

I think that one of these things might have caused the optimal screen resolution for my monitor to be removed. When I booted my computer today, the resolution was 1024x768 (should be 1280x1024). In the "Monitors" tool, the highest resolution is 1360x768, and my monitor is no longer recognized (says "Unknown").

After googling quite a bit, I found that running xrandr might help:

```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9

```

I then looked around for ways to add the correct resolution, using xrandr to add new modes. However, I simply cannot believe it has to be this difficult? Must certainly be a driver problem somewhere, but I don't know how to figure out which updates were installed yesterday so that I can undo them.

Everything's been working fine since I installed 10.04, until this happened :-/

Any suggestions? Please tell if I should include any logs or output from commands.

Thanks,

Dan

---

