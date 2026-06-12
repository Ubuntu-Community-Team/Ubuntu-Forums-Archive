---
title: "How do I make Imagemagick convert things one at a time?"
date: 2010-03-18
forum: General Help
---

### Post by s3a on 2010-03-18
How do I make imagemagick convert things one at a time? I know how to make imaggemagick convert all pages of a pdf into individual jpeg files by storing it all in the RAM at once but if there isn't enough RAM, this will use swap like crazy and be suuuuuuuper slow.

Here is the command  for the "crazy swap-using" way:
convert --units PixelsPerInch -density 150x150 filename.pdf filename.jpg

If someone could give me the terminal command so that it converts 1 page at a time (or a user defined amount at a time), then I would REALLY appreciate it!

Thanks in advance!

---

### Post by Trumpen on 2010-03-18
You can split the pdf document into pages with pdftk and then convert each page to a jpeg image.

Hopefully, pdftk will need less memory than convert. Here is some code :

```
pdftk filename.pdf burst

for page in pg_*.pdf; do
    convert --units PixelsPerInch -density 150x150 $page ${page%.*}.jpg;
done
```

---

### Post by kaibob on 2010-03-18
The suggestion by Trumpen is a good one and is the way to go. If, for some reason it doesn't work, you may want to give graphicsmagick a try, as it seems to do a much better job of handling memory issues. Graphicsmagick is in the repo's and is a small install. The commands are pretty much the same as Imagemagick except they contain a gm:

```
gm convert --units PixelsPerInch -density 150x150 filename.pdf filename.jpg
```

As a last resort, if nothing else works, you may want to give ghostscript a try. It does not have density or other settings, although this could be done later. You have to change "file.pdf" to the filename of the target file. 

```
gs -sDEVICE=jpeg -dNOPAUSE -dQUIET -dBATCH -sOutputFile=page-%d.jpg "file.pdf"
```

---

### Post by s3a on 2010-03-19
Thanks! I'll test it out later because I'm busy with school at the moment but ya, thanks again! :)

---

