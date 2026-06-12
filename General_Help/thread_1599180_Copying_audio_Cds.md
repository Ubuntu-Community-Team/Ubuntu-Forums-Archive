---
title: "Copying audio Cds"
date: 2010-10-17
forum: General Help
---

### Post by Man_Beach on 2010-10-17
What's the best way to make a simple, straightforward copy of an audio CD in Ubuntu 10.04 (Lucid Lynx)?

---

### Post by TeoBigusGeekus on 2010-10-17
What software do you use? Brasero, K3b, none?

---

### Post by Man_Beach on 2010-10-17
Well, I've tried Brasero and that doesn't work.

---

### Post by TeoBigusGeekus on 2010-10-17
> **Man_Beach said:**
> Well, I've tried Brasero and that doesn't work.
Any specific error messages?

---

### Post by Elfy on 2010-10-17
Do you mean copy or rip? I use sound juicer to rip.

---

### Post by Man_Beach on 2010-10-17
A straight copy.

Error message :

All required applications and libraries are not installed.

Please install the following manually and try again:
cdda2wav (application)
toc2cue (application)
cdrdao (application)
toc2cue (application)
cdrdao (application).

---

### Post by TeoBigusGeekus on 2010-10-17
Well, install them
```
sudo apt-get install cdda2wav toc2cue cdrdao
```

---

### Post by Man_Beach on 2010-10-17
That isn't what I asked: I want something that works, not solutions for something that doesn't.

I seem to remember when I last tried (in 8.10) it wasn't necessary to manually install things for what should be a straightforward and simple operation - I just put a disc in, hit the copy button and made a copy. We're in the 21st century now and it shouldn't be necessary to manually install anything for such a basic operation. Take a look at the (mostly incomplete) bugs in Brasero [https://launchpad.net/ubuntu/+source/brasero/+bugs](https://launchpad.net/ubuntu/+source/brasero/+bugs) and perhaps you'll see why I'm reluctant to bother any further with Brasero.

---

### Post by yetiman64 on 2010-10-17
Here's a link to check,
1. Method to create an iso of an audio cd (uses sound juicer) [--Link-- ]("https://help.ubuntu.com/community/CreateIsoFromCDorDVD")
> 
[LIST=1]
[*]Insert the CD or DVD
[*]Wait for Sound Juicer to pop-up with the songs on the disc
[*]Close Sound Juicer
[*]Click "Places" > "Computer" (the menu at the top of your screen)
[*]Right-click the icon of the CD
[*]Select "Copy Disc..."
[*]Alongside "Copy disc to:", change the drop-down to read "File image"
[*]Click "Write"
[*]Choose where you want to save the file
[*]Click OK
[/LIST]
To burn the cd takes 2 clicks, right click the image file (iso) and click "Write to disc"
Edit: <removed 2nd method link as it was not straightforward, that is, it relied on terminal use>

---

### Post by Man_Beach on 2010-10-17
GnomeBaker works.

(And as an aside, I fail to see why Ubuntu is happy to issue a new release when they haven't ironed out all of the bugs in the previous one. I bet Brasero can't copy a CD in Maverick, either.)

---

