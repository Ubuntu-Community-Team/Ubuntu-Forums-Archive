---
title: "Replacing Google Thumbnails on PDF Documents."
date: 2011-11-09
forum: General Help
---

### Post by Infinite Indefinite on 2011-11-09
A number of the books that may be downloaded from [archive.org]("http://www.archive.org") have been scanned by Google.  Unfortunately, these tend to have a Google declaration on their first page - and since pdf thumbnailers normally use the first page in order to create the thumbnail, this results in all these files basically having the same, rather uninformative, thumbnail.

What's worse, is that the Google declaration page is sometimes a different size from the rest of the document.  

Anyway, to cut a long story short, one can use Imagemagick to obtain a satisfactory thumbnail.

First install the program if necessary:

```
sudo apt-get install imagemagick
``` 

Then go to terminal (Applications > Accessories > Terminal), go to the directory with the pdf file and apply the following: 

```
convert -crop '60%x70' -gravity SouthWest -geometry x192 *fileone.pdf*[9] ~/Desktop/*thumbnail.png*
```

with *fileone.pdf* being replaced by the name of the file, and the number in the square brackets (9 in this case), being replaced by the number of the page (*minus one*) desired as the thumbnail: 

A few notes on the code:

The -crop value ('60%x70') determines how much of the image is cropped from the x axis (60% in this case) and the y axis (70% in this case).  Change this value until you get the result desired.

The -gravity value determines which part the image is retained from - i.e. cropping removes from the opposite direction.

The size option for geometry (x192 in this case) should also be modified if necessary until you get the result desired.


Once the thumbnail is created, it can be used to replace the existing Google thumbnails, by renaming them according to the Google thumbnail that needs to be replaced and then placing them in the thumbnails folder.  To prevent them being overwritten, change the permissions to read and execute only.

*This might seem like a rather minor matter, but those Google thumbnails can be annoying.*

---

