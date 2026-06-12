---
title: "Looking for a mature book collection manager"
date: 2011-01-09
forum: General Help
---

### Post by siddartha on 2011-01-09
I have quite a large virtual library - most of the volmes are in PDF - and I'm just tired of seeking a working app to manage them.

The ideal app would be stable, cross platform (Lin and Win), not in Java or some scripting language (the ease of pissing lines of code spells Alpha software for ever). It should be able to do some search on sites (amazon for example) to fill up the DB based on ISBN and most important: be able to scale. Everything tried so far just bloats with every book added, and that's just poor programming.

Does something like this exist? I'm willing to try even closed source apps.

---

### Post by cascade9 on 2011-01-09
Apart from cross platform, tellico should do what you want- 

[http://tellico-project.org/](http://tellico-project.org/)

---

### Post by siddartha on 2011-01-09
That is true. Tellico was one thing that proved years ago that using GTK when you don't run Gimp daily is just a waste of space. It just works. But it is so tied to KDE and nowadays I'm mostly on Windows.

---

### Post by cascade9 on 2011-01-09
You could always run a linux distro in a virtual machine for tellico with windows.

---

### Post by siddartha on 2011-01-09
WinXP SP3 plus VM plus Linux plus KDE plus Tellico in 1GB on an Atom? But the days when people would feel fine with a 386 equiped with 4MB are long gone.

---

### Post by cascade9 on 2011-01-09
Not super fun, but do-able. 

Tellico doesnt need plasma-desktop, so you dttn need 'full' KDE 4.X. Even if you did, its not as heavy as people say if you get the right setup/distro (currently running KDE 4.4.5 with kwin and it boots to about 200MB used on a 4GB system).  

You could always buy another RAM stick, DDR2/3 is cheap.

---

### Post by parys on 2011-01-10
> **siddartha said:**
> I have quite a large virtual library - most of the volmes are in PDF - and I'm just tired of seeking a working app to manage them.

The ideal app would be stable, cross platform (Lin and Win), not in Java or some scripting language (the ease of pissing lines of code spells Alpha software for ever). It should be able to do some search on sites (amazon for example) to fill up the DB based on ISBN and most important: be able to scale. Everything tried so far just bloats with every book added, and that's just poor programming.Well, I've got a suggestion but it violates one of your constraints. :) Calibre is the best ebook manager out there, IMO. [http://calibre-ebook.com](http://calibre-ebook.com) It's written in Python, I believe, but it is cross-platform (inasmuch as you can get python on windows), it does do metadata lookup, and manages ebooks quite well.

Mendeley would be another option, but it's written in Java. :/

---

### Post by parys on 2011-01-10
> **siddartha said:**
> I have quite a large virtual library - most of the volmes are in PDF - and I'm just tired of seeking a working app to manage them.

The ideal app would be stable, cross platform (Lin and Win), not in Java or some scripting language (the ease of pissing lines of code spells Alpha software for ever). It should be able to do some search on sites (amazon for example) to fill up the DB based on ISBN and most important: be able to scale. Everything tried so far just bloats with every book added, and that's just poor programming.Well, I've got a suggestion but it violates one of your constraints. :) Calibre is the best ebook manager out there, IMO. [http://calibre-ebook.com](http://calibre-ebook.com) It's written in Python, I believe, but it is cross-platform (inasmuch as you can get python on windows), it does do metadata lookup, and manages ebooks quite well.

Mendeley would be another option, but it's written in Java. :/

---

### Post by oldos2er on 2011-01-10
Alexandria (think it's Linux only), or Calibre.

---

### Post by siddartha on 2011-01-12
Calibre comes up on every discussion. Guess they do have some good marketing. Anyway, years ago the idea was to have an app do one thing and do it well. Calibre it's an excellent example of taking things the other way - do anything imaginable and fail as much as possible. For a 50 book library it works like a charm. And if the books are already well structured, tagged and named probably you can raise to 75 files. For 10.000 the list of problems is longer than the list of features. Still, it's a good example why scripting language is excellent for an overnight hack, but unfit for a larger project.

cascade: I can buy 10 DDR sticks but what's the use? Today manufacturers do solider the memory to save on the socket.

Alexandria is a good example why OSS doesn't get anywhere - instead of pushing tellico to go further and faster somebody decided that Gnome can use that functionality too. So here you have it: a second grade software for the sake of "I can code too".

Eh, the bottom line sounds more like Tellico for Linux and Alpha Ebook Manager for Windows.

---

### Post by cnbiz850 on 2011-03-01
To better keep track of my hundreds of books and documents, I have been looking for such a thing for a couple of years.  Tried Calibre and agree with the above post that it is not very good.  Recently I found this thing called Referencer on Ubuntu's repository very good.  It allows you to tag books, jot down notes, and search.  Serves my needs.  Very simple to use.  Books can be imported by directory.

Haven't tried Tellico, hesitate to install all the KDE related files.

---

### Post by cnbiz850 on 2011-10-12
After about a year's experience, I jump back to Calibre from Referencer.  [Here is a write-up about the reasoning.]("http://leojia.blogspot.com/2011/10/managing-ebook-library-on-ubuntu-in.html")

---

### Post by kushdilip on 2012-07-04
IMHO Tellica is far better than  Calibre in terms of simplicity and functionality. 
The thing I hate most about Calibre is that, It copies every file to its own folders which is a pain. While with Tellica you can just import the pdf file and get the metadata and link to file in drive, It doesn't copy the entire file.

---

