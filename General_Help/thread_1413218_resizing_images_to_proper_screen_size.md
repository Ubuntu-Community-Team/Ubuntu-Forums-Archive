---
title: "resizing images to proper screen size"
date: 2010-02-22
forum: General Help
---

### Post by VitaminCPP on 2010-02-22
I want to watch my photos on PAL TV with 720x576 screen size. I have images 720*520. I don't want my TV to stretch them, so I intend to resize my pics to 720x576 by adding black bars on top and bottom. I can achieve it with GIMP, but I have like 100 photos. Any easier way for it?

Thanks.

---

### Post by chewearn on 2010-02-22
[Imagemagick]("apt://imagemagick") can do what you wanted.  The command is "convert".

E.g. have all the photos in a subdirectory called "in_dir".
Create a subdirectory called "out_dir" to receive the converted photos.

```
for a in $( ls in_dir ); do
convert "in_dir/$a" -background black -gravity center -extent 720x576 \
"out_dir/$a"
done

```

---

### Post by VitaminCPP on 2010-02-22
Thank you, it worked perfectly! Only with 720x576 swapped to 576x720 for vertical images.

---

### Post by geirha on 2010-02-22
> **chewearn said:**
> 
```
for a in $( ls in_dir ); do

```

Never ever do for var in $(ls). Firstly it'll break if there are any odd characters in the filenames (like spaces), and secondly, why use an external command when the shell can do it much better by itself?

```
for a in in_dir/*.jpg; do
```

---

