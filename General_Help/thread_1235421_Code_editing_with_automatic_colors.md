---
title: "Code editing with automatic colors"
date: 2009-08-09
forum: General Help
---

### Post by kilgore9 on 2009-08-09
I'm new to writing "code" and use it only for one thing (lilypond).   I would like to customize gedit or some other program to automatically color certain symbols.  For example, curvy brackets "{ }" always blue, parentheses always red, etc.  Anyone know of a program that I can customize to do this?

---

### Post by Barafu Albino Cheetah on 2009-08-09
Jedit can be easily customized, (I managed to teach it Inform 7, which is the weirdest language I know). There was some music plugins for it already. 
Kate/KWrite can learn new languages too, but I remember the process was hard on KDE 3.3  
Or take console Emacs for old-school hardcore. One who knows Lisp can teach it everything.

---

### Post by kilgore9 on 2009-08-09
Thanks for the tip, but how do I "teach" gedit to do this?  Seriously I know nothing about doing code.... just this one program to create sheet music.....  I don't need a special code editor, just something that will color certain symbols when they are entered...

---

### Post by nikhilbhardwaj on 2009-08-09
jedit is a java based editor that will be perfect for you
you can find out here
[http://www.phpvideotutorials.com/jedit/](http://www.phpvideotutorials.com/jedit/)
as to how you can customize it
it has all features like syntax highlighting, code completion you name it and it's got it.

---

### Post by ad_267 on 2009-08-09
gedit support syntax highlighting by default too. It probably just doesn't have support for the lilypond format. You can try the different languages under View - Highlight Mode to see if one suits you.

It looks kind of similar to LaTeX markup so try that option.

---

### Post by kilgore9 on 2009-08-09
Yeah I found all the syntax highlighting, but none of it suits me for lilypond.  But I just read that Kate supports lilypond, I guess I'll try it!

---

### Post by ad_267 on 2009-08-09
Ok, if you don't like Kate you should be able to add syntax highlighting for Lilypond by adding a new lilypond.lang file in /usr/share/gtksourceview-2.0/language-specs. You could copy one of the existing files and customise it to your needs.

Edit: Here's a good explanation [http://live.gnome.org/Gedit/NewLanguage](http://live.gnome.org/Gedit/NewLanguage)

Someone already tried making a lilypond.lang file so you could start from that: [http://ubuntuforums.org/showthread.php?t=1150569](http://ubuntuforums.org/showthread.php?t=1150569)

---

### Post by kilgore9 on 2009-08-09
Thanks!  Kate looks OK so far and supports lilypond, looks real nice.  I like the look and feel of gedit better, but adding a new .lang file looks to be waaaaay beyond my ability.  The link to an explanation you sent makes absolutely no sense to me :P.  Like I said, I really know nothing about writing code.  I only know lilypond....

---

### Post by ad_267 on 2009-08-09
Fair enough, Kate's a good editor so you might as well stick with that.

---

### Post by kilgore9 on 2009-08-09
for any other lilypond users out there reading this, I just discovered Frescobadli [http://www.frescobaldi.org/](http://www.frescobaldi.org/) and its great!  It colors the code just like Kate, but includes PDF preview, convert to PDF with the click of a button, hotlinks to error zones, score wizard,  and lots of other useful stuff!

---

### Post by ad_267 on 2009-08-09
You might also want to keep an eye on [Canorus]("http://canorus.berlios.de"). It's designed to be a GUI notation editor more like Sibelius, but can use Lilypond to produce a PDF.

It's still early in development but it seems pretty usable. There are nightly builds for Ubuntu at [http://193.95.242.3/canorusNightly/ubuntu-i386/](http://193.95.242.3/canorusNightly/ubuntu-i386/). The latest ones seem to be broken though, the R1170 one works OK.

---

### Post by kilgore9 on 2009-08-09
Looks very interesting!  I feel like I still have so much to learn in lilypond, but it looks like i have time.  It will be a while before canorus is ready for prime-time, it seems....  anyway I love lilypond :)

---

