---
title: "svn - subversion question?"
date: 2012-03-02
forum: General Help
---

### Post by liquidmonkey on 2012-03-02
just started using svn and one thing puzzles me.
i have added a folder that has some files in it, call it 'SpecialFolder'.

i have since renamed 'SpecialFolder' to 'BookFolder' and changed/moved a few things with the newly named BookFolder.
when i goto commit it, it tells me it can't find a certain file or text.

so how can i force the repository to rename the folder and add all the contents?
and if i do a svn update, i get the SpecialFolder back with all the original contents when really i need all that replaced with BookFolder.

thanks for any suggestions!

---

### Post by sagar_322 on 2012-03-02
Delete the 'Book Folder' if u have renamed it, then do svn up to get fresh copy of 'SpecialFolder' from repo then do svn move SpecialFolder Book Folder. This should change the folder name and then commit the changes. 
Hope this helped you.!!!

---

### Post by liquidmonkey on 2012-03-02
it turned out to be a bit more complicated but you totally helped out, thanks!
needed to do a bunch of svn --force delete and svn commit :)

in the future i will use svn move!

---

