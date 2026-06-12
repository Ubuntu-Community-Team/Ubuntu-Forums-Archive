---
title: "prerequest package problem"
date: 2009-06-30
forum: General Help
---

### Post by hero1900 on 2009-06-30
i am trying to install griffith
and i got this dependencies error 
**[COLOR=Red]satisfiable: python-support (>= 0.90.0)[/COLOR]**
and they require this packages to be pre-installed 
-------------------------------------------------
Griffith requires the following libraries:
 
[LIST]
[*][Python]("http://www.python.org/") 2.3 or later
[*][PyGTK]("http://www.pygtk.org/") 2.6.1 or later (including Glade)
[*][pysqlite2]("http://initd.org/tracker/pysqlite") 2.0 or later
[*][SQLAlchemy]("http://www.sqlalchemy.org/download.myt") 0.5 or later
[*][ReportLab]("http://www.reportlab.org/downloads.html") 1.19 or later
[*][Python Imaging Library (PIL)]("http://www.pythonware.com/products/pil/")
[*][PyXML]("http://pyxml.sf.net/")
[/LIST]
so what is the problem i already have python and pyGTK ??

---

### Post by synapsys on 2009-06-30
Maybe try

```
sudo apt-get build-dep griffith
```

---

### Post by hero1900 on 2009-06-30
not working i didn't add any repository i just download the DEB package manually i want to know what is the prerequisite that i need to install it

---

