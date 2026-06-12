---
title: "Poor image quality converting from png to pdf"
date: 2009-08-23
forum: General Help
---

### Post by marcusesses on 2009-08-23
Hi, 

I have a png file (created in Inkscape) that I am trying to convert to a pdf file. 

I use the command

```
convert file.png -compress Zip file.pdf
```

which does a nice job of converting the file type and keeping the file to a manageable size. 


However, I am then inserting that pdf file into a LaTeX document, and the quality of the image in the LaTeX document is terrible. When I zoom in to the document the quality gets better, but I don't understand why the quality drops so much. 

Does anyone have any ideas what could cause this?

EDIT: I'm not sure what step the problem arises (Inkscape? convert? LaTeX?), but I thought perhaps someone has some experience with this.

---

### Post by dlmarti on 2009-08-23
I've not tried to embed png->pdf->latex before, but I have had similar issues in the past.

Basically what you want to do, is to keep the DPI the same through out all three applications.  Without doing that your asking for trouble.

---

### Post by marcusesses on 2009-08-23
How do I ensure that I keep the DPI constant?

(I don't even know what DPI stands for. Time for some googling...)

---

### Post by dlmarti on 2009-08-23
> **marcusesses said:**
> How do I ensure that I keep the DPI constant?

(I don't even know what DPI stands for. Time for some googling...)

dpi == dots per inch

If you want the thing to appear as a 2"x2" image in the final document, and you set final document to 300 dpi (fairly standard).  Then the image better start as a 600x600 pixel image and each of the programs you flush it through better maintain that setting.

Some of the programs have a way to set the dpi, and some of them you just have to make sure that the output size is appropriate.

---

### Post by XCan on 2009-08-24
Using rasterized graphics in latex is bound to cause all kinds of headaches. However, in some(many?) cases the printed version looks fine. Also, have you looked at your output using Adobe Reader? In general, it has a much better rendering engine to deal with aliasing.

---

### Post by mcduck on 2009-08-24
Why not convert directly from SVG to PDF? PDF can handle vector graphics and this way you wouldn't need to worry about image quality or resolution at all, instead you'd get pretty much perfect result.. ;)

edit: What comes to your original problem, convert assumes you are creating PDF for display use (72 DPI) unless you specify higher DPI yourself. Use the "-density"-parameter to set the desired DPI..

---

### Post by marcusesses on 2009-08-24
[QUOTE]Also, have you looked at your output using Adobe Reader? In general, it has a much better rendering engine to deal with aliasing.[\QUOTE]
I used Evince to view the document and it looked terrible, unless I zoomed in to about 200%. I'm not sure what differences ther are between Evince and Adobe Reader....

> **mcduck said:**
> Why not convert directly from SVG to PDF? PDF can handle vector graphics and this way you wouldn't need to worry about image quality or resolution at all, instead you'd get pretty much perfect result.. ;)

Do you know how to do this? It is my understanding that one can only convert SVG files to PNG, JPEG or BMP,and to convert directly from SVG to PDF would require a third party program, like svg2pdf.


> **mcduck said:**
> edit: What comes to your original problem, convert assumes you are creating PDF for display use (72 DPI) unless you specify higher DPI yourself. Use the "-density"-parameter to set the desired DPI..

What do you mean by display use? I understand this solution (and I'll give it a whirl), but I don't understand why you would need to manually rescale the display. 

I'm sorry, this is really my first foray into the world of graphics, so I'm a bit lacking in the requisite knowledge.

---

### Post by XCan on 2009-08-24
Yes, the rendering engine is completely different. If you look at a document that does not have the fonts embedded you will see the huge difference between different reader.

As for converting svg to pdf, install inkscape and either open the svg in it and export to pdf or type ```
 inkscape -z --file=original.svg --export-pdf=converted.pdf 
```

Of course, EPS should work great for your purposes as well, but I guess most people perfer pdf nowadays.

---

### Post by mcduck on 2009-08-25
> 
Do you know how to do this? It is my understanding that one can only convert SVG files to PNG, JPEG or BMP,and to convert directly from SVG to PDF would require a third party program, like svg2pdf.
XCan already suegstd how to do that with inkscape, although I'm quite sure Imagemagick would do the trick as well, and I don't see an reason why svg2pdf wouldn't work.

But Inkscape will most likely have best SVG support so I'd use that one. And it actually has the option to save into PDF just like you'd save into SVG.

> 
What do you mean by display use? I understand this solution (and I'll give it a whirl), but I don't understand why you would need to manually rescale the display. 
You don't need to "scale the display". You need to tell the pixel density to be used when converting from vector graphics to bitmap, and the pixel density to be stored in the PDF and at which all the graphics are embedded into the PDF.

For example default DPI for computer displays is usually 72 or 90 DPI. At that resolution A4 size image (21cm x 29,7cm) would be 744 x 1052 pixels. This is fine when the document is viewed on computer display.

For print quality you'd usually go for 300DPI, and at that resolution the same A4 image would be 2480 x 3508 pixels.

So if you use 72DPI setting (default for Imagemagick) all the images in your PDF will be considerably smaller resolution than if you used higher DPI suitable for print use.

---

