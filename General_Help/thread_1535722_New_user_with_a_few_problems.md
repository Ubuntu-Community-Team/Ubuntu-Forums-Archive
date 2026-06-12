---
title: "New user with a few problems"
date: 2010-07-21
forum: General Help
---

### Post by Marksman09 on 2010-07-21
Hey guys, Dunno if this is where I'm supposed to post this or not but not 100% sure on the forum rules yet.
Just installed a nice clean version of Ubuntu 10, after trying Ubuntu 9 a few times and having constant struggles with my graphics card drivers i was amazed to see everything working and a usable operating system in front of me. The problem now is a lot of the reasons i switched to Linux aren't working. If anyone knows the cause, how to fix, or just where to point me in regards to any or all of the following problems I would be extremely grateful. thanks :)

1) I Seem to be having some trouble with php. When i open a php file through Firefox off my web server i get a completely blank page. No errors just a blank page. When I connected to my pc through ssh from a friends house, i was editing the same document and opening it from my own web server at home without a problem.

2) After trying to edit the config file for gvim (/home/mark/.gvimrc) it know opens this file everytime i startup GVIM ignoring the settings and giving me an error saying  'E484: Cannot open file /home/mark/.syntax.vim'

and just as a side note if anyone has any ideas, I cant open Java files but to be honest i really couldn't care less, I just want to be able to enjoy programming. Please help :)
Thanks.

---

### Post by deathadder on 2010-07-21
> 
1) I Seem to be having some trouble with php. When i open a php file through Firefox off my web server i get a completely blank page. No errors just a blank page. When I connected to my pc through ssh from a friends house, i was editing the same document and opening it from my own web server at home without a problem.
In your php.ini file (/etc/php5/apache2/php.ini) make sure that "display_errors = On" and that error_reporting is set "error_reporting = E_ALL & ~E_NOTICE"

---

### Post by Marksman09 on 2010-07-21
Woo, I've never been so happy to see an error message, thanks for the help deathadder. :)

---

