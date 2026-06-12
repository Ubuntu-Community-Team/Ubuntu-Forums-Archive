---
title: "Anywhere to get get barcode 39 font?"
date: 2010-02-08
forum: General Help
---

### Post by sgwebb on 2010-02-08
I need to find barcode39 font for Unbuntu 9.10, I had this on my Windows xp, does anyone know where to get it ?

---

### Post by sgwebb on 2010-02-08
Nevermind.. I was searching for it specifically for Ubuntu.. but then realized I probably only needed to copy the font into a directory and I was correct.. for anyone else that wants to know ..

Get the font here
[http://www.idautomation.com/fonts/free/#Download_Free_Barcode_Font](http://www.idautomation.com/fonts/free/#Download_Free_Barcode_Font)

Download to directory

Extract it 

Copy the .ttf file to your /usr/share/fonts as root user

the font should then work, I was able to use it abiword right after.

---

### Post by pabloab777 on 2012-09-10
Keep in mind that you could easily generate barcodes PDFs with "barcode" package. If you have a TXT with barcode strings (with Unix line endings), for example, for Code 39 on a Letter page, table of 4 columns, 11 rows, no margins:
```
cat barcodes.txt | barcode -e code39 -o barcodes.pdf -u mm -t "4x11+0+0" -p Letter
```

---

### Post by joshnoth on 2013-03-05
well, I know some websites have free [[COLOR=#000000]Code 39[/COLOR]]("http://www.barcodelib.com/net_barcode/barcode_symbologies/code39.html") barcode fonts, like barcodesinc, but I am not sure whether it works for Unbuntu 9.10.

---

### Post by oldos2er on 2013-03-05
Old thread closed.

---

