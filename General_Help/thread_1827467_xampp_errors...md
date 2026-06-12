---
title: "xampp errors.."
date: 2011-08-18
forum: General Help
---

### Post by suryaD on 2011-08-18
hello ppl..i have a problem..the other day i installed xampp successfully on my ubuntu machine and all the files of xampp like htdocs etc are stored in /opt folder on my filesystem.the problem is whenever i write a php program thru bluefish editor  and store it in htdocs folder it is saying that u dont have permission to save it in this folder..below is the pic related to this error..guys are there any alternatives to save my files else where so that my pgm is executed
 running-xampp 1.7.4
 ubuntu ver-11.04(natty)
 editor-bluefish editor
[IMG]http://i56.tinypic.com/118ep14.png[/IMG]

---

### Post by suryaD on 2011-08-21
guys anyone know the solution...ASAP

---

### Post by Wim Sturkenboom on 2011-08-21
Read up about linux permissions.

Basically you need to get permissions to write in the httpdocs directory which is probably owned by apache, http, www-data or similar.

Read up how you can have the document root in another directory (e.g. a subdirectory in your home directory). Failing that, and useful anyway, read up on virtual hosts and place the document root for the virtual hosts somehwere in your home directory.

And there is no rush for us, only for you,so ASAP will not help much. It usually has the opposite effect. If you're in a hurry, do your own research.

---

