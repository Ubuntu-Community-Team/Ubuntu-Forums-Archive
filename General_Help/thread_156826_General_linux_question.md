---
title: "General linux question"
date: 2006-04-07
forum: General Help
---

### Post by fimbulvetr on 2006-04-07
This isn't ubuntu specific so I'm posting it outside of the normal forums. I have a pretty good track record here, so I figured it would be one of my first resources. I have a device I'm trying to get linux working on but the booting kernel output is not all readable. The output is 50% visible with 25% of the remaing on the left non-visible portion and 25% of the right non-visible portion. It's probably the same case for above and below. The last line I see is loading the cfq scheduler so it's likely there's about 3-5 lines of output below that that I am not seeing. 

To the point - does anyone know how to configure the kernel to use, say, a 20x20 screen or something else absurdly small?

p.s. It's an HTC apache phone and I've also posted on xda, so please don't recommend going elsewhere - I already am:) I just know that there are some knowledgeable people around here as well.

---

### Post by 5-HT on 2006-04-08
If this is a resolution issue for the CLI, you can specify which resolution you'd like to use (should take effect for the scrolling kernel messages on boot). Maybe that will help?

To do so, just append vga=### to the kernel boot option (either in menu.lst or just by manually changing it in the grub kernel menu for a one-time thing).

Here is a table of resolution codes:
```

      |640x480|800x600|1024x768|1280x1024|1600x1200|
------|-------|-------|--------|---------|---------|
 8 bit|  769  |  771  |  773   |  775    |  796    |
15 bit|  784  |  787  |  790   |  793    |  797    |
16 bit|  785  |  788  |  791   |  794    |  798    |
24 bit|  786  |  789  |  792   |  795    |  799    |

``` 
Hope this helps.

---

