---
title: "Somewhat complicated cat request"
date: 2012-07-27
forum: General Help
---

### Post by wheel_walker on 2012-07-27
I have another cat request. 

I have the following files:
000_file0.bin : This is the sprite sheet
000_file1.bin : This is the palette, 15bpp BGR (555) LE
000_file3.bin : This is the big sprite

I need a bash script that will concatenate the files above, in the following order:
000_file1.bin +000_file0.bin + 000_file3.bin

And which will then do that for the 001* set, the 002* set, and so on until it finishes with the 255* set; as I have 256 of each of the above 3 files, from 000_file*.bin to 255_file*.bin.

I imagine this will require a for loop, but since I'm not really a programmer, I don't really know what to do next.

---

### Post by steeldriver on 2012-07-27
something like this maybe?

```
for i in $(seq -w 1 255); do cat "$i"_file1.bin "$i"_file0.bin "$i"_file3.bin > "$i"_file.bin; done
```

---

### Post by wheel_walker on 2012-07-27
It worked, but I had to change it since you forgot to go from 0 to 255, not 1 to 255.  

```
for i in $(seq -w 0 255); do cat "$i"_file1.bin "$i"_file0.bin "$i"_file3.bin > "$i"_file.bin; done
```

This will come in handy in the future.  Thanks!

---

### Post by Vaphell on 2012-07-27
native bash solution without external commands (seq)
```
for i in {000..255}; do ...; done
```

---

### Post by steeldriver on 2012-07-27
^^^ doh! you know, I never even thought to try giving the builtin {N...M} sequence an explicit field width like that

---

### Post by sisco311 on 2012-07-27
> **steeldriver said:**
> ^^^ doh! you know, I never even thought to try giving the builtin {N...M} sequence an explicit field width like that

Yep, BASH 4 allows zero padded number expansion.

seq is part of GNU/coreutils, but is not standard.

There are more options mentioned in BashFAQ 018 (link in my sig).

---

