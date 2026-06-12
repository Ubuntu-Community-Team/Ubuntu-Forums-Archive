---
title: "Emacs!"
date: 2010-08-01
forum: General Help
---

### Post by TheHimself on 2010-08-01
With the advent of emacs23-gtk I , at last, dared to get my hands on it. I've installed "emacs goodies" which are some .el files but I don't know how to "run" them and more importantly how to have them run when emacs begins. 

Also there are some simple things like having emacs load files of the last session automatically or remembering line wrapping mode that I don't know how to do. Does emacs23-gtk support tabs?

---

### Post by TheHimself on 2010-08-03
Any ideas anybody?

---

### Post by dino99 on 2010-08-03
[http://superuser.com/questions/55642/how-to-install-emacs-text-editor-on-ubuntu-linux](http://superuser.com/questions/55642/how-to-install-emacs-text-editor-on-ubuntu-linux)

---

### Post by TheHimself on 2010-08-03
I've already installed emacs. My question is about using it.

---

### Post by Zorgoth on 2010-08-03
As far as "tabs" goes, I don't know if you can get a tabbed interface, but emacs automatically maintains all your open buffers, and supports frames (C-x 2 and C-x 3 to split window, C-x 0 to close a frame, C-x 1 to close all other frames).  You can switch between buffers by clicking on the buffer name (right-click goes the other way) or with C-x Left and C-x right.

As far as what emacs does automatically on startup, in the installation instructions for whatever you downloaded you should find short segments of code to paste into your ~/.emacs file, which gives emacs its initial state.

I think it is also possible to save the buffer state for a later session, but I don't know how because personally I just save my files regularly.

One thing about emacs is that you should not expect it to handle things in the same way as another editor (e.g. GUI-based concepts like tabs).  It will, however, almost invariably handle them better :D

Edit:  I posted a quick emacs tutorial with all the basic keyboard shortcuts recently if you're interested:

[http://ubuntuforums.org/showthread.php?t=1542042](http://ubuntuforums.org/showthread.php?t=1542042)

---

### Post by TheHimself on 2010-08-05
Thanks this helps a lot. Another unusual thing is that when I type something like () or {} or $$ then the cursor jumps two places back and after a second goes back to its original place! What is the rational behind this?

---

### Post by Zorgoth on 2010-08-05
It is indicating the location of the matching bracket I believe.

---

### Post by jpkotta on 2010-08-07
> **TheHimself said:**
> With the advent of emacs23-gtk I , at last, dared to get my hands on it. I've installed "emacs goodies" which are some .el files but I don't know how to "run" them and more importantly how to have them run when emacs begins. 

Also there are some simple things like having emacs load files of the last session automatically or remembering line wrapping mode that I don't know how to do. Does emacs23-gtk support tabs?

To use an elisp library, you have to load the file.  There are various ways to do this, but the best way is usually [autoloading]("http://www.gnu.org/software/emacs/manual/html_mono/elisp.html.gz#Autoloading").  The elisp-goodies package is mostly set up for autoloading, so you only have to execute a command and the correct file(s) will get loaded.

There is desktop.el that can save all sorts of state.  I've never tried it.  I use [save-visited-files-mode]("http://github.com/nflath/save-visited-files/").

There is a tabbed-mode included in elisp-goodies, but as Zorgoth said, there are better ways.  I use [ido]("http://www.emacswiki.org/emacs/InteractivelyDoThings").  Ido is faster than tabs (if you know the buffer you want) and scales to dozens of buffers.

---

### Post by TheHimself on 2010-08-10
Thanks! Now I can see how powerful emacs is. 

I got a code from [http://xahlee.org/emacs/file_management.html](http://xahlee.org/emacs/file_management.html) to make emacs open contents of a subdirectory in the same buffer and I added it to my .emacs file but it doesn't work.

---

