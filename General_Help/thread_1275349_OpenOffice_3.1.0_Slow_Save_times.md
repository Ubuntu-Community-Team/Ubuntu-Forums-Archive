---
title: "OpenOffice 3.1.0 Slow Save times"
date: 2009-09-25
forum: General Help
---

### Post by fisheater on 2009-09-25
Hi all!

So far my switch to open source has been very good, thanks to all you out there who make it happen for not technical users.

I am writing a document in OpenOffice 3.1.0 and am finding that the save times are very long, 1-2 minutes. On occasion even longer 3-5 min.

The document is 119 pages long mostly text with a few pics in jpg/png/gif formats, max resolution 300 dpi. Most of them are 72 dpi. It is saved as a native odt file. File size 12 MB.

It is slow on both a win xp computer at work and my linux 9.04 at home. Both computers are fairly new with good ammouts of ram (1.5 - 2.5 GB).

I have searched this and found others with similar problems but no clear solution. Is this because there is none?

Thanks for you assistance in this.

---

### Post by cbtengr on 2009-09-25
> **fisheater said:**
> Hi all!

So far my switch to open source has been very good, thanks to all you out there who make it happen for not technical users.

I am writing a document in OpenOffice 3.1.0 and am finding that the save times are very long, 1-2 minutes. On occasion even longer 3-5 min.

The document is 119 pages long mostly text with a few pics in jpg/png/gif formats, max resolution 300 dpi. Most of them are 72 dpi. It is saved as a native odt file. File size 12 MB.

It is slow on both a win xp computer at work and my linux 9.04 at home. Both computers are fairly new with good ammouts of ram (1.5 - 2.5 GB).

I have searched this and found others with similar problems but no clear solution. Is this because there is none?

Thanks for you assistance in this.

You might find some information at the OpenOffice forum:

[http://www.oooforum.org/](http://www.oooforum.org/)

---

### Post by Hagar Delest on 2009-09-26
Personally, I prefer [http://user.services.openoffice.org/en/forum/](http://user.services.openoffice.org/en/forum/). :mrgreen:

How have you added the pics? If by copy-paste, it may have increased the size of the file because they can have been changed to .png. Make a copy of the file, open it with an archive manager and see what are the biggest files in the /pictures folder. If biggest are in .png and should be in .jpg, open them with a picture manager, save them in .jpg and replace them in OOo by using the menu Insert>Picture>From file (and not by copy-paste).

---

### Post by fisheater on 2009-09-28
Hagar,

Thanks for the post, that is what I did for the pics (cut and paste). I will attempt what you suggest - though I am not sure what you mean. I will try and use 7-zip and see if that will open the file. If not I will take some of the big pics out and reformat them to jpg. (Why does that make such a difference? Size of file?)

Thx!

FE

---

### Post by Hagar Delest on 2009-09-28
.png format is a lossless format whereas .jpg is a compressed format that leads to quality loss. So a jpg pic will take much more space if saved as png because every pixel has been recorded. Even worse if a pic has been saved as jpg before because the jpg format introduces some blur that defeats the compression algorithms of the png format.

---

