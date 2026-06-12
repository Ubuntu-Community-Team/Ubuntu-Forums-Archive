---
title: "Using Grep"
date: 2010-09-26
forum: General Help
---

### Post by flyingsuperhigh on 2010-09-26
Hello Everyone, 

I have a pretty simple problem but I still can't seem to figure out the solution. I basically have to use the grep command (I can't use any other command) to find a match. There a two files that exist. One file called (sorted.txt) contains information about users (one user per line). This information consists of their id, username, email, ...The second file (invalid.txt) contains just the name of the user (username). My task is to compare these two files and display all the user's and their info (id, username, email,...) who are on the second file. Also, I am writing  the output to another file called found.txt.

This is the command I am using:

grep -o -F /home/2009/jack/comp206/store/testbed/invalid.txt /home/2009/jack/comp206/store/testbed/sorted.txt>/home/2009/jack/comp206/store/testbed/found.txt

---

### Post by matt_symes on 2010-09-26
Switches are case sensitive. This may help [http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep).
Sounds like coursework to me so i will not write it for you.  Good luck.

---

### Post by CharlesA on 2010-09-26
Sounds like a homework assignment to me as well.

---

