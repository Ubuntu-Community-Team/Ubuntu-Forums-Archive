---
title: "Quick command line validation please"
date: 2010-12-17
forum: General Help
---

### Post by ManyBeers on 2010-12-17
sudo mkdir /etc/adobe=(created a directory in /etc named Adobe)correct?

echo "OverrideGPUValidation=true" >~/mms.cfg=(created a text file in my Home directory named mms.cfg which contained the text
...OverrideGPUValidation=true...correct?

sudo mv ~/mms.cfg /etc/adobe/=(moved from my Home directory to /etc/adobe mms.cfg) correct?

These commands were part of a flash tutorial but they did not work.
So I cd'd into etc and using sudo tried rm -r /adobe. Basically I
want to undo what those 3 commands did. Any help would be appreciated

Link to tutorial=(Flash in fullscreen is choppy, completely white or crashes)
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html")

---

### Post by efflandt on 2010-12-17
But there is no /adobe (in /).  So if you already did **cd /etc**, from there you would do:

**sudo rm -r adobe**

Any path you begin with / is a path that starts at / (root).  A path relative to where you are (current directory) does NOT begin with /.

---

### Post by ManyBeers on 2010-12-17
> **efflandt said:**
> But there is no /adobe (in /).  So if you already did **cd /etc**, from there you would do:

**sudo rm -r adobe**

Any path you begin with / is a path that starts at / (root).  A path relative to where you are (current directory) does NOT begin with /.

Ok thanks. 
So this command= **echo "OverrideGPUValidation=true" >~/mms.cfg**=
created text "OverrideGPUValidation=true" which would normally show in the terminal but redirected to a file called mms.cfg which was already in my Home or created it if it didn't exist.
Is that correct.

---

### Post by trent.josephsen on 2010-12-17
Right on

---

### Post by ManyBeers on 2010-12-17
> **trent.josephsen said:**
> Right on

Thanks for the confirmation.

---

