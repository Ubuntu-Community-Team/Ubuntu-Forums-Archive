---
title: "View temp of graphics card via terminal"
date: 2009-08-07
forum: General Help
---

### Post by ubudog on 2009-08-07
How do I do this?  By the way my graphics card is nvidia.  Thanks! :)

---

### Post by blueridgedog on 2009-08-07
You can view the temp with "sensors".

To install and setup:

```
sudo apt-get install lm-sensors
sudo sensors-detect
```

Then to run it:

```
sensors
```

Determining which is your gfx card and which are motherboard and CPU may take some figuring on your end.

---

### Post by ubudog on 2009-08-07
> **blueridgedog said:**
> You can view the temp with "sensors".

To install and setup:

```
sudo apt-get install lm-sensors
sudo sensors-detect
```

Then to run it:

```
sensors
```

Determining which is your gfx card and which are motherboard and CPU may take some figuring on your end.

Thanks for the help! :P

---

