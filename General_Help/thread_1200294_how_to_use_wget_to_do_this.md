---
title: "how to use wget to do this?"
date: 2009-06-29
forum: General Help
---

### Post by MountainX on 2009-06-29
[http://googlesystem.blogspot.com/2009/02/download-books-from-google-book-search.html](http://googlesystem.blogspot.com/2009/02/download-books-from-google-book-search.html)

Can someone help me put together the wget comand to download all the image files of a book on Google Books?

I'm guessing I need -rk and -O, right?

---

### Post by t4thfavor on 2009-06-29
point me at a working link for a book, and I will see what I can do.

Also I'm looking at the .net source maybe if we find the algorithm we can duplicate it.

I would assume that if it was possible with wget they would just use that in windows as well. We shall see.

I think they are blocking wget, I can't get it to download even one page.

---

### Post by MountainX on 2009-06-29
> **t4thfavor said:**
> point me at a working link for a book, and I will see what I can do.

Thank you!

[http://books.google.co.uk/books?id=UaIuXnKzCrUC&printsec=frontcover&source=gbs_v2_summary_r&cad=0](http://books.google.co.uk/books?id=UaIuXnKzCrUC&printsec=frontcover&source=gbs_v2_summary_r&cad=0)

> **t4thfavor said:**
> 
Also I'm looking at the .net source maybe if we find the algorithm we can duplicate it.


Cool. That would be awesome.

---

### Post by t4thfavor on 2009-06-29
The .net is uncommented to the maxxx, and I am currently on a netbook running linux. Its pretty complex as well. I will have to look at it when I get back on my workstation.

I also think they bocked out wget as it says 
401 Unauthorized
Authorization failed.
When you try to download a valid url with wget.

However this is something the Linux community could bennefit from if we were to tackle it.

---

### Post by t4thfavor on 2009-06-29
[http://gbe.saturnpolly.net/](http://gbe.saturnpolly.net/)

worked for me, you just put in the page range, and select the methd you would like to download the images.

good luck.

EDIT:
Seems they catch on after a bit, and stop you from downloading stuff for a bit. It appears a more complex setup is in order

lolzors

    We're sorry...

    ... but your query looks similar to automated requests from a computer virus or spyware application. To protect our users, we can't process your request right now.

    We'll restore your access as quickly as possible, so try again soon. In the meantime, if you suspect that your computer or network has been infected, you might want to run a virus checker or spyware remover to make sure that your systems are free of viruses and other spurious software.

    If you're continually receiving this error, you may be able to resolve the problem by deleting your Google cookie and revisiting Google. For browser-specific instructions, please consult your browser's online support center.

    If your entire network is affected, more information is available in the Google Web Search Help Center.

    We apologize for the inconvenience, and hope we'll see you again on Google.

---

