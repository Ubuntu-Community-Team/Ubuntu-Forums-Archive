---
title: "MP3 Metadata with Regular Expressions"
date: 2010-03-29
forum: General Help
---

### Post by ScarletWyvern on 2010-03-29
Does anyone know how a way that I can edit the metadata tags on some MP3s using regex?

I've got almost 100 MP3, all named "01 - <song title>," "02 - <song title>," etc., and I, understandably, don't want to edit them all by hand.

Running "s/\d{2} - //g" would be so much easier.

Thanks.

---

### Post by ScarletWyvern on 2010-03-29
Bump?

---

### Post by n0dix on 2010-03-29
With a script in bash, perl, or etc. I don't have much knowledge about this programs.

---

### Post by ScarletWyvern on 2010-03-29
That's the problem...

I don't know how to program something like that...

I tried using id3tool to read the tag, use sed to apple the regex, and then use id3tool again to rewrite the tag, but id3tool only supports 30-character tags.

---

### Post by cjhabs on 2010-03-29
> **ScarletWyvern said:**
> That's the problem...

I don't know how to program something like that...

I tried using id3tool to read the tag, use sed to apple the regex, and then use id3tool again to rewrite the tag, but id3tool only supports 30-character tags.

Try lltag - it is in the repos - load it and check out the man page - hopefully it'll do what you want.

---

