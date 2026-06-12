---
title: "OCR programs? I cannot get useful results"
date: 2009-10-11
forum: General Help
---

### Post by mringer on 2009-10-11
I have a paper document that I want to scan & turn into a plain text file. This in good clear typescript, black on white. I scanned it with a HP all-in-one and xsane. I dont know what settings for xsane are suitable for subsequent OCR. The document for xsane is completely unhelpful, it lists several options with no indication which settings might be useful. With settings that I thought reasonable, xsane gave me a very clear image of the typescript.

I tried tesseract, which some people on this forum recommend as the best OCR program available. Again, ROTTEN documents. The man page does not even mention the fact (repeatedly aired in this forum), that you must first convert the image to uncompressed .tif format. (not .tiff, I have no idea what the extra  f  means). The resulting text was recognisable, but it had so many mistakes that it would probably take longer to correct these than to retype the whole document from scratch.

I tried gocr and ocrad, which were far worse. If there were any correct letters I did not see them.

Please does anybody know of a better OCR program? Or are there settings that I should be using on Xsane?

---

### Post by DenysT on 2009-10-11
Depending on which OCR uses I have had the best results scanning at 150-200 dpi. I usually scan with black and white settings but for certain documents I find scanning with grayscale settings and then converting to black and white before saving to TIF. (I use PSP in Windows and I don't even know if GIMP has this as I'm just beginning to use GIMP).

If the OCR program has access to the scanner use it instead of saving to a TIF file, sometimes this can give better results.

---

### Post by StuartN on 2009-10-12
> **mringer said:**
> Or are there settings that I should be using on Xsane?

I am still scanning photographs and images, but will have to do my paper records some time, so I gave this a try.

I set the image type to tiff. A resolution of 300 dpi seems to be the bare minimum with the high quality printed documents I tested. Going to 600 dpi was much, much slower and slightly more accurate.

Scanning to black-and-white worked, although it was essential to despeckle in the viewer before calling gocr. Scanning to grey and letting gocr set its own cut-point was far better (and easier).

Choosing the appropriate rectangle on the preview, with the page straight and no creases is vital. 

(This is nothing like Apple scan, Omniscan, or even Abbyy finereader).

But yes, a 300 dpi greyscale tiff and gocr can give a near 100% accurate recognition.

---

