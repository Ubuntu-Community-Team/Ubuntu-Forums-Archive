---
title: "mysql workbench files open with file roller"
date: 2011-06-15
forum: General Help
---

### Post by mrlizard123 on 2011-06-15
I have mwb files that clearly are some form of zip as ubuntu insists they are "Zip archives" and if I change the program to mysql-workbench all zips also get changed.

Can I override the MIME type program opening (which is what I'm assuming is happening) and say that for mwb extension just open with mysql-workbench?

Cheers!

---

### Post by DanielAbrahao on 2011-10-28
I stumbled on same problem here. 
You can easily fix it following these steps:

First I edited the .desktop file, adding the MimeType parameter (I don't know if realy need this, but wont hurt)

```
$ sudo vi /usr/share/applications/MySQLWorkbench.desktop
```Just added this on last line:
```
MimeType=application/x-mwb
```After that, you need to create an xml file (x-mwb.xml) that will be used to create the new mime type:
[HTML]
<?xml version="1.0"?>
 <mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
   <mime-type type="application/x-mwb">  
   <comment>Workbench file</comment>
   <glob pattern="*.mwb"/>
 </mime-type>
</mime-info>
[/HTML]Then, just run this 3 commands and it is all! You are done!
```

$ xdg-mime install x-mwb.xml
$ xdg-mime default /usr/share/applications/MySQLWorkbench.desktop application/x-mwb
$ xdg-icon-resource install --context mimetypes --size 48 /usr/share/mysql-workbench/images/MySQLWorkbench-48.png application-x-mwb
```


Hope it helps you. Or someone else! :)

---

