---
title: "finding file directories through command terminal"
date: 2012-07-22
forum: General Help
---

### Post by opfeld on 2012-07-22
I am trying to use the chown cmd to change the ownership of an entire file on my computer, and I get it for the most part

sudo chown -R username /home/username/Downloads/movie backdrops

Problem is that the terminal keeps telling me that this directory doesn't exist

It does exist and if I open one of the files in there the location is exactly as I typed above but it still doesn't get found. 

Is there some type of naming convention used when operating the terminal I am missing?

---

### Post by qamelian on 2012-07-22
The problem is the space between the words movie and backdrops. You need to place a \ before the space, like so:
```
sudo chown -R username /home/username/Downloads/movie\ backdrops/
```

Linux doesn't treat spaces in file and folder names the same as Windows. Linux interprets movie and backdrops as two separate entities, rather than one folder name. The \ is called an escape and it basically tells the shell to treat the space as a literal part of the name.

---

### Post by opfeld on 2012-07-22
thank you very much that worked perfectly, good thing to know

---

