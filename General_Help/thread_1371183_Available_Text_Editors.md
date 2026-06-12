---
title: "Available Text Editors"
date: 2010-01-03
forum: General Help
---

### Post by Final Version on 2010-01-03
I want a good text editor, with syntax highlighting. Also, what C++ compilers are available for Ubuntu 9.10.

---

### Post by atjesse on 2010-01-03
Editors: 
The best editor with language notations is Gedit itself. There are varient editors like Geany which can also be used as an IDE.
others:KATE(KDE-default),EMACS,KWriter

C++ compilers: 
Geany, DevCpp
Among, I recommend DevCpp.

Above all you need g++ to compile c++ apps.Run
sudo apt-get install g++

---

### Post by lovinglinux on 2010-01-03
If you don't mind installing some kde dependencies, then I would recommend Kate text editor. It is awesome and way much better than Gedit. You can customize a lot of stuff and it has several nice features, like expanding/collapsing code between tags/brackets, a document browser and a session manager. With the document browser and the session manager feature, I just need to open a saved session to get all documents from a project like the image below. Additionally, you can bookmark lines in the code, highlight the code between brackets and so on.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142260&stc=1&d=1262517912[/IMG]

Kate has made me much more productive and since I use KDE, I also get a kate session launcher in the panel :)

Compilation of C++ is done with g++ as already stated. To install it, just run this:

```
sudo apt-get install build-essential
```

Then all you need is an IDE like Geany, Code::Blocks or others. See the stickies from the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum. It has lots of info on available editors and IDEs. BTW, programming questions would be better placed there.

I also recommend installing esvn or kdesvn to control subversion.

---

### Post by kellemes on 2010-01-03
geany and vim

---

