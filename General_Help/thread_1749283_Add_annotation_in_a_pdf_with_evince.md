---
title: "Add annotation in a pdf with evince"
date: 2011-05-04
forum: General Help
---

### Post by iris-n on 2011-05-04
This is an answer in search of a question. I hope, though, that it will be useful.

In Natty 11.04, evince now has the much anticipated feature of reading and adding annotations to pdf files.

What motivates this post is that although it is clearly stated in the evince release notes that it can add notes, I couldn't figure out how to do it.

Search the web, I found a [video]("http://carlosgc.linups.org/2010/Jul") from the developer who added the feature explaining how to use it.

So the magic is: View -> Side Pane (if it's not already activated). Click on thumbnails, a drop down menu will appear. Last option, annotations. Two tabs, List and Add. Click on add, and then the pencil. Now just click where you want to add the note, and voilà.

I can't figure out why would they make it so hidden. But, trollish or not, the feature is finally here!

---

### Post by matthewbpt on 2011-05-04
-------------------------------------------------------------------
EDIT: Whoops I misread your post ... you've already got it working
-------------------------------------------------------------------
Try installing poppler-data and poppler-utils

```
sudo apt-get install poppler-data poppler-utils
```

Apparently annotations require this but it isn't installed by default, note though that I haven't tested this as a solution because I don't have Natty installed atm.

---

### Post by iris-n on 2011-05-04
Yes, I already got it working, and I'm on Natty, not Maverick.

However, I do have another machine with Maverick (don't want to upgrade, machine too critical), and I'd like to make it work with annotations.

I did try your command, it didn't work. I think the problem lies with the version of libpoppler Maverick shipped. It is 0.14, and annotations require 0.15.

If you now an easy way to install 0.15 I'd be happy.

---

### Post by mike555 on 2011-05-04
You could install " Xournal " ,it annotates very well .

---

### Post by dre12b on 2011-06-16
Is there a keyboard or menu shortcut to add an annotation in Evince? I NEED the feature, but start grumbling every time I find it multiple mouse clicks away.

---

### Post by ArielSonique on 2011-07-06
Hi, I am on Debian with XFCE. Could you please tell me which version of Evince implements this annotation feature?

EDIT: I just received a reply from the creator that it is implemented in Debian from versions 3.x (still in experimental repository). 

Now that I can annotate, how can I delete these annotations? And can I add highlights?

---

### Post by m5taha5m on 2011-10-26
Hi,
How can delete an annotation in evince?

---

