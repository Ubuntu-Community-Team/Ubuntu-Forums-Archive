---
title: "How can string a bunch of JPEGs into a video on ubuntu?"
date: 2011-03-21
forum: General Help
---

### Post by Ulysses1994XF04 on 2011-03-21
I've been going to the gym 4-6 times a week for the past 2 months with the intent of burning off my fat and then building up muscle. I've been taking a picture of myself every day since I've started, and will continue for a few months. To get a better idea of how I'm progressing, I want to string all my pictures together into a video, with each picture being 1/4 second. What software can I use on ubuntu to string a bunch of JPEGs together into a video?

---

### Post by Script Warlock on 2011-03-21
pitivi or openshot

---

### Post by SeijiSensei on 2011-03-21
Another approach is to import the pictures into GIMP and save them as an animated GIF.  During the export process, you can specify the length of time each frame appears on screen.  So for your purposes you'd specify 250 milliseconds for all the frames during export.

To do this, open the initial frame, then use File > Open as Layers, use Shift-Click to highlight all the remaining frames, then OK.  To save, choose Save As, pick GIF from the formats offered, and follow the instructions.

---

