---
title: "Supported Multimedia Formats"
date: 2011-02-13
forum: General Help
---

### Post by ddjolley on 2011-02-13
Is it documented anywhere exactly what multi-media formats I can expect Ubuntu to support out of the box?  If so, a pointer to that documentation would be appreciated.  It would also be nice for me to know exactly what package is responsible for providing the support for each supported format.

Thanks for any input.

          ... doug

---

### Post by dabl on 2011-02-13
That's a fairly tall order.  Did you review this already: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by uRock on 2011-02-13
It would probably be easier to ask what packages are needed for the format you are trying to use.

---

### Post by ddjolley on 2011-02-14
> Did you review this already: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Yes.

> That's a fairly tall order. 

I certainly didn't intend to place a "tall order".  :) I appologize; but, I don't understand why that would be a "tall order".   The document that you cited refers to Ubuntu's commitment to only include completely free software by default.  It is my understanding that because of this policy and the licensing restrictions associated with most codecs, Ubuntu ships with support for a very limited number of multi-media file formats.  For example, I have determined empiraclly that Ubuntu ships with support for the ogg format.  This is not surprising since the ogg format is a completely free format.  Similarily Ubuntu does not ship with MP3 support because that is not a completely free format.  Why is it so difficult to put together a list of the formats (likg ogg) that Ubuntu supports out of the box?  I would expect that to be a fairly short list.  I would also think that such a list would be very useful to newbies like myself because it would allow us to know exactly what we can expect from Ubuntu out of the box in terms of multi-media support and therefore (by implication) also what multi-media formats are going to require other arrangements.  What am I missing?

Thanks.

          ... doug

---

### Post by uRock on 2011-02-14
All formats are supported out of the box, if you installed Ubuntu 10.10 and selected to install the Fluendo package while running the installer. Otherwise, all closed source media is not supported out of the box.

---

### Post by dabl on 2011-02-14
> **ddjolley said:**
> 

I certainly didn't intend to place a "tall order".  :) I appologize; but, I don't understand why that would be a "tall order".   



Perhaps the estimated size and difficulty of the job differs according to who has to do the work.  ;)

If it's not me, then I can agree -- it's trivially easy!  :D

Seriously, the wiki list of all electronic file formats is here: [http://en.wikipedia.org/wiki/List_of_file_formats](http://en.wikipedia.org/wiki/List_of_file_formats)

Looking at just "sound/music" (62) and "video" (30), that's a mere 92 files that need to be collected and tested.  I don't know where I would find, or how I would create a lot of those formats -- do you?

---

### Post by ddjolley on 2011-02-14
I truly appologize for being so dense.

> All formats are supported out of the box, if you installed Ubuntu 10.10
> and selected to install the Fluendo package while running the installer. 

By out-of-the-box I mean WITHOUT the Fluendo package.  So, the above sentence does not relate to my question.

> Otherwise, all closed source media is not supported out of the box.

I understand that.  I'm simply asking what *OPEN* source multi-media formats *ARE* supported out of the box.  I have given one example, ogg.  I am simply asking if there are other open source multi-media formats (in addition to ogg) that are supported out-of-the-box (i.e., without the Fluendo package).  Maybe ogg is the only format on the list.  Maybe (as I thought one commentator might be suggesting) the list is so long that it would be impractical to present.  I find that hard to believe; but, I guess it's possible.  I just don't know even a few formats that would be on such an incredibly long list.

Anyway, I'm just trying to clarify this point so that I understand it.  So far (unfortunately) I am not real clear.

Thanks.

         ... doug

---

### Post by uRock on 2011-02-14
> **ddjolley said:**
> I truly appologize for being so dense.

> All formats are supported out of the box, if you installed Ubuntu 10.10
> and selected to install the Fluendo package while running the installer. 

By out-of-the-box I mean WITHOUT the Fluendo package.  So, the above sentence does not relate to my question.

> Otherwise, all closed source media is not supported out of the box.

I understand that.  I'm simply asking what *OPEN* source multi-media formats *ARE* supported out of the box.  I have given one example, ogg.  I am simply asking if there are other open source multi-media formats (in addition to ogg) that are supported out-of-the-box (i.e., without the Fluendo package).  Maybe ogg is the only format on the list.  Maybe (as I thought one commentator might be suggesting) the list is so long that it would be impractical to present.  I find that hard to believe; but, I guess it's possible.  I just don't know even a few formats that would be on such an incredibly long list.

Anyway, I'm just trying to clarify this point so that I understand it.  So far (unfortunately) I am not real clear.

Thanks.

         ... dougFrom what you are saying Ubuntu doesn't offer partitioning out of the box either, yet your system was partitioned, unless you used the Wubi installer.

Almost all formats are supported out of the box on Ubuntu 10.10.

---

