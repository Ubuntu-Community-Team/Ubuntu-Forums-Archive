---
title: "Support for .cbr files"
date: 2010-07-11
forum: General Help
---

### Post by mameshiba on 2010-07-11
Hello,

I've had some documents sent to me with a .cbr extension and I can't open them in ubuntu. Does anyone know what I need to install in order to be able to read them?

When I try to I get the error message "Unable to open document: File type RAR archive (application/x-rar) is not supported".

Thanks

---

### Post by stoneage on 2010-07-11
Try extracting them with unrar

```
sudo apt-get install unrar
```

[http://en.wikipedia.org/wiki/Comic_Book_Archive_file](http://en.wikipedia.org/wiki/Comic_Book_Archive_file)

---

### Post by cj.surrusco on 2010-07-11
.cbr files are the same as .rar files, I believe. So, if you change the extension to .rar, then you may be able to extract it. Also, a program called 'comix' is supposed to be able to read them.

---

### Post by sanityfare on 2010-07-11
Hi

Enter cbr into your Ubuntu Software Center and install the package of your choice. 

SF

---

### Post by mameshiba on 2010-07-11
Thank you! Sorted (^-^)

---

### Post by cascade9 on 2010-07-11
.cbr files are 'comic book reader' files. 

[http://en.wikipedia.org/wiki/Comic_Book_Archive_file](http://en.wikipedia.org/wiki/Comic_Book_Archive_file)

You can open them with rar, but its a lot easier to use comix (GTK) or qcomicbook (Qt). There are probably other cbr viewers around for linux, but those are the ones I remember trying :lolflag: 

BTW, there are variants in the .cbr theme- 

.cbr - rar-compressed 
  .cbz - zip-compressed 
  .cba - ace-compressed 
  .cb7- 7zip-commpressed
.cbg - targzipped 
  .cbb - tarbzip2ped

---

