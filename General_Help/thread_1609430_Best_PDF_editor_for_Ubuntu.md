---
title: "Best PDF editor for Ubuntu"
date: 2010-10-30
forum: General Help
---

### Post by swaprava on 2010-10-30
I work with PDF files (Portable Document Format) very frequently. I guess many people like me does similar kind of work and when we work with multiple people and want to share the PDF files we need to annotate it. Write on the PDF as one can do in Adobe Acrobat in Windows. I was long in search of a similar application in Ubuntu. To my surprise, I found no similar tools mentioned in the forum posts. All they mention is the same junk pdfEDIT or something of that sort. I was feeling hopeless till my Boss introduced me to xournal. It is wonderful and you can play magic on PDFs with it. The package is in the repo. Just type,

```
sudo apt-get install xournal
```and it's yours. You can scribble, use your pdf as a notebook, mark on it using pen in different inks, highlight, scratch and finally export again as pdf. What more can a researcher expect? I was benefited and hence thought of spreading the message. Explore and enjoy!!

---

### Post by mike555 on 2010-10-30
They even make a version for Windows ....

---

### Post by Legeril on 2010-10-30
sounds like a nice app, will this replace Adobe as my primary .PDF viewer? Is it worth removing Adobe if I install it?

---

### Post by mike555 on 2010-11-03
You probably should keep your default viewer and just use  Xournal when you need it .

---

### Post by ectospasm on 2010-11-11
Xournal is really designed for marking a PDF.  Xournal makes it easy to highlight, or otherwise mark off items on a PDF without having to print it out and do it the old fashioned way.  You can also type notes on it.  That's all I've used it for right now, but it's essentially an image editor or "paint" program that can import and export PDFs.  Pretty neat, IMO.

---

### Post by mosaic2s on 2010-11-24
Thanks for your tips. Used XOURNAL. Found it good. Few limitations though.
Does not allow document to be rotated. - need to use pdf shuffler for that.
also, the mouse buttons have to be assigned every time it is started.

pdf save feature is not very great - may not save page how you want it. esp large ones.

if they can assign hot keys like
p for pencil,
e for eraser,
h for hand,
a for full screen,
z for zoom area etc.
it will speed up the annotation for any user.

Best if they can use GIMP hot keys to lower the learning curve. No need for shift+ctrl+?? for the keys.

---

### Post by layr on 2011-01-03
Would go with **[Mendeley Desktop]("http://www.mendeley.com/download-mendeley-desktop/ubuntu/instructions/").** As good soft as you'd find for Win.

---

### Post by ectospasm on 2011-01-11
> **layr said:**
> Would go with **[Mendeley Desktop]("http://www.mendeley.com/download-mendeley-desktop/ubuntu/instructions/").** As good soft as you'd find for Win.

Mendeley is overkill for this.  It's like using PowerPoint or Impress as a paint program.  Sure, it can do the job, but the specific purpose of Mendeley is well beyond the scope of this user's request.  

I'd never heard of Mendeley, but I think I could use it in my own research.  Again, it's overkill if all you want to do is edit a PDF.

---

### Post by TeoBigusGeekus on 2011-01-11
I had also searched for an application to manipulate bookmarks in pdf files for years. Finally found it a few months ago: [jpdfbookmarks]("http://flavianopetrocchi.blogspot.com/").

---

### Post by jibon_24 on 2011-09-17
Thanks it's working fine for me

---

### Post by rojaasensei on 2011-09-17
Thank you for the recommendation for Xournal.  Your post added a couple of details I had overlooked.

Installed, it's great, and so lightweight!

Thanks again.:p

---

### Post by frncz on 2012-01-25
I use xournal, a very useful program, but I have not found a way to import a graphic into a pdf with xournal, e.g. a signature. Is there a PDF editor that allows me to do that?

Also, placement of new text is a bit imprecise with xournal.

cheers

Mike

---

### Post by rewyllys on 2012-03-09
I can recommend PDF Studio Pro as an excellent PDF editor for Linux. It's not free, but I found the price well worth it to me.

You can take a look at it at:

[http://www.qoppa.com/pdfstudio/index.html](http://www.qoppa.com/pdfstudio/index.html)

---

### Post by collisionystm on 2012-03-09
AWESOME! Thanks!

---

### Post by chrisgianti on 2012-05-06
> **layr said:**
> Would go with **[Mendeley Desktop]("http://www.mendeley.com/download-mendeley-desktop/ubuntu/instructions/").** As good soft as you'd find for Win.

Thank you. This software is the closest thing I can find to a decent version of Foxit for Ubuntu. If only it had a few more pdf editing features.

---

### Post by MSemlali on 2012-07-03
Thanks a lot! It's working fine for me too :)

---

### Post by nkhong on 2012-07-17
Excellent recommendation! Thank you much.  I'm now using xournal to annotate my pdfs.

---

### Post by rodtaylor on 2012-08-05
Highly recommendable!! Xournal works just fine for me! 

I was looking for an application to be able to highlight my pdf file and Xournal works just the way I wanted!

Thanks for the recommendation!!

---

### Post by cedric_tux on 2012-12-10
For me it's PDFStudio form Qoppa

---

### Post by llehman on 2013-02-11
I have a specific question about the pdf editors mentioned. I am an author, and I receive the final blues (as they used to call them) from my publisher as a pdf, and I then have to create the index of it for my books.

Do any of you happen to know if these programs include index creation (not tabs to use within a pdf document), but the creation of a separate index, which would be a separate file?

Thanks a bunch!

---

### Post by vasilbelarus on 2013-02-11
As for me - Okular is the best reader for PDF, DJVU, FB2, EPUB etc.
It also has features to annotate documents in any format and much more.
It really worth trying!

---

### Post by Impavidus on 2013-02-11
> **llehman said:**
> I have a specific question about the pdf editors mentioned. I am an author, and I receive the final blues (as they used to call them) from my publisher as a pdf, and I then have to create the index of it for my books.

Do any of you happen to know if these programs include index creation (not tabs to use within a pdf document), but the creation of a separate index, which would be a separate file?

Thanks a bunch!
Ouch.
Apparently your publisher interprets digitising as replacing paper and ink by a digital description of where to put the ink on the paper (known as PDF, never meant for anything else than printing or on-screen reading), discarding all additional data on the structure of the text. It's better to generate an index as part of the typesetting process, instead of afterwards. In my opinion, the best PDF editor is the one that edits the data before a PDF is generated.

You can use the search function of the PDF readers to find certain keywords in your PDF, but you still have to decide whether every mention of those keywords is worth an entry in the index. In that sense, your job won't be much easier than that of index makers 200 years ago. After you have marked all index entries by hand as annotations in your PDF, you can export those annotations as (keyword; page) pairs, sort them and bundle the pagerefs for each keyword. I think there are programs for that last part, but it's the easy part anyway. Then the index is ready for typesetting. I don't think there are programs that do all of it automatically.

I've never tried to made indices this way, so I don't know the details. I prepare them early on on the process. (And yes, I even use LaTeX to write my Sinterklaas poems.)

---

### Post by llehman on 2013-02-12
Actually, I have a program under Windows called PDF Index Generator, which does the job decently. I haven't tried running it under Crossover, or in VirtualBox, but was wondering if anybody knew of something similar in native Linux.

My publisher is not atypical in the small publisher niche. I'm sure Rowling has never worried about this!

---

### Post by Impavidus on 2013-02-12
I'm quite sure Rowling has somebody to do it for her.

I'm often baffled by the way people use computers, or technology in general. It gives us so many new possibilities, but people tend to replace parts of their processes by new technologies, without rethinking the overall design of the production process of, for example, a book. Therefore they don't use new technologies to their full potential. Of course, publishers and software designers form two largely separate worlds, with the publishers being far more traditional. When I see the slow rate of adoption of e-books compared to how quickly the film industry adopted the DVD... Or compare it to the rate of adoption of new technology by the car industry compared to the airline industry. Although I have to admit I prefer paper books, as they better guarantee my rights as a reader.

Maybe I should say my only writings ever published were a short story in the magazine of my student association (well recieved though) and some articles in scientific journals.

Anyway, to come to the point, I don't know about any native linux program that will do the job. You could try your windows application in wine or CrossOver, or a virtual machine. But still, any attempt to process PDF will be a kind of hack with somewhat unpredictable results.

---

### Post by llehman on 2013-02-20
Thanks for considering the question! I don't disagree with what you are saying, but of course we authors don't control what happens when the manuscript leaves our hands.

---

### Post by knowlittle on 2013-03-27
I tested xournal. What annoyed me was an inability to rotate page. It does not seem to allow vertical writing. Simple but could be a turn off if you don't have the right orientation. Still can not find any better than xournal, however.

---

### Post by kdobkowski on 2013-04-07
Thanks! I was looking for something like that :D

Even more, is there any other application similar to Acrobat Reader Pro? I mean, that edits the text in the PDF file etc.?

---

### Post by mdavis1231 on 2013-04-22
The absolute best PDF software that I've found for Linux is PDF Studio 8  Pro.  It truly is the equivalent of Adobe Acrobat Pro.  It's rich with  features, and I challenge anyone to find a better PDF Viewer/Editor for  Linux.  I have it on my Ubuntu 12.04 LTS desktop, and wouldn't use  anything else!  Take advantage of the free trial and see for yourself!  [http://www.qoppa.com/pdfstudio/](http://www.qoppa.com/pdfstudio/)

---

### Post by kdobkowski on 2013-04-22
> **mdavis1231 said:**
> The absolute best PDF software that I've found for Linux is PDF Studio 8  Pro.  It truly is the equivalent of Adobe Acrobat Pro.  It's rich with  features, and I challenge anyone to find a better PDF Viewer/Editor for  Linux.  I have it on my Ubuntu 12.04 LTS desktop, and wouldn't use  anything else!  Take advantage of the free trial and see for yourself!  [http://www.qoppa.com/pdfstudio/](http://www.qoppa.com/pdfstudio/)

Wow, well this one is just awesome! :o
Thanks buddy! Appreciate your replay! :KS:P

---

