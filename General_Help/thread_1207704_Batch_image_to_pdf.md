---
title: "Batch image to pdf"
date: 2009-07-08
forum: General Help
---

### Post by kehon on 2009-07-08
is there a program that can take a set of images/already scanned images jpeg mainly and make a pdf from them

---

### Post by kaibob on 2009-07-08
> **kehon said:**
> is there a program that can take a set of images/already scanned images jpeg mainly and make a pdf from them
Are you looking for something with a GUI or command line. If the latter, first copy all of the image files into an empty directory. Then, open a terminal window, change to the directory that contains the files, and enter:

```
convert *.jpg output.pdf
```

If you want to input images with differing formats, you will need to change *.jpg to whatever is appropriate. You can use * if you like.

The convert utility is a part of the Imagemagick suite, which may not be installed by default. If not, it's in the repo's.

---

### Post by kehon on 2009-07-08
um can you explain this :
i used that conver *.jpg output.pdf and the pdf its 187 mb while all of the jpg files put together is only 22 mb why such a big difference

---

### Post by Chronon on 2009-07-08
I saw a discussion of this problem on the IM forum: [http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=11951](http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=11951)

It looks like maybe there's a regression in the version in the Ubuntu repositories that has since been fixed.  Maybe you can find a trustworthy PPA to install from, unfortunately I don't have one to suggest.

---

### Post by kehon on 2009-07-08
cool thanks that worked

---

### Post by Chronon on 2009-07-08
I haven't tried this myself, so I'm not sure which bit worked.  Did simply using "-compress jpeg" work for you or did you install a newer version of imagemagick?  If the latter, would you like to share the source you used?

---

### Post by kehon on 2009-07-08
that worked

---

### Post by kaibob on 2009-07-08
> **kehon said:**
> um can you explain this :
i used that conver *.jpg output.pdf and the pdf its 187 mb while all of the jpg files put together is only 22 mb why such a big difference

I had that problem when I upgraded to Jaunty. That's one of the reasons I went back to Hardy. I'm glad this issue has been noticed and, apparently, fixed.

I just ran a test and converted some JPG images to a PDF using the command line in my earlier post. The JPG images totaled 20 MB and the PDF contained 17 MB. You can, of course, further reduce the size of the PDF with convert command-line options.

Anyways, it sounds like you have this all sorted out.

---

### Post by kehon on 2009-07-08
how did you get it smaller than the size of the jpeg

---

### Post by kaibob on 2009-07-08
> **kehon said:**
> how did you get it smaller than the size of the jpeg
I didn't do anything special. I copied 8 JPG files into my ~/temp directory. Nautilus indicated that the total size of all images was 20 MB. I then ran the following command:

```
convert *.JPG output.pdf
```

I checked and output.pdf contained 17 MB. I opened output.pdf, and it contained all the images. 

I just ran some additional tests, and the PDF was about 5 percent larger than the input images. I don't know why the PDF is smaller is some cases and larger in others. As long as the PDF is not substantially larger, I wouldn't be concerned.

---

