---
title: "Question regarding recursive scripts"
date: 2009-07-22
forum: General Help
---

### Post by naturenut on 2009-07-22
First a little background. I'm new to linux, but have been using OS/2 for many years.

I had a setup under OS/2 for building webpages using CMD files (scripts) and BASIC apps I wrote. I have translated the CMD files to linux scripts and made the changes to the programs to make them work and all works as it should. The process is as follows:

1) menu script is run, which
     a) runs a BASIC program to display a menu and write the MenuAction script
     b) calls the MenuAction script

2) MenuAction script is run, which
     a) runs commands to do the dirty work - combination of BASIC and scripts
     b) calls menu script, unless Exit was chosen in the menu, then it exits the shell

Now, under OS/2 I had problems with this setup if I ran through the loop very many times - the return stack would fill up and the shell would close. Linux seems to be more adaptable, so I'm curious as to whether I can pop the menu script address off the top of the stack when MenuAction is run with an option other than Exit?

---

