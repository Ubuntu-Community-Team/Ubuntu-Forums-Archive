---
title: "Bash find/replace?"
date: 2010-04-03
forum: General Help
---

### Post by jon.reeve on 2010-04-03
I'm having problems with Tomboy. I have a few hundred note files and I need to go through all of them and replace all instances of "<link:broken>a</link:broken>" with "a". Is there a bash command I can use to do this?

---

### Post by jobix on 2010-04-03
I'm assuming these note files that you refer to are simple text files. Here's an example of how you would replace it for a single file named abc.txt:

> sed -i 's/<link:broken>a<\/link:broken>/a/g' abc.txt

Use a for loop if you want to do it for multiple files. Try it out on one file to make sure it's messing up anything. Also, it's good to have backups if the files are very important.

Here's a simple tutorial on sed.

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by jobix on 2010-04-03
Upon reading a bit further, apparently sed can make an auto-backup. Use "sed -i.bak" instead of "sed -i".

---

