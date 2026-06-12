---
title: "Replacing crap in files"
date: 2010-01-26
forum: General Help
---

### Post by jfreak53 on 2010-01-26
Ok I know title is catchy, ha ha.  I suck at regular expressions so I need some help guys.  I have a moodle install on my server that some but not all of the files have a return at the top of the file and at the very end of the file, this is adding too much space at top of page and breaking css, like 20 lines extra blank!  But it's a bunch of files across a whole moodle install, I can't do it by hand.

So I think I got the find command and sed working, what I am missing is the actual find and replace part, or delete which ever you think would work better.  Here is what I got:

> find . -name "*.php" -type f -exec sed -i 'this is what im missing' {} \;

As you can see I have tried many things in the quotes but either they erase everything or they erase characters through out the whole file.  So what do I need to add or remove to make the replace sequence remove a carriage return at the top of every php file if it exists and one at the bottom last line only if it exists?  Thanks in advance guys.

---

### Post by J V on 2010-01-26
uhm... for your purposes I would try a python strip() command, would probably work much easier...

---

### Post by jfreak53 on 2010-01-26
Don't know python at all, how would that work?

---

### Post by t4thfavor on 2010-01-26
or perl, If you give us an example of what you are trying to remove I can try to model something around it.

---

### Post by JohnFH on 2010-01-26
```

# delete all leading blank lines at top of file
 sed '/./,$!d'

 # delete all trailing blank lines at end of file
 sed -e :a -e '/^\n*$/{$d;N;ba' -e '}'  

```

Taken from here:
[http://www-h.eng.cam.ac.uk/help/tpl/unix/sed.html]("http://www-h.eng.cam.ac.uk/help/tpl/unix/sed.html")

---

### Post by jfreak53 on 2010-01-26
JohnFH:

PERFECT!  Thanks for the help, I searched for those two things forever and never found it on google.  Thanks again everyone for your help.

---

