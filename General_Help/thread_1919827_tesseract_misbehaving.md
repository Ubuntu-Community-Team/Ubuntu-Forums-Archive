---
title: "tesseract misbehaving"
date: 2012-02-03
forum: General Help
---

### Post by Langstracht on 2012-02-03
Initiating a tesseract operation from the command line works fine.  However when I use the same command (i.e. on the same tif file) in a script it abends and gives the following error:

check_legal_image_size:Error:Only 1,2,4,5,6,8 bpp are supported:16
Segmentation fault

Does any one know what's going on and how I can overcome this?

Thanks in advance.

---

### Post by ajgreeny on 2012-02-03
Must be something to do with the colour depth of the .tif file you are using, I think, 
> 1,2,4,5,6,8 bpp are supported:16though I can not think of any good reason why it works in terminal but not in a script.

What version of tesseract are you using?  I have version 3.0.0 from the ppa which you can get with```
sudo add-apt-repository ppa:alex-p/notesalexp
sudo apt-get update
sudo apt-get install tesseract-ocr tesseract-ocr-eng 
```
See [http://wiki.openkm.com/index.php/Third-party_software_integration:_OCR_Tesseract](http://wiki.openkm.com/index.php/Third-party_software_integration:_OCR_Tesseract).
This newer version is much more flexible about the tif image used, and will even handle coloured images, though greyscale are possibly better, and works with jpeg as well as tif and tiff images.

I also find this version much more accurate than the version from Lucid's repos though I don't know what version is in later ubuntu versions.

---

### Post by Langstracht on 2012-02-04
Thanks so much for taking the time to respond.

I was using 2.0.0.  Relying on the security blanket ubuntu sources provide, I had NO idea that there was a later version.  Indeed I understood that no resources had been directed to tesseract in years.

In any event I took your advice and installed 3.0.0 - warning to others who may follow "-r" is not recognized for repository removal any more.

That said I have put it through its paces and, as far as I can tell, it seems to work just fine.

So thank you again for that.

---

### Post by ajgreeny on 2012-02-04
> **Langstracht said:**
> Thanks so much for taking the time to respond.

I was using 2.0.0.  Relying on the security blanket ubuntu sources provide, I had NO idea that there was a later version.  Indeed I understood that no resources had been directed to tesseract in years.

In any event I took your advice and installed 3.0.0 - warning to others who may follow "-r" is not recognized for repository removal any more.

That said I have put it through its paces and, as far as I can tell, it seems to work just fine.

So thank you again for that.
Great!
Have you tried it with a jpeg image yet, or with a coloured image, and if so, how did it work?  Do you also find it more accurate, as I do?

PS:
What exactly do you mean by > warning to others who may follow "-r" is not recognized for repository removal any more.

---

### Post by Langstracht on 2012-02-05
I had not tried it with .jpg but have been prompted to do so by your question.

And the answer is yes it works.  On some .jpgs.  But it does not on some others.  And actually I have found this to be true with .tifs as well.  It works with some ... but not with all.  Which is a bit of pain.

As for accuracy of the conversion I'd have to do some experimentation to find out one way or the other.  As well as to (try to) figure out what gives with the inconsistent ability to process files.  That said I was quite happy with how 2.0.0 worked until the incident which prompted this thread.  Can't say I've noticed that 3.0.0 is demonstrably better.  

Finally as to the "-r", "your" link ([http://wiki.openkm.com/index.php/Third-party_software_integration:_OCR_Tesseract](http://wiki.openkm.com/index.php/Third-party_software_integration:_OCR_Tesseract)) says to disable the "new" repository by use of "-r".  It does NOT work.

---

