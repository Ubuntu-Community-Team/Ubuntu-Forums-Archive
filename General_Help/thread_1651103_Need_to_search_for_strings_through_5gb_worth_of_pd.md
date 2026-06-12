---
title: "Need to search for strings through 5gb worth of pdf documents on a regular basis"
date: 2010-12-22
forum: General Help
---

### Post by J-E-N-O-V-A on 2010-12-22
But I'm not sure how to program it, or don't have the will to right now. Does anybody here? 

Which programming language would you recommend if I manage to get some initiative?

---

### Post by cjhabs on 2010-12-22
> **J-E-N-O-V-A said:**
> But I'm not sure how to program it, or don't have the will to right now. Does anybody here? 

Which programming language would you recommend if I manage to get some initiative?

I use recoll to search through my documents - it indexes pdf files.

---

### Post by tgalati4 on 2010-12-22
There are some document management tools out there:

egroupware-mydms - web-based groupware suite - document management system

mydms - open-source document management system based on PHP and MySQL

recoll - Personal full text search package with a QT GUI

apropos pdf

This brings up a bunch of PDF-to-whatever tools that could be used in a search script.

For instance:

pdftotext FILENAME.pdf | grep "Your particular search string" >> searchdump01.txt

Add some looping and you're done.

---

