---
title: "Hide File Extensions"
date: 2011-04-25
forum: General Help
---

### Post by shimabuku on 2011-04-25
Hello everyone! Just recently installed the latest Ubuntu on my laptop and working perfectly. I have installed and configured LAMP but unable to figure out how to hide php and html file extensions when visiting a URL. I have enabled mod_rewrite via sudo a2enmod rewrite. Can this be accomplished globally rather than using a htaccess file? Thanks!

---

### Post by majorawesome on 2011-04-25
Well all you have to do is go rename your files to just the name
for example, you have a file called "pudding.mp3" if you removed the ".mp3" aka extension and the file will be called "pudding" you think it wouldn't work right? WRONG! nautilus still recognizes the file WITHOUT the extension. although some programs need the extension but I don't know which.

---

### Post by shimabuku on 2011-04-25
Not the answer i was quite looking for. Maybe I posted this thread in the wrong section.

---

### Post by SeijiSensei on 2011-04-25
I'm not sure I understand the reason for your question.  File extensions like .html and .php tell the web server what Content-Type headers to use and, in the case of PHP, whether to use the parser or not.

Now if you're trying to create URLs like this:

[http://www.example.com/something/](http://www.example.com/something/)

then just make sure that "Options +Indexes" is enabled in the directory to which /something/ points, and create an index.html or index.php file in that directory.  You can point to that URL, but the address bar in the browser will usually still include the complete filename once it is fetched from the server.

If you have parameter strings you can use:

[http://www.example.com/?key1=value1&key2=value2](http://www.example.com/?key1=value1&key2=value2)

Why you care about the extensions being shown is beyond me, though.

---

### Post by WorMzy on 2011-04-25
> **SeijiSensei said:**
> Why you care about the extensions being shown is beyond me, though.

Probably because of [this]("http://mikeschinkel.com/blog/welldesignedurlsarebeautiful/")

@OP, if you'd prefer to have "beautiful" URLs by default, maybe you should consider using a framework like Django. Making Apache use beautiful URLs is a hassle.

---

### Post by shimabuku on 2011-04-25
Thanks for the quick replies! Whenever I go to a directory such as something/ it displays the index.html or index.php file. Is there a way to hide this globally ie. apache2.conf?

---

### Post by dino99 on 2011-04-25
create an hidden folder ( .myfolder) and move your files into it

---

