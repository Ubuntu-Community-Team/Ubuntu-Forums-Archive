---
title: "How do I print directly to the printer?"
date: 2010-09-24
forum: General Help
---

### Post by searchfgold6789 on 2010-09-24
I've tried lpr [FILE]
didn't work
I've tried cat [FILE] > /dev/lp0
couldn't figure out how to get to the root prompt

and I googled until my googler was sore. All I got was lengthy and confusing user manuals for cat.

Does anyone have any ideas, besides going through the trouble of loading GIMP everytime I want to print something?

---

### Post by philinux on 2010-09-24
I would think something like.

```
lpr documentname -P Stylus-Photo-R200
```

Should'nt need the name of the -P printer as it will output to the default one.

See man lpr.

Arrgghh. seems to only work with .txt files. .odt files come out garbage.

---

### Post by searchfgold6789 on 2010-09-24
It looks like that would've worked, but my old printer gets a data error... I'll try looking that up.

---

### Post by Mark Phelps on 2010-09-24
> **searchfgold6789 said:**
> Does anyone have any ideas, besides going through the trouble of loading GIMP everytime I want to print something?
If it's an image file, you have no choice.  

The default Linux command (lpr) simply "sends" a file to the printer -- which is expecting ASCII text, not an image file.

---

### Post by KeyserSoze93 on 2010-09-24
Try imagemagick to convert your image to a postscript file, with a line like:

```

convert picture.jpg ps:-|lpr

```

Results may vary - as this does nothing to make your image fit the paper, but it's worth a try.

You'll need to install the imagemagick package, which provides the convert tool.

---

