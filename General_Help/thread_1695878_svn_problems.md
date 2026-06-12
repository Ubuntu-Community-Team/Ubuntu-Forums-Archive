---
title: "svn problems"
date: 2011-02-26
forum: General Help
---

### Post by colts18 on 2011-02-26
I have a project on google code and I want to add a file to it I am using xubuntu 8 so I need to use the terminal.  I thought I had to put svn add and the file name but that did not work. Anyone know?

---

### Post by colts18 on 2011-02-27
I have figured it out. To upload a file:
svn add file_name
svn ci -m "message explaining changes"  file_name

I also learned how to delete a file:
svn delete file_name
svn ci -m "message explaining changes" file_name

Hopefully that is helpful for someone else who is having trouble DO NOT USE SVN COMMIT THE SECOND LINE COMMITS CHANGES.

---

