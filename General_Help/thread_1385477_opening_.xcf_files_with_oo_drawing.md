---
title: "opening .xcf files with oo drawing"
date: 2010-01-19
forum: General Help
---

### Post by petition on 2010-01-19
Hi folks,

I'm running 9.04 jaunty. I made a file in gimp and saved it as .xcf. I want it to be a pdf file, so I try opening it with open office drawing, but it keeps opening it with the word processor instead. The word processor starts the file if I do a right-click 'open with' on the file on my desktop, and even if I use open from the file menu in drawing itself.

I'm wondering what to do to get drawing to open this file. Is it that .xcf is not supported by drawing?

Thanks for your help. I so appreciate this website and the helpful community it has spawned.

---

### Post by petition on 2010-01-19
The problem is still happening, but I got around it by saving the file as a jpeg in gimp, then drawing would open it.

So yeah, problem solved.

---

### Post by 311005901 on 2010-01-19
> **petition said:**
> 
I'm running 9.04 jaunty. I made a file in gimp and saved it as .xcf. 

Sorry we couldn't help you sooner, but I'm glad you resolved it yourself! :D

For future reference, .xcf is a "GIMP only" format. In most cases, only GIMP will open it up. It's not an image format (like .gif or .jpg), but rather a big fat archive file that tells the GIMP program what changes you've made to the file and all kinds of other crap that OpenOffice can't read.

:popcorn:
I'm really happy that you figured out what you needed to do!

---

### Post by howefield on 2010-01-19
Likewise, happy you're sorted, but for reference.

The convert command can convert around 100 different file types including xcf to pdf. It's part of the imagemagick application.

```
convert file.xcf fle.jpg
```

---

### Post by 311005901 on 2010-01-26
Petition, could you please mark this thread as "SOLVED"?
By using this tag, it's easier for the forum administrators to weed out lost posts. :)

---

