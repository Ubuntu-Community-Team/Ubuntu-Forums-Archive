---
title: "Optimized ogg for Ubuntu?"
date: 2006-06-09
forum: General Help
---

### Post by Cable on 2006-06-09
Are there compiles floating around anywhere of the latest version aotuv Lancer optimizations of the ogg vorbis codec?  I loved it in Windows, and would like to obtain it for Ubuntu.

---

### Post by disturbed1 on 2006-06-10
[http://rarewares.org/]("http://rarewares.org/")

```

deb http://www.rarewares.org/debian/packages/unstable/ ./
```

Enjoy :mrgreen:

---

### Post by Cable on 2006-06-10
What's that command for?  If I type it in the terminal it says "deb: command not found."

---

### Post by Cable on 2006-06-10
Ah, nevermind.  It was what to add to sources.list to use synaptic to get the packages.  Thanks!

---

### Post by Cable on 2006-06-10
Hmmm....which package is the lancer compiles?

---

### Post by treris on 2006-06-10
never mind

---

### Post by MakLeod on 2007-05-13
How would I set Sound Juicer up to use the aotuv commands instead of the normal default ones?

---

### Post by MakLeod on 2007-05-23
/bump

---

### Post by Major_Kong on 2007-06-04
> **MakLeod said:**
> How would I set Sound Juicer up to use the aotuv commands instead of the normal default ones?

I'm not sure you can... maybe replacing the libvorbisenc2 for the aotuv version will do the trick.

EDIT: How do i build these packages for amd64 ?

---

### Post by Major_Kong on 2007-06-04
/bump

---

### Post by Major_Kong on 2007-06-05
Anyone ?

---

### Post by MakLeod on 2007-06-12
> **MakLeod said:**
> How would I set Sound Juicer up to use the aotuv commands instead of the normal default ones?

Would love to see an answer to this.  :D

---

### Post by hugmenot on 2007-06-15
1. Someone goes ahead and works the aotuv patch into the feisty libvorbis package and provides those debs.
2. Interested parties install that.
3. All encodes are subsequently done with the aotuv tunings, no extra commands needed;
just "oggenc -q6", e.g.. This can be verfied by looking at the producer string in the vorbiscomments.

---

### Post by MakLeod on 2007-06-15
> **hugmenot said:**
> 1. Someone goes ahead and works the aotuv patch into the feisty libvorbis package and provides those debs.
2. Interested parties install that.
3. All encodes are subsequently done with the aotuv tunings, no extra commands needed;
just "oggenc -q6", e.g.. This can be verfied by looking at the producer string in the vorbiscomments.

Sorry, I'm not at my main computer to check, but are you saying the aotuv patches are already in the official Ubuntu repositories?

---

### Post by hugmenot on 2007-06-15
Isn&#8217;t it enough to read properly?

---

