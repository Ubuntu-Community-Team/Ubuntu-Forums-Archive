---
title: "Screen resolution issues on all-in-one desktop"
date: 2012-09-17
forum: General Help
---

### Post by xeitgeixt on 2012-09-17
I have an Acer z5600 with a multi-touch, 23 inch screen. This is an all in one piece. 

After installing Ubuntu, I noticed that only a small corner of the screen displayed my desktop environment- the rest of the screen was a distorted mess. 

After looking through my options in terms of what I can do to adjust the screen resolution, turns out my hardware isn't recognized and that I have only two, 4:3 choices to pick from (both of which do nothing when selected).

I ran a Google search and couldn't find someone with a similar problem (at least I don't think).

---

### Post by Kirk Schnable on 2012-09-17
We may be able to assist you in finding the correct video drivers.  Can you please supply the output of:

```
lspci -v
```

```
sudo lshw -c video
```

Thanks
Kirk

---

