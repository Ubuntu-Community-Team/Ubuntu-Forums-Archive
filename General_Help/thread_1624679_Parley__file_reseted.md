---
title: "Parley : file reseted"
date: 2010-11-18
forum: General Help
---

### Post by azerty.123.450 on 2010-11-18
Hello, I use Lucid Lynx and Gnome. This morning, I was restarting Parley  from command-line to understand why it didn't played mp3 files. On  restarting Parley, I pointed out that my file was reseted. 


 This is what was written on my terminal and the content of my file.

 ```
Parley(4722): "Could not open or properly read "/media/Documents_/Parley/Anglais/Vrac.kvtml"
(Error reported: unexpected end of file)" "Error Opening File"
```
 ```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE kvtml PUBLIC "kvtml2.dtd" "http://edu.kde.org/kvtml/kvtml2.dtd">
<kvtml version="2.0">
  <information>
    <generator>Parley 0.9.3</generator>
    <title>Document Lesson</title>
    <date>2010-11-18</date>
  </information>
  <identifiers/>
  <entries/>
</kvtml>
```
 The file backup has the same content.

 

 ```
-rw-r--r-- 1 alpha alpha  311 2010-11-18 09:08 Vrac.kvtml
-rw-r--r-- 1 alpha alpha  311 2010-11-18 08:59 Vrac.kvtml~

```
 

 I just want to add, that an update system occured during I used Parley.

 

 What can I do to recover my file ?

---

### Post by zaphod777 on 2010-11-18
I'm not to familiar with that program but it looks like you have 3 identical threads you should delete the others. 

My best guess would be to purge the program and re-install if you don't mind losing your configuration files.
```
sudo apt-get purge parley
sudo apt-get install parley
```

---

### Post by azerty.123.450 on 2010-11-18
Ok, I've just emptied the others threads, I knew they were not posted.

I tried your advice, but my datas are still missing.

---

### Post by zaphod777 on 2010-11-18
hmm not sure how to fix this error you may want to submit a bug report to the parley team 
[https://launchpad.net/ubuntu/+source/kdeedu/+bugs](https://launchpad.net/ubuntu/+source/kdeedu/+bugs)

Another great flash card program is called Anki you might want to check it out if you can't get Parley working. Anki even has an Android app and an online client and allows syncing between them all.

---

