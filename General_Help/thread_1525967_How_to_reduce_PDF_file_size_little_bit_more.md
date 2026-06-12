---
title: "How to reduce PDF file size little bit more?"
date: 2010-07-07
forum: General Help
---

### Post by vickoxy on 2010-07-07
Hi,
i made 272 Photos from one book. Total size was 920MB. I used than gscan2pdf to create pdf document, and reduced there quality size. Result 116 MB. Than i converted it to grayscale ([http://handyfloss.net/2008.09/making-a-pdf-grayscale-with-ghostscript/](http://handyfloss.net/2008.09/making-a-pdf-grayscale-with-ghostscript/)) with: ```
gs -sOutputFile=grayscale.pdf -sDEVICE=pdfwrite \
-sColorConversionStrategy=Gray -dProcessColorModel=/DeviceGray \
-dCompatibilityLevel=1.4 -dNOPAUSE -dBATCH color.pdf
```

Result: 108MB

Is it anyway possible to reduce size more? Something like google does with their books?

Thanks

---

### Post by vangop on 2010-07-07
Hi!
My wife makes tons of book photos, when the drives where getting low on space I started converting them to DJVU. This is much more suitable format for ebooks made out of scans/photos. I made books ~3mb out of 200Mb or something, the ratio is really amazing. 
I used windows app called document express for that. Sorry can't advice on any linux apps.

---

### Post by vickoxy on 2010-07-07
> **vangop said:**
> Hi!
My wife makes tons of book photos, when the drives where getting low on space I started converting them to DJVU. This is much more suitable format for ebooks made out of scans/photos. I made books ~3mb out of 200Mb or something, the ratio is really amazing. 
I used windows app called document express for that. Sorry can't advice on any linux apps.

If that is freeware, could you post me some links where to find this converter? And does it convert from PDF?

Thanks

---

### Post by vangop on 2010-07-07
No, unfortunately this is a commercial app from lizardtech. 
If you want to try DJVU I suggest you start  with [http://djvu.sourceforge.net/]("http://djvu.sourceforge.net/") (I use its viewer on Win and it's very good). PDF is simply not suitable for scans (if anything at all), poor compression.
But I guess DJVU is more work, especially on linux with free tools. I have no experience with this on linux, not sure if it djvulibre will do OCR out of the box or you'll have to do it manually.

---

### Post by AlexDudko on 2010-07-11
There is a terminal application in Ubuntu repositories, which converts pdf to djvu - **pdf2djvu**.

---

### Post by kaibob on 2010-07-11
You can try the following command--which uses the predefined ghostscript dPDFSETTINGS setting--on a test file (before conversion to grayscale). Since you have already reduced file size, I suspect this command will not further reduce file size and may even increase it a bit. But, it's easy to give it a try.

```
gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -dPDFSETTINGS=/screen -sOutputFile=output.pdf input.pdf
```

---

