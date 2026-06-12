---
title: "General software for viewing huge .txt files..."
date: 2010-05-19
forum: General Help
---

### Post by jiapei100 on 2010-05-19
Hi, all:

Is there any software in Linux to view huge .txt files, say, over 10 megas?

I'm now using default "gedit", version 2.28.0, which seems to not be able to open huge .txt files.

It's the same case for Windows default .txt browser, but in Windows, "Win Word" seems to work fine.

Any suggestions for software under Linux to browse huge .txt files?

Cheers
JIA

---

### Post by SlidingHorn on 2010-05-19
Give Mousepad a shot:

```
sudo apt-get install mousepad
```

Then to open/edit the file:

```
mousepad <file>
```

---

### Post by efflandt on 2010-05-19
To view text files, you could always use **less** from a terminal (make the terminal 132 columns wide if you need to).

---

### Post by SlidingHorn on 2010-05-19
> **efflandt said:**
> To view text files, you could always use **less** from a terminal (make the terminal 132 columns wide if you need to).

Didn't think to mention it, but you could also use vi:

```
vi <filelocation>
```

It's not as up-front as your average text editor, so here's a good reference guide to get you started: [http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Editors/ViIntro.html]("http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Editors/ViIntro.html")

---

### Post by Lord.Quackstar on 2010-05-19
nano is actually pretty good. It's built in, so just nano sometextfie

---

### Post by jiapei100 on 2010-05-19
Hi, all the above:

Thank you everybody. Thanks for you kind and prompt reply.

However, nano and vi are bash commands which may only open .txt file from within bash view. It's not quite convenient for me to control the way to browse.


Thanks to SlidingHorn. Mousepad is perfect. That is exactly what I need. Pretty fast and extremely convenient.

Best Regrads
JIA

---

