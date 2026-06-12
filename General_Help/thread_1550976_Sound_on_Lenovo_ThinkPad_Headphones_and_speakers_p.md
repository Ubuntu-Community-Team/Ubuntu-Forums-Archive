---
title: "Sound on Lenovo ThinkPad Headphones and speakers play at same time"
date: 2010-08-11
forum: General Help
---

### Post by oscargodson on 2010-08-11
It was so close to a perfect install ;)

The only thing really missing is this issue with the sound. I've searched all over the forums and i found one thing where you get the model and codecs and write them to a file, however, I can't seem to find what my "model" is because none of the postings have anything about Lenovo laptops. Here is the command they all asked for:
```

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX

```

With that info, how do I get the model, and how do I get my speakers to stop playing when headphones are plugged in. Also, I don't have any software installed like pulse audio either, so it's not that.

Thanks so much to whoever can answer this... :)

---

### Post by oscargodson on 2010-08-12
No one knows what the model is and/or how to help?

---

### Post by ngrieb on 2010-09-21
Been having a similar problem: the ALC269 codec seems to be buggy: google it...not sure when or if they are going to fix it but my sound is very sporadic and never does the same thing twice. I just found out about this so I will see what's going on too.

---

