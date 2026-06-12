---
title: "Problems creating a Video DVD using a DVD+RW Disc"
date: 2010-06-20
forum: General Help
---

### Post by inkhorn on 2010-06-20
I recently got a DVD+RW to use for burning downloaded TV shows onto (so that I didn't have to keep buying to DVD-R's).  I'm having weird problems successfully creating a disc that's compatible with my standalone DVD player.  I've been using DVD Styler, which worked perfectly fine with DVD-R's, and every time the program about to finish burning onto the DVD+RW, it gives me the following error message:

```
/dev/dvdrw: flushing cache
/dev/dvdrw: writing lead-out
:-( unable to reload tray: No such file or directory
Failed
```The odd thing is that I am perfectly able to play the resultant DVD video on my laptop, but not on the standalone DVD player.  I definitely format the DVD before each time I burn onto it.  I'm at my wit's end here!  Does anyone know what I can do to successfully create a video DVD using a DVD+RW on my Ubuntu machine?

Thanks,

Inkhorn

---

### Post by fooman on 2010-06-20
not sure if its your problem or not,  but...

when using dvdstyler, devede and the like...you must format the disc as "NTSC" if in the U.S. in order for you to view them on a standalone dvd player.  not sure about other countries.

hope that helps.

---

### Post by Paddy Landau on 2010-06-20
Check your manual. Not all DVD players can read DVD-RW.

---

### Post by inkhorn on 2010-06-20
I know that my standalone reads this disc.  I just followed a tutorial that tells you how to lump all your videso into one file and burn them and it actually played on my DVD player.  The only problem is that not having chapters makes going from episode to episode very difficult.

I think the problem may be as fooman says.  When I right clicked on the titles in the DVD Styler window and clicked on Properties, it said they were in PAL format.  That probably accounts for why my standalone wouldn't read a thing from the DVD!

Inkhorn

---

### Post by Paddy Landau on 2010-06-21
> **inkhorn said:**
> The only problem is that not having chapters makes going from episode to episode very difficult.
Try ManDVD (in the repositories). Its very first question when you start it is whether to use PAL or NTSC.

ManDVD gives the option of adding each video separately with its own chapter. Additionally, it has an option to define chapters.

---

