---
title: "Where can I find Nautilus Plugins?"
date: 2010-01-05
forum: General Help
---

### Post by JpTiger0 on 2010-01-05
I'm specifically looking for something that will let me batch rename files-- that is, highlight several files and rename them, so that the first is named what I type in, and the following are given maybe that name and a number (eg "pic.jpg, pic1.jpg, pic2.jpg" etc). Windows explorer has been able to do it forever, and if M$ can do it, linux should be able to do it better. 

The other plugn I'd like is to give more categories for sorting files, specifically "date picture taken." Closest thing nautilus has by default is "date file modified" which gets screwy if you do something like rotate an image. Any ideas?

I'd rather not switch from nautilus because I'm using a distro (eeebuntu) where it's very hard to disentangle the file manager from. I tried replacing it once with Thunar and it was a minor disaster. I ended up reinstalling the OS. Thanks!

---

### Post by Anzan on 2010-01-05
Just search Synaptic for "Nautilus".

---

### Post by JpTiger0 on 2010-01-05
Not much luck there. Found Nautilus actions, etc. but nothing for batch rename or display more categories. At least nothing obvious...

---

### Post by scott_g on 2010-01-05
> **JpTiger0 said:**
> I'm specifically looking for something that will let me batch rename files-- that is, highlight several files and rename them, so that the first is named what I type in, and the following are given maybe that name and a number (eg "pic.jpg, pic1.jpg, pic2.jpg" etc).

You could try GPRename:
```
sudo apt-get install gprename
```
It is a batch file renamer; very powerful once you figure out how to use it.

For the 'date picture taken' you could use F-Spot or something, but this might also be a limitation of the ext3 filesystem (as it doesn't have a date created tag, I belive, but it might be stored as a tag in the picture itself), I'm not sure.

These aren't plug-ins, but they give the same functionality I think...

Scott

---

### Post by oldos2er on 2010-01-05
Some ideas here: [http://ubuntuforums.org/showthread.php?t=352973](http://ubuntuforums.org/showthread.php?t=352973)

---

### Post by RedRat on 2010-01-05
I suggest that you use Thunar, it has a first class renaming function and every bit as good as Nautilus.

---

### Post by JpTiger0 on 2010-01-05
Cool, first of all thanks for all the replies. I have a batch renaming program (pyrenamer), but it's a pain to use-- in another file explorer, I just have to highlight the files, hit F2, type in a name and done. I handle a lot of photos at once, and it would make my work a lot faster. The lin for other ideas has just what I'm looking for in a script that works for nautilus, but the d/l link is broken. And as I said above, I'd rather not try to replace nautilus, as last time I did, bad things happened to my distro. I don't have the space on my little eeepc's hard disk (four gigs) to handle two file browsers.

So if anyone has a lead on that one script...

---

### Post by estiedi on 2011-04-13
If for renaming photos, I use **jhead**. It's installed by default with Ubuntu (I suspect that Shotwell depends on it). It can rename photos using the exif data. In my case I rename the files to the date/time the photo has been taken. Works great and is very fast. If you don't mind using a shell it might be an option.

Google for "+jhead script Ubuntu" and you'll find scripts that make the usage simpler for certain purposes (renaming, rotating,...).

---

