---
title: "Similar Picture Seach/Tiny Eye"
date: 2011-11-24
forum: General Help
---

### Post by NertSkull on 2011-11-24
So here's a question I have not been able to find any information on yet.

Is there a way to do a "reverse image" search in ubuntu.  Similar to what tiny eye does.  But instead of searching the web, searching folders on my drive.

Details:

I've scanned in a few thousand loose negatives.  I'm now scanning in (in batch) a lot of prints.  Not all the prints match the negatives and vice versa.  But some do.

I want to scan in all the prints.  Then take each one, and "compare" to the negatives.  If the negative of that picture is scanned in, I'll toss that print.  Otherwise, I'll keep the print (because the negative must be lost).

But I don't want to do this by hand.  I want something like TinyEye, but to have the input be my print.  And the database which with it compares to be a directory on my computer (instead of the TinyEye web directory).

I hope that makes sense.  And I hope this is doable.  Any thoughts?

---

### Post by NertSkull on 2011-11-27
bump

---

### Post by searchfgold6789 on 2011-11-27
Well, I don't know a specific way of doing that, but it seems like something the imagemagick suite would be able to do. At least this will bump you up a notch.
 - search

---

### Post by NertSkull on 2011-11-28
So, that was a good place for me to start.  Imagemagick has a compare utility that may do what I want.

Its amazingly slow, so I have to convert everything to a small thumbnail, but that's not a big deal.

Here's where I'm stuck though.

If the images are different, it errors out saying "too different" and then it stops.

So how can I get it to skip the "too different" images and go to the next one until it gets on that is similar.

I hope that made sense.  I'm sure I just need some sort of command line magic to search against the entire directory.

---

### Post by searchfgold6789 on 2011-11-28
What's the command you're using now; what exactly have you tried?

---

### Post by NertSkull on 2011-11-28
So, this is what I'm using right now.  It uses compare on all my images in the Pictures/test folder.  So I've got that part.

But the comparison doesn't work.  It doesn't find the scanned print to be the same to the scanned negative.  Even if I use mogrify to make both exactly 100x100 I still don't get them finding eachother.

I feel I'm getting closer though. 

```
find -iname "*.jpg" | xargs -l -i compare -subimage-search ~/Pictures/original.png {} ~/Pictures/test/{}
```

---

### Post by searchfgold6789 on 2011-11-28
OK, if they were both different resolutions then some of the pixels will be removed, discolored, or reassigned to a different position and the image will be different than it was before. The only way they'll be the same is if the colors in each picture in each pixel are the same. I'm sure there's a way to make the command only scan a range of colors in both pictures, and that may be exactly what you want.
By "print" I'm assuming you mean a full-colored photograph. You'll have to find some way to compare, for example, only certain colors (channels I think they're called?) of the print to the same channel of the negative. When comparing with a negative, you may want to compare only the black and white channels of the print with the black and with channels of the negative.
The command line stuff is beyond me, but I hope this post helped you in some way.
 - search

---

