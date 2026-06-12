---
title: "Checking folder integrity with md5sum or shasum?"
date: 2009-10-15
forum: General Help
---

### Post by billdotson on 2009-10-15
When I burn data DVDs I would like to check the folder integrity of the files that I burn. I have not seen or figured out a way to do an md5sum or a shasum of a folder (or multiple files and folders as a collective group) only a specific file. 

Does anyone know how to do this? Thank you.

---

### Post by billdotson on 2009-10-16
Has nobody needed to do this before?

---

### Post by kavon89 on 2009-10-16
Write a script which recursively finds all the files within the directory, sort the list of files in lexicographical order and find the hash for every file. Then store it along with the path it can be found under the top folder (including the file's name) in a single line in a file. Then another smaller/easier script or flag in the same script to compare the files line by line in order.

Hell I might write this up in Java if you're interested, could be a useful little program.

EDIT: This should actually be more of a real program in C++ making use of multiple cores.

---

