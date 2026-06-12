---
title: "De-photoshopping a picture"
date: 2011-10-28
forum: General Help
---

### Post by Total Noob on 2011-10-28
I'm a lawyer; I get digital pictures turned over to me as evidence.

Is there a Linux program that will de-photoshop a pic and take it back to its original, in case the evidence has been doctored, such as to remove something that is there or add something that isn't?

For instance, in this really famous Pulitzer Prize winning photo from the days of film

[IMG]http://images.quickblogcast.com/8/7/2/7/7/187876-177278/Kent_State.jpg[/IMG]

you'll note there seems like there's a pole coming out of her head; it was a rod holding up a temporary fence.

When the pic was published in the paper, the pole was airbrushed out. 

[IMG]http://www.evernote.com/shard/s1/res/4a0833a3-0506-451e-a3e1-3634a35d5ed2.jpg[/IMG]

Is there software that can go back to the original version of a pic in case this has been done to phony up a case?

Thanks.

---

### Post by gsmanners on 2011-10-28
Somehow I doubt this is the right forum for such a question, but I'm going to guess that the answer is no.

---

### Post by Jose Catre-Vandis on 2011-10-28
If the images sent to you are in psd format (or other PS specific format that retains edits), which should then mean that all the layers are still there then yes, you could get at the original (the same as xcf files in GIMP). But if the image has been "flattened", which means all the layers have been combined, and the format is jpg or png or similar, then you most probably won't be able to get at the original.

---

### Post by MG&amp;TL on 2011-10-28
Perhaps the publisher received (and often they do) the original file once they decided it was good enough for publishing.

This is usually RAW format and a metadata file. I believe if you open in a program that can handle RAW editing, you could probably "undo" the changes. I think the GIMP can handle RAW. But I'd have to check.

---

### Post by Nixarter on 2011-10-28
Yes and/or no.  It depends on a few things.

For a full size unedited version, no (when working with only the digital output file).  And by output file, I mean the file as exported from the image editing program (such as photoshop).

When working from a printed version of the output, full or small versions are not possible to recover.  I strongly suggest that you request a digital version, even if you have no idea if one exists.  See below.

However, when working from a digital output file, there are a some techniques that may be of value to you.  (FYI, the subject is media forensics).  

First and foremost, there is often metadata (data about data) within a file.  This ranges from date, time, and even sometimes GPS location of the camera when the image was taken, to any programs used to edit the image.  This can be of value in determining whether or not the image has been manipulated, if that is an issue.  This is text information, though (thus, it can be edited after the fact).

There is a lot more you can do, including possibly getting back unedited smaller versions of the file, and possibly (though less likely) a full uedited version, if certain conditions can be met.  Unfortunately I have to leave, but I will update (probably tomorrow).

---

### Post by Nixarter on 2011-10-30
Often, the digital images are in jpg format, and they (and others) often contain a smaller "thumbnail" (scaled down version of the **original/unedited** image.  So, if the small one is extracted and the large image purported to be real don't match up, something was edited.  This can range from innocent cropping to take out unnecessary information, to alterations with the intent to mislead.  Image manipulation programs (including photoshop) alter some metadata, but often leave other data (like thumbnails) unless they are specifically commanded to remove them.   This also depends on program versions and settings.

Full unedited images can usually be gathered pretty easily, even if they have been deleted, BUT it requires physical access to a storage media that has had the image on it at some point.  This might be useful in a case investigation if the thumbnail doesn't match up with an image someone attempted to enter as evidence, for example.

Imaging techniques should not be ignored as well.  Much can be done to manipulate the light to 'physically' make a misleading image without using an image manipulation program.  There is a vast array of such techniques.

I'm pm you some more info.

---

### Post by Total Noob on 2011-10-31
> **Nixarter said:**
> Often, the digital images are in jpg format, and they (and others) often contain a smaller "thumbnail" (scaled down version of the **original/unedited** image.  So, if the small one is extracted and the large image purported to be real don't match up, something was edited.  This can range from innocent cropping to take out unnecessary information, to alterations with the intent to mislead.  Image manipulation programs (including photoshop) alter some metadata, but often leave other data (like thumbnails) unless they are specifically commanded to remove them.   This also depends on program versions and settings.



How do I access the camera thumbnail that rides with the current version? Can I get it for all kinds of pix, ie, stuff found on line like photos of models and stars that have been adjusted to make them better looking?

Thanks.

---

