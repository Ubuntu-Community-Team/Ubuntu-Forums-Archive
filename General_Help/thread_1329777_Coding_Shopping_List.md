---
title: "Coding Shopping List"
date: 2009-11-17
forum: General Help
---

### Post by old_salt on 2009-11-17
I've been a Linux user for 6 years and well versed in a lot of areas. Everywhere you turn from newbs to experienced, there's the promo to "Give Back" or "Get Involved" with the focus primarily being development or writing programs. 

Well, as a networking person, I'm now getting that itch to try my hand at coding. I'm clueless just like anyone else that's not a professional coder so........ here's my request.

Could this forum post a ""Get Started to Coding How-To" for those who are interested to the curious?

I think questions to be answered would be;

- What binaries, libraries etc should be installed?
- What apps should be used for working on GUI's / and code?
- What languages are specific to KDE, Gnome, XFCE and what's neutral to all?
- What are some links to guides for beginners?
- What are some good books available for beginners?
- Are there any online resources of developers/coders that are willing to conduct classes or maybe even take under one's wing on a particular project?


I see IRC, Mail Lists, Twitter and a myriad of means to communicate however; I've been in the IT field for 23 years and NEVER used any of these let alone IRC. Don't know squat about these. I think this area needs to be identified as well if it's required.

Not looking for attitude here, just trying to explain that to get started, what's needed TO get started? I'll bet my next paycheck I'm not alone either.

:P

---

### Post by scragar on 2009-11-17
OK, I guess I'll start off this list.

First you need to pick a language, with perl(Not something I'd recommend for a beginner, included only because it's my current language of choice) and python you should be all set, for C/C++ you will need build-essential.```
sudo apt-get build-essential
```

Personally I would say if you have to learn a gui easily, go for QT, it's so much simpler and shorter than GTK.

Everything is neutral on all enviroments, QT just runs slightly faster on KDE and GTK on gnome, honestly in modern enviroments it's not a big deal though.

 [http://www.reddit.com/r/carlhprogramming/?count=150&after=t3_9o8ey](http://www.reddit.com/r/carlhprogramming/?count=150&after=t3_9o8ey) Best C/C++ tutorial I can think of right now.

[http://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list](http://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list) Honestly I would not purchase a book though unless you can follow an online tutorial, online tutorials often offer more advice and are upto date, books tend to go out of date and don't allow for copy/paste.

No idea for this, sorry.

---

### Post by fluffman86 on 2009-11-17
Linux itself is really built around a lot C code.  Ubuntu/gnome uses C/C++ and the GTK+ libraries.  Kubuntu/KDE uses Qt.  A few programs use python and java.

If you've never done any coding at all before, I would actually suggest starting with html and css.  I know, I know...HTML is not computer code.  But it teaches you how to open and close tags, how to read documentation, and how to verify your code is working.  Maybe then you could follow that up with some PHP.

If you want to start building programs straight away, then look into python.  It's really simple to learn, and pretty powerful.  python.org has it's own tutorials available, and you can pick up books at a local bookstore as well.

After python, maybe try out some java, then perl, and then move on to a lower level language like C.

Of course, that's really if you have all the time in the world.  In actuality, you're going to mess around with (hopefully) a few languages, find one that you really like, and probably never move from there.

---

