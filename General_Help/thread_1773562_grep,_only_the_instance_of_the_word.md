---
title: "grep, only the instance of the word?"
date: 2011-06-02
forum: General Help
---

### Post by jaes84 on 2011-06-02
I am trying to run grep on my file, which has alot of unneccesary stuff, and i want to extract stuff like: g_file" g_type" and so on, but when i run egrep g.*" on the file, it just prints out every line with this instance. How do i stop grep from doing this, and just printing out the word?

---

### Post by Habitual on 2011-06-02
-w matches whole word.

[http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep)

---

