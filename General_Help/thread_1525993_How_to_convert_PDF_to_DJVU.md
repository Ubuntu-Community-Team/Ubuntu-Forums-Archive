---
title: "How to convert PDF to DJVU?"
date: 2010-07-07
forum: General Help
---

### Post by vickoxy on 2010-07-07
Hi,
i have one big pdf file that i made from 272 Photos. Heard that djvu format is better at compression than pdf. But have no clue how to use it. I have in synaptic installed pdf2djvu package, and it is in /usr/bin, but have no idea how to use it.

Any idea?

Using 10.04 64bit

---

### Post by cariboo on 2010-07-07
pdf2djvu is a command line program, you have to use it in a terminal.

If you type pdf2djvu in a terminal it will give you all the options, and how to use it.

---

### Post by vickoxy on 2010-07-07
> **cariboo907 said:**
> pdf2djvu is a command line program, you have to use it in a terminal.

If you type pdf2djvu in a terminal it will give you all the options, and how to use it.

Thanks

Just running ```
pdf2djvu old.pdf -o new.djvu
```

Waiting to see result. Does anyone here knows if there is some gui app as for windows?

---

### Post by vickoxy on 2010-07-07
Unfortunately, the output file is over 300mb, and input was 108mb. Any idea what should i put there in terminal?

Thanks

---

### Post by luigi_mb on 2010-07-07
> **vickoxy said:**
> Unfortunately, the output file is over 300mb, and input was 108mb. Any idea what should i put there in terminal?

Thanks

```

man pdf2djvu

```

/luigi

---

### Post by vangop on 2010-07-10
Hi!
DJVU offers a better compression for images (greyscale espec), excellent result with ocr.
I have great doubts that PDF 2 DJVU will ever work. 
If it is not done on windows, forget about it on linux.
You should use images as input. PDF is compressing the images, DJVU needs images, so PDF is decompressed and then the images are compressed again. You lose quality due to conversions.
You can try to use ocr for your pdf [ocr your pdf]("http://ubuntuforums.org/showthread.php?t=1456756")
Let me know if that works.

---

### Post by AlexDudko on 2010-07-11
If resolution is not specified it defaults to 300 dpi. You can specify desired resolution with option **--dpi=_resolution_**.
For instance:
> pdf2djvu --dpi=200 input.pdf -o output.djvu
or simply:
> pdf2djvu -d 200 input.pdf -o output.djvu

---

