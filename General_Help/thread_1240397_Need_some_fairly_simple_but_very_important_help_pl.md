---
title: "Need some fairly simple but very important help please"
date: 2009-08-14
forum: General Help
---

### Post by The Switch Blade on 2009-08-14
[FONT=Arial][SIZE=2]"Cutting ccd frames into quadrants:
  Lower left of frame is 0,0, upper right is 2048,2048.
  example of each quadrant being cut from the original frame:
    in iraf, for quadrant 1: imcopy file.fits[1025:2048,1025:2048] fileq1.fits
         for quadrant 2: imcopy file.fits[1:1024,1025:2048] fileq2.fits
         for quadrant 3: imcopy file.fits[1:1024,1:1024] fileq3.fits
         for quadrant 4: imcopy file.fits[1025:2048,1:1024] fileq4.fits
    the cutting into quadrants is easily scripted in a bash shell."

Can someone help me devise this script?

I can't just do something like

[/SIZE][/FONT][FONT=Arial][SIZE=2]cl> imcopy 061102_*.fits[1025:2048,1025:2048] 061102_*q1.fits
ERROR: Number of input and output images not the same

because the wildcard doesn't work.

"[/SIZE][/FONT][FONT=Arial][SIZE=2]IRAF (an acronym for Image Reduction and Analysis Facility) is a huge collection of software written by astronomers and by programmers at the National Optical Astronomy Observatory (NOAO) geared towards the reduction of astronomical images in pixel array form, that is, data taken from imaging array detectors such as CCDs"
[/SIZE][/FONT]

---

### Post by The Switch Blade on 2009-08-15
bump

---

### Post by The Switch Blade on 2009-08-15
bump

---

### Post by The Switch Blade on 2009-08-15
bump

---

### Post by Bachstelze on 2009-08-15
This looks very much like a school assignment. Closed.

---

