---
title: "Help with bash"
date: 2006-02-04
forum: General Help
---

### Post by Rahu on 2006-02-04
I was wondering how to set programs to run from a single command in bash

My specific problem:
I installed Firefox 1.5 to/home/jeff/Programs/Firefox/
Firefox 1.0 is set to the command "firefox" in the terminal
I would like to have that command open firefox 1.5


thx to anyone for help :)

---

### Post by bongobonga on 2006-02-04
The command 'which firefox' will give you the full path name of the file that is executed when you run firefox from the command line. It will probably be '/usr/bin/firefox', which is itself a link to whatever location in which the file 'firefox ' is located. For me, 
'ls /usr/bin/firefox -lah' gives

lrwxrwxrwx  1 root root 30 2005-11-29 20:43 firefox -> ../lib/mozilla-firefox/firefox

So all you have to do is to delete this link and replace it with a link to whatever version of firefox that you want. Do something like the following 

ln -s /home/jeff/Programs/Firefox/firefox  /usr/bin/firefox

---

