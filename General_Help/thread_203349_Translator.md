---
title: "Translator"
date: 2006-06-25
forum: General Help
---

### Post by DoTry on 2006-06-25
Hello :)

Well, I'm considering to install Ubuntu on my PC - However, there is one little thing I'd like to know before I start in the process.

Is there a Translator in linux (hold on) that could import Babylon's dictionaries?
I use Babylon a lot, it is a necessarity!
English is not my mother-tounge and the translators out there don't support my language - even if does, they do not contain the length of words\expressions etc Babylon does.

So, is there such a software that could import Babylon's files (that hold the expressions, etc..), or better yet - is there such a way to make Babylon work on Ubuntu? (without this crazy and complicated Wine)?

---

### Post by mips on 2006-06-25
I had a look in the ubuntu repositories and found **babytrans**.

Here is a description of the package:

> Front-end to use the dictionaries from Babylon Translator
BabyTrans is a graphical interface for the Babylon Translator dictionaries (available under Windows).

Does that help ?

---

### Post by DoTry on 2006-06-25
Well, I checked too - apparently Babytrans only supports .dic files, which are formats formally used by Babylon. Nowadays, Babylon is based on .blg. 
Babytrans's project is discontinued, so that option is ruled out.

I also found wordtrans - but that program too doesn't support blg files..!

So, besides Babytrans (and wordtrans), isn't there a NEW software that is the replacement of Babylon in Linux?
GBL is used for years now, any respectable on-going software should support it. It is weird..

---

### Post by DoTry on 2006-06-25
Oh, just found out something:

Does Ubuntu support kabylon?

---

### Post by gingermark on 2006-06-25
[QUOTE=DoTry]Does Ubuntu support kabylon?[/QUOTE]

Short answer - yes.
Longer answer - There doesn't appear to be a package for it in the repositories at the moment (although one may exist somewhere), so it looks as though you'll have to compile it yourself from the source code.

---

### Post by mips on 2006-06-25
Nothing in the repos and no .deb files on the net. Found this [ftp://ftp.berlios.de/pub/fakt/kabylon](ftp://ftp.berlios.de/pub/fakt/kabylon)

---

### Post by DoTry on 2006-06-25
[QUOTE=gingermark]Short answer - yes.
Longer answer - There doesn't appear to be a package for it in the repositories at the moment (although one may exist somewhere), so it looks as though you'll have to compile it yourself from the source code.[/QUOTE]

Well, I hope there won't be any problems also with the libraries.

Anyways, thank you.

---

### Post by mips on 2006-06-25
I think future versions of wordtrans will support .blg files. Another one to look out for is QTrans in future.

Can't you use .dict files for now ?

---

### Post by DoTry on 2006-06-25
[QUOTE=mips]I think future versions of wordtrans will support .blg files. Another one to look out for is QTrans in future.

Can't you use .dict files for now ?[/QUOTE]

Sad thing is, there is no .dict for my language... I searched.

I found couple of solutions - babylon has online dictionary (though, I don't know if it contains the same length of definitions the pro version has), so there are couple of softwares that use this option. Kabylon is based on this principle. Other scrips I found are addons to Firefox (which follow again the same principle).
So, I'll use this for now, hopefully Wordtrans will get right on track and their next release will support blg.

---

### Post by mips on 2006-06-25
What is your language ?

---

### Post by DoTry on 2006-06-25
Hebrew. The only resource is (or better yet was) Babylon.

---

### Post by mips on 2006-06-25
Ok, I did a bit of googling and engtoheb.dic does exist, dunno about hebtoeng.dic.

Start searching with google or contact babylon for the .dic files. Alternatively as them if their is any way to conver from the new to the old file formats.

---

### Post by DoTry on 2006-06-25
No.. There is nowhere to download engtoheb - even google didn't help.

Anyways, I'm no worried. I'll use the online babylon translator (which seems pretty good) and my dictionary books. Heh, it's right about time to stop being spoiled and use books ;>

---

### Post by mips on 2006-06-25
engtoheb.dic definately does exist as I found numerous references to it on the net.

---

### Post by DoTry on 2006-06-25
You have no obligation to do so, however, if you'll check the links in google you'll see these are not download links. They relate to someone who posted he lost the file engtoheb and asks where can he download it, no replies. One relates to a guide about wordtrans with hebrew support, etc.

---

### Post by medya on 2007-04-27
you can convert BLG (babylon dictionaries) using dictconv, it is [explained here]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")

---

### Post by glps on 2007-12-15
There is **qtrans** for kde3 see that link:
[http://packman.links2linux.de/package/qtrans](http://packman.links2linux.de/package/qtrans)

It uses babylon *.dic dictionaries and supports hebrew and japanese.

---

### Post by Oriolo on 2008-04-13
Yes, engtoheb together with other dictionaries can be found at:
[ftp://ftp.ac-grenoble.fr/ge/languages/babylon_dict/](ftp://ftp.ac-grenoble.fr/ge/languages/babylon_dict/)
Good luck!
:)

---

### Post by marciowb on 2008-07-17
There is [Stardict]("http://stardict.sourceforge.net"). Try it and love it! It's fantastic! Better than Babylon. Belive me.
If you need some help to full install it or its TTS or glossaries, see tips at: [http://www.marciowb.net/blog/2008/07...a-linux-para-o](http://www.marciowb.net/blog/2008/07...a-linux-para-o)

Regards,
Marcio Wesley Borges
[http://www.marciowb.net/blog/](http://www.marciowb.net/blog/)

---

