---
title: "Why are thumbnails stored as pngs instead of jpegs"
date: 2009-11-19
forum: General Help
---

### Post by lavinog on 2009-11-19
I went through my ~/.thumbnail folder and noticed that all of the thumbnails are stored as png files.
I converted all of them to jpeg to see the size difference and 140mb of png files were converted to 40mb of jpgs.
The average png file was 20k while the average jpg was 4k.

What is the reason for using png over jpg for thumbnails.
There are many complaints about nautilus being too slow to generate thumbnails...could switching to jpeg address this?

---

### Post by emigrant on 2009-11-19
png are transparent unlike jpg, jpg make a white background.

---

### Post by lavinog on 2009-11-19
> **emigrant said:**
> png are transparent unlike jpg, jpg make a white background.

But is the transparency used?
I can understand if the source material had transparency, but many of my thumbnails are of jpegs.  Wouldn't it make more sense to at least check if the source file supports transparency then choose from png, or jpeg.

---

### Post by dcstar on 2009-11-19
> **lavinog said:**
> I went through my ~/.thumbnail folder and noticed that all of the thumbnails are stored as png files.
I converted all of them to jpeg to see the size difference and 140mb of png files were converted to 40mb of jpgs.
The average png file was 20k while the average jpg was 4k.

What is the reason for using png over jpg for thumbnails.
There are many complaints about nautilus being too slow to generate thumbnails...could switching to jpeg address this?

Using a lossy compression format that takes more CPU time to create is hardly going to make things quicker.

---

### Post by lavinog on 2009-11-19
> **dcstar said:**
> Using a lossy compression format that takes more CPU time to create is hardly going to make things quicker.

They are both compression formats:

```

time convert image.pnm image.jpg

real	0m0.588s
user	0m0.560s
sys	0m0.130s
-------------------
time convert image.pnm image.png

real	0m3.707s
user	0m3.720s
sys	0m0.150s

```
converting to png took 6x longer than to jpg.

Even in video conversion, lossy encodes faster than lossless.

---

### Post by betlog on 2010-08-23
perhaps you should talk to the people working that :
http://jens.triq.net/thumbnail-spec/index.html

I am currenly looking for a solution to slow and frequently reloading thumbnails.
Whenever I open my more heavily populated folders in firefox, to upload or save an image, I can end up waiting several minutes while it finishes loading all of the thumbs, and because I sort by date, the thumbs jump around a lot until it's finished, making selecton almost impossible.

---

### Post by Ginsu543 on 2010-08-23
Png is the default image format for the entire OS. All the default icons are in png format. And icons do require transparency. I guess Ubuntu went for quality over speed.

---

### Post by betlog on 2010-08-23
edit: my issue has diverged from this thread somewhat, so separating it now.
to: [http://ubuntuforums.org/showthread.php?p=9758295](http://ubuntuforums.org/showthread.php?p=9758295)

---

### Post by lavinog on 2010-08-24
The funny thing is, you can generate the thumbnails as jpegs, and replace the thumbnails with them (with the png extension) and the thumbnails will still display correctly.

Why do the thumbnails need to have a png extension...isn't that a windows thing to do?

---

### Post by betlog on 2010-08-24
afaik, system-wide, linux will ignore the extension and actually check whats in the file.. so it doesnt really need an extension
the fact that jpg will still work as a thumb is pretty cool... sucks for anyhting using alpha.. but nice to know if you want to we cqn test stuff with a different format.

maybe you could do some comparitive time trials comparing the two different formats for stuff 
Time to load a huge folders thumbs which have been previously generated... and relative size, and how that relates to overflowing (or not) the default maximum_cache=512 setting i mentioned in the thread i linked above

---

