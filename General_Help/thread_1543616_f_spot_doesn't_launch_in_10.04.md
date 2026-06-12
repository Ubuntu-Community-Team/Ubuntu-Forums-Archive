---
title: "f spot doesn't launch in 10.04"
date: 2010-08-01
forum: General Help
---

### Post by shellbo on 2010-08-01
hello everyone
i recently did a fresh live-cd install of 10.04, after a crash.
now f-spot won't launch
when i try to start it, a panel window opens saying "starting f-spot", but nothing happens
tried doing a reinstall/install- didn't work
tried reading forum documentation, but nothing has worked so far
any suggestions?

---

### Post by BLOODBANKER on 2010-08-10
Sorry to hijack this problem, but my Lucid install will not launch F-spot either. Any help would be nice.,,  Running on a Dell Dimension 8200.;)

---

### Post by jcolyn on 2010-08-10
Have you tried shutting down the computer for a minute then restarting it??

I do a lot of image editing using Gimp and recently darktable and need a good image viewer. F-stop was worthless for me even though it worked. I didn't like how it catalogs the images into multiple folders so I installed gthumb from the repositories or you can open a terminal and type ```
sudo apt-get install gthumb
```

A much better image viewing program..

---

### Post by shellbo on 2010-08-11
restart deos not solve anything, neither does a reinstall.... 
anyone??? 
help please!

---

### Post by azertyh on 2010-08-11
hi,
i had the same problem and solved it : delete the folder ~/.config/f-spot
my thread about it : [http://ubuntuforums.org/showthread.php?t=1520451](http://ubuntuforums.org/showthread.php?t=1520451)

---

### Post by shellbo on 2010-08-11
hi.
i ran across this post when i first started searching for an answer, but unfortunately i don't really understand the proposed solution.
what is it that i have to do exactly and how do i have to go about doing it?
a newbie-friendlier explanation would be very much appreciated!

---

### Post by azertyh on 2010-08-12
launch nautilus
ctrl+h to show hidden files
double-click on the folder .config
delete the folder f-spot

---

