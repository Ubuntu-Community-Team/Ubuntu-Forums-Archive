---
title: "Linux client for Amazon Cloud Drive?"
date: 2012-04-25
forum: General Help
---

### Post by Legendário on 2012-04-25
I see that Amazon is charging only US$ 20 a year for 20Gb of space and unlimited space for song in it's Amazon Cloud Drive, which I find a very good price, even converting to my country's currency: [https://www.amazon.com/clouddrive/learnmore](https://www.amazon.com/clouddrive/learnmore)

Unfortunetely (as always) they don't have a client for Linux. Is there any option for this case? Does anyone know an open source client for that?

---

### Post by techsupport on 2012-04-25
> **Legendário said:**
> I see that Amazon is charging only US$ 20 a year for 20Gb of space and unlimited space for song in it's Amazon Cloud Drive, which I find a very good price, even converting to my country's currency: [https://www.amazon.com/clouddrive/learnmore](https://www.amazon.com/clouddrive/learnmore)

Unfortunetely (as always) they don't have a client for Linux. Is there any option for this case? Does anyone know an open source client for that?

Probably because Ubuntu wants you to use their native app instead:

[http://en.wikipedia.org/wiki/Ubuntu_One](http://en.wikipedia.org/wiki/Ubuntu_One)

It is almost the same price too. I wouldn't waste my time waiting around for Amazon to provide Ubuntu a client for Amazon cloud services either. There might be a slight conflict of interest there too. :)

:guitar:

---

### Post by oldos2er on 2012-04-25
There's Dragondisk, haven't used it myself though. [http://www.dragondisk.com/](http://www.dragondisk.com/)

---

### Post by Zakhafr on 2012-04-25
It looks like it is could be hosted by the same system and the S3 professional system.

[https://aws.amazon.com/fr/s3/#pricing]("https://aws.amazon.com/fr/s3/#pricing")

(Sorry, as I am French I do automatically get the French page... bad automatic translation though... quite sure you can get the same page in english if you don't understand French)

If so
-A) it looks like a sort of WebDAV as they speak of GET/PUT/COPY/LIST requests. So you could try DavFS2 (in the repositories)
-B) For S3 you could try S3FS (Google it!)

---

