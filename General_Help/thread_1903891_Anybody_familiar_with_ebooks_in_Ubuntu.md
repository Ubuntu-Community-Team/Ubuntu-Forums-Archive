---
title: "Anybody familiar with ebooks in Ubuntu?"
date: 2012-01-03
forum: General Help
---

### Post by cptrohn on 2012-01-03
I was just wondering because I am interested in getting some ebooks from my public library, but their website says that to view them that you have to have Adobe Digital Editions installed on your PC.

So does anyone use something from open source that is compatible with the ebook formats in Linux?  I know that Adobe Digital Editions doesn't have a linux version of the software....  There is an android version available and I plan on using my gtablet to download some, but there are also some books for school that I would like to be able to download to my laptop to be able to use for reference at school as well.

Any ideas from the OS community?

Thanks!

---

### Post by cptrohn on 2012-01-03
I guess what doesn't make any sense to me at all is that there is a version of digital editions available for Android but nobody has ported that to other linux based distros?

---

### Post by mcduck on 2012-01-03
> **cptrohn said:**
> I guess what doesn't make any sense to me at all is that there is a version of digital editions available for Android but nobody has ported that to other linux based distros?

Probably because there being one for Android doesn't mean it would be open source. Most likely it isn't (since the very reason for it's existence is DRM), so the only ones able to port it to Linux would be the ones who originally made it.

Anyway, as sad as it is I can't help you with the ebooks from your library. I pretty much stick to ebooks using the free and open .epub format...

(I would assume that there's some tool available to convert the books to another format, but that's most likely something that can't be discussed on these forums...)

---

### Post by frncz on 2012-01-03
I am not sure what your requirements are, but I use [www.gutenberg.org/](www.gutenberg.org/) to download e-books to our family's kindles in the .mobi format, using Ubuntu. It works fine, at no cost and huge selection of books, admittedly only for books that are out of copyright.
Mike

---

### Post by xc3RnbFO8P on 2012-01-03
> I was just wondering because I am interested in getting some ebooks from my public library
Can you not play them online direct from the library website?, my library have that option, I just have to login.

---

### Post by 73ckn797 on 2012-01-03
There is "calibre" and "fbreader" which are in the repositories and Firefox has an addon, Epub Reader, that will read some formats. I use several epub formats which open in a Firefox tab.

---

### Post by cptrohn on 2012-01-03
> **Ringi said:**
> Can you not play them online direct from the library website?, my library have that option, I just have to login.

Unfortunately no,  you HAVE to have the Adobe Digital editions installed to get them.

Looks like I will be installing virtual box and XP in the near future...

---

### Post by cptrohn on 2012-01-03
> **frncz said:**
> I am not sure what your requirements are, but I use [www.gutenberg.org/](www.gutenberg.org/) to download e-books to our family's kindles in the .mobi format, using Ubuntu. It works fine, at no cost and huge selection of books, admittedly only for books that are out of copyright.
Mike

No, it won't work for what I am wanting to use it for....  Really sucks..  Oh well.

---

### Post by mungatsuma on 2012-01-03
> **cptrohn said:**
> I was just wondering because I am interested in getting some ebooks from my public library, but their website says that to view them that you have to have Adobe Digital Editions installed on your PC.

So does anyone use something from open source that is compatible with the ebook formats in Linux?  I know that Adobe Digital Editions doesn't have a linux version of the software....  There is an android version available and I plan on using my gtablet to download some, but there are also some books for school that I would like to be able to download to my laptop to be able to use for reference at school as well.

Any ideas from the OS community?

Thanks!

Sorry to intrude, but it might help if you give the file format or extension. Adobe Digital Editions support PDF/A and .EPUB (XHTML) from wikipedia. In linux try Calibre (Installation instructions from here [http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux) ) and FBReader (Instalation instructions here [http://www.fbreader.org/content/linux#debian](http://www.fbreader.org/content/linux#debian)).
 Between the two of them you will be able to read most Ebook formats. Hope that helps and pardon me this is my first post.

---

### Post by 73ckn797 on 2012-01-03
> **mungatsuma said:**
> In linux try Calibre (Installation instructions from here [http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux) ) and FBReader (Instalation instructions here [http://www.fbreader.org/content/linux#debian](http://www.fbreader.org/content/linux#debian)).
 Between the two of them you will be able to read most Ebook formats.  Is there an advantage to using these sources versus both being in the repositories? Besides possibly getting the latest version?

---

### Post by Toz on 2012-01-03
Adobe Digital Versions seems to have a good rating with wine ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545")).

---

### Post by oldos2er on 2012-01-03
> **73ckn797 said:**
> Is there an advantage to using these sources versus both being in the repositories? Besides possibly getting the latest version?

Calibre is updated fairly frequently with both bug fixes and new features.

---

### Post by 73ckn797 on 2012-01-04
> **oldos2er said:**
> Calibre is updated fairly frequently with both bug fixes and new features.
Are those fixes reflected in the repo's version?
I tried fbreader on 2 machines but the page forward button was grayed out and non-functional. Once I found the Firefox add-on I have been using that. I do not read a lot of digital books so my needs are not too much.

---

### Post by Dennis N on 2012-01-04
In addition to the other ideas, you can read Kindle books on a Linux machine in the Chromium or Chrome Browser by installing the free Kindle Cloud Reader from Amazon. Of course, that is not open source, but it works well, and many items are free of charge.

---

### Post by HermanAB on 2012-01-04
So far, I have not encountered an ebook that required installing any special software.  In general, I just click it in Nautilus and something will open it and then I try to do a Save As or print to PDF and then after that there are no more problems, DRM or locks to mess with...

---

### Post by oldos2er on 2012-01-04
> **73ckn797 said:**
> Are those fixes reflected in the repo's version?

As far as I know, no.

---

### Post by fragos on 2012-01-04
Chrome also has a Google ebooks extension available that I use for ebooks purchased from Google.

---

### Post by cptrohn on 2012-01-06
Thanks all for all of the great replies!

Ok I was FINALLY able to research a little more from the libraries website on this situation  I guess they use a system called Overdrive for their ebooks and the format that is used is Adobe epub?   I am just a babe in the woods on the whole ebook thing, and while kindle and google books would be great if I wanted to purchase them...  I just want to be able to read them for free from the public library instead... (I just LOVE me some free lol)

---

### Post by cptrohn on 2012-01-06
> **HermanAB said:**
> So far, I have not encountered an ebook that required installing any special software.  In general, I just click it in Nautilus and something will open it and then I try to do a Save As or print to PDF and then after that there are no more problems, DRM or locks to mess with...

OK because up to know most of my experience with ebooks has been with media that came with my textbooks for school and they all had a CD included that just let me open it as a .pdf  SO all the readers out there are a little overwhelming to me I guess right now.

---

### Post by JKyleOKC on 2012-01-06
The Overdrive servers that many public libraries use do require the Adobe package to even get the book to your machine, so all of the replies that advise using a converter from the epub format are, unfortunately, useless in your case. I ran into the same problem myself in trying to check out books from my local library for my Nook. It's necessary to first bring them into the Adobe program, then copy them over to the Nook or other reader device.

Ebooks that you download from Project Gutenberg or from the many other web sites can be loaded, and read. The epub file format is essentially a wrapper over the popular pkzip format, and can be read directly via file-roller (the archive reader that's the Ubuntu default) if you don't mind having to switch things around every few pages.

The Adobe program, which most libraries supply free for the download, works just fine in a Windows virtual machine. That's how I solved my problem.

---

### Post by cptrohn on 2012-01-06
> **JKyleOKC said:**
> The Overdrive servers that many public libraries use do require the Adobe package to even get the book to your machine, so all of the replies that advise using a converter from the epub format are, unfortunately, useless in your case. I ran into the same problem myself in trying to check out books from my local library for my Nook. It's necessary to first bring them into the Adobe program, then copy them over to the Nook or other reader device.

Ebooks that you download from Project Gutenberg or from the many other web sites can be loaded, and read. The epub file format is essentially a wrapper over the popular pkzip format, and can be read directly via file-roller (the archive reader that's the Ubuntu default) if you don't mind having to switch things around every few pages.

The Adobe program, which most libraries supply free for the download, works just fine in a Windows virtual machine. That's how I solved my problem.

OK, thanks jKyleOKC.....  I am going to see if I can get in touch with the libraries IT guy sometime this week and see what we could possibly work with on it...   Maybe the Kindle route is the way to go,  I just talked with a friend and she says she can download them to her kindle without using the ADE software so maybe I am just getting bad information from the website and the staff there...Guess I just have to look into it more to see what I can do... And thanks to everybody for all the different options they posted, I will test them out and see what works best for me in this deal.. Lol...

---

### Post by nizamibilal1064 on 2012-04-28
> **cptrohn said:**
> I was just wondering because I am interested in getting some ebooks from my public library, but their website says that to view them that you have to have Adobe Digital Editions installed on your PC.

So does anyone use something from open source that is compatible with the ebook formats in Linux?  I know that Adobe Digital Editions doesn't have a linux version of the software....  There is an android version available and I plan on using my gtablet to download some, but there are also some books for school that I would like to be able to download to my laptop to be able to use for reference at school as well.

Any ideas from the OS community?

Thanks!
Hi
I found FBreader a good option as it is free and compatible with linux based systems. You can download and install  FBreader from Ubuntu Software System or visit [http://www.fbreader.org/](http://www.fbreader.org/). After installation , open the FBreader and click on the Show Preference Dialogue icon. Its is a green colour Wheel in my case. Just change the Book path to Your desired path or You can keep it default. It support several open book format (You can read Ubuntu full circle magazine also). Download your eBook in any supported format and copy it to the location given in Book path. Click on the Show library tree icon , you can now see the list of books. Go back and Go forward icon are not for browsing through the book , rather they are for going to your last location.   Enjoy Reading....

---

### Post by WinfriedG on 2012-05-22
If you need to use Adobe Digital Editions install it under wine it works without any problems on my Lubuntu 11.10 powered Acer Aspire One netbook. 
I hate DRM coded e-books therefore I normally use ebook onlin shops which sell epub books without DRM, which are since the mid-2011 year available at least at German shops (buecher.de, ciando.de or beam.de)
Another option is to remove the DRM and read it with FB reader. But unfortunately that is illegal, some people say.  So you better don't do it.:mad:

---

### Post by Rodney9 on 2012-05-22
[http://www.gutenberg.org/](http://www.gutenberg.org/)
[https://www.smashwords.com/](https://www.smashwords.com/)
[http://www.obooko.com/](http://www.obooko.com/)
[http://manybooks.net/](http://manybooks.net/)

These are my favourite free ebook sites, I read them on my Sony ereader

Rodney

---

### Post by traditionalist on 2012-05-24
> **73ckn797 said:**
> Are those fixes reflected in the repo's version?
I tried fbreader on 2 machines but the page forward button was grayed out and non-functional. Once I found the Firefox add-on I have been using that. I do not read a lot of digital books so my needs are not too much.

No, for the latest version of calibre;

[http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux)

QUOTE 
**Download for linux**

              The latest release of calibre is 0.8.52.          [What's new]("http://calibre-ebook.com/whats-new").     
              Please do not use your distribution provided calibre package,         as those are often buggy/outdated. Instead use the Binary install described below.     
      [B]UNQUOTE
[/B]

---

