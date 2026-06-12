---
title: "TeTex / Miktex"
date: 2005-03-04
forum: General Help
---

### Post by Leif on 2005-03-04
Ok, sorry beforehand about how fuzzy this question is going to be, but if anybody's willing to help I'll try to fill in the missing parts as asked.

I've got a document that works fine under windows/miktex. I want to be able to completely switch to ubuntu, but when I try to latex the same files with tetex, I get errors. These files are on an smb share, so they are exactly the same files. 

First problem I get is with the fancyhdr package :

! Undefined control sequence.
l.39 \fancyheadoffset
                     [LE,RO]{\marginparsep+\marginparwidth}

The rest of the fancyhdr specific commands work fine. I figured it must be different versions, so I took out the offending line. Then I get :

! LaTeX Error: Cannot determine size of graphic in ..//logo.png (no B
oundingBox).

But the file logo.bb is in the same directory as the png, and this works fine under miktex too. Any ideas ?

On another note, I think I've gotten too used to miktex's automatic package downloading and graphical setup tools, I just don't get why a linux poster-boy project like latex works better under windows :)

---

### Post by drasko on 2005-08-21
Gee, I must agree on this -- MikTeX package manager is really great. I spend whole day today searching for missing styles and font. Why can't someone make a proper latex package manager for Linux? Now we are left with apt-getting tetex packages (all of them), and things are still missing...

Drasko

---

### Post by sonmez on 2006-03-14
By the way MikTeX 2.5, going to be released on first half of  2006,  is going to be for "Unix-like operating systems" too. So I wonder if it is going to be available for Ubuntu or not? MikTeX seems to be very actively developing. I think I would like to use it instead of TeTeX.

---

### Post by neoflight on 2006-03-15
[QUOTE=drasko]Gee, I must agree on this -- MikTeX package manager is really great. I spend whole day today searching for missing styles and font. Why can't someone make a proper latex package manager for Linux? Now we are left with apt-getting tetex packages (all of them), and things are still missing...

Drasko[/QUOTE]

why use tetex if you could use texlive:-D ...its very comprehensive...installing packages is easy though not automatic like the mpm.  

just suggesting...:)

---

