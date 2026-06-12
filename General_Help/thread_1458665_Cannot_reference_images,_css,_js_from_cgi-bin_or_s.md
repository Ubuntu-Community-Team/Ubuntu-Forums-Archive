---
title: "Cannot reference images, css, js from cgi-bin or sub-directory"
date: 2010-04-20
forum: General Help
---

### Post by rkad40 on 2010-04-20
I posted this question on the beginner's forum but didn't get resolution.  Any help would be greatly appreciated ...

I am trying to run Perl based CGI tools on a Linux server running  Ubuntu.  My system admin is a bit of a novice at Linux configuration  (though infinitely more knowledgeable than me).  

So, my admin set me up with a public cgi-bin directory and sure enough, I  can execute CGI scripts from this directory.  

But there is one glaring problem ...

I can only execute scripts in this directory using the URL.  I cannot  reference image files, CSS files, JavaScript files or even view HTML  files in this or any sub-directory. At a minimum I would think that sub-directories should be public.  So in other words, if I want my CGI  applications to look like Craig's List I'm golden.  But alas, this is  not what I want.

My admin is really scratching his head on this one.  And unfortunately  I'm not literate enough in Ubuntu to help him out.  It's not a  permissions thing.  I know that much.  

Suggestions?

---

### Post by tgalati4 on 2010-04-20
Is ownership www-data:www-data for all files (except .htaccess) in /var/www/yourwebpage?

---

### Post by gmargo on 2010-04-20
There are a few responses on your ABT thread, including mine; the forum admins here frown upon multi-forum posting.  Especially after only a few hours.
[http://ubuntuforums.org/showthread.php?t=1458250](http://ubuntuforums.org/showthread.php?t=1458250)

---

