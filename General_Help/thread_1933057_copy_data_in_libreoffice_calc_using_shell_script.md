---
title: "copy data in libreoffice calc using shell script"
date: 2012-02-28
forum: General Help
---

### Post by kashif12 on 2012-02-28
Good Day.

I want to :
 clear and update sheets (from files on local disk) in libreoffice calc file using shell script or macro
 change TITLE of graphs in those sheet using shell script /command/command


I have one libreoffice calc file which contain  four sheets

abc_28022012 |def_28022012|ghi_28022012 | jkl_28022012

I want guidance in making a shell script or macro to:

  automatically change name of sheets to todays date
  automatically change TITLE of graphs in each sheet to todays date
  automatically clear contents of each sheet and fill in value from a location on local system from files abc.xls ,def.xls etc

Appreciate any help ...

In windows it is piece of cake but in ubuntu ;)

---

### Post by TeoBigusGeekus on 2012-02-29
You have 2 options:
1) Use the libreoffice api:
[http://planet.go-oo.org/]("http://planet.go-oo.org/")
This of course would require you to learn Java or Python or C++, etc.

2) Manipulate ods documents as xml text files. If you save an ods file from libreoffice as straight xml (.fods file), you can open it with a text editor and see how it is constructed. You can then create a text manipulating script (heavy on sed commands I presume) which can change the contents of the xml file according to your needs.

---

