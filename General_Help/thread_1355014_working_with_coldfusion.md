---
title: "working with coldfusion"
date: 2009-12-14
forum: General Help
---

### Post by phillip1882 on 2009-12-14
Before I begin, I did want to thank you guys for all the help you've provided. Does ubuntu have a donate button?
But anyway, I am learning cold fusion and haven't really worked with servers before, I understand much of the SQL logic behind it, but haven't really written anything for myself yet. To make a long story short, I need to be able to work with cold fusion. I successfully installed it, but it put the files on my hard disk, and I'm not exactly certain what the next step is. There is further installation I need to do, but in order to do it I need access to my hard disk. Can anyone give some advice and help?

---

### Post by phillip1882 on 2009-12-17
bump, sorry

---

### Post by junapp on 2009-12-17
well cold fusion is similar to php in purpose, so you'd want to create a cfml or cfm page which renders some html. You'll probably want to start by putting that file in /var/www

After that, you use your browser (if on the same machine) and browse to [http://localhost/yourcfmfile.cfm](http://localhost/yourcfmfile.cfm)

From there, you can do anything you want. You'll want to start by finding a beginner tutorial for Cold Fusion which brings you through the basic cf tags.
example: [http://articles.sitepoint.com/article/cold-fusion-tutorial#](http://articles.sitepoint.com/article/cold-fusion-tutorial#)

Does that help?

---

### Post by phillip1882 on 2009-12-17
a little, but what  really need to know is how to access my hard drive from command prompt.

---

### Post by junapp on 2009-12-21
how many hard drives do you have?

your whole filesystem is stored on your hard drive, which when you goto a command prompt likely puts you in your home folder (which is on your harddrive).

What specifically are you trying to do?

When at a command prompt type 
ls -la
and you'll see a list of files - those are on your harddrive. Use a command like 'cd' to change to whatever directory you want to view.

---

### Post by phillip1882 on 2009-12-22
Okay, I'm sorry, I guess I should be more specific, I need access to the root file system, in particular where cold fusion is stored. 
(File System/opt/coldfusion9)

---

