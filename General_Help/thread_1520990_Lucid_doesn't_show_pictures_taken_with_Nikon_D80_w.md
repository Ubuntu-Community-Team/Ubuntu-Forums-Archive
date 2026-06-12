---
title: "Lucid doesn't show pictures taken with Nikon D80 when uploading to web"
date: 2010-06-30
forum: General Help
---

### Post by nicjasno on 2010-06-30
As said in the title, my Lucid install does not show any pics that have been made with the D80. They show up perfectly fine in nautilus when browsing them, or watching them, but the file upload dialog does not show them.

Even if i rename them, move to a different directory...
I also chmoded them, to no avail. Here's a screenshot:

[[img]http://thumb.phyrefile.com/n/ni/nicjasno/2010/06/30/300/Screenshot-30.png[/img]](http://www.phyrefile.com/image/view/ETEhbFgqVEWkFsrg)

Other pictures show up fine. I have no clue what could cause this.

---

### Post by justleen on 2010-06-30
Poeh...
Have you tried renaming them to .jpg? (lowecase)?

Just hunch..

---

### Post by nicjasno on 2010-06-30
Incredible, i have not tried that, and it solved it. Thanks.

But this is weird, since 9.10 was able to read the big cases just fine. Renaminig it isn't a very elegant sollution. :(

---

### Post by justleen on 2010-06-30
```
rename 's/JPG/jpg/' *.JPG 
```

Totally agree that is not very elegant, but at least is works ;)

For some reason nautilus is not "seeing" the JPG files as image in that one dialog...
What happens if you change the file type, in the right-bottom-corner? What options are listed there?

---

### Post by nicjasno on 2010-06-30
There are none. Just "files".

---

### Post by justleen on 2010-06-30
Well weird..

Just tested with picasa upload form and with a simple (dummy) html upload form.  They only show "All files" and no other filter.. But at least I do see all files, instead of none..

---

### Post by nicjasno on 2010-06-30
Is there a way to mass rename diles that are inside of folders? 

Because i have 3 years worth of pics to rename (which worked in all previous distros). And they are neatly stacked in many separate folders.

---

### Post by justleen on 2010-06-30
yea, there is..
```

find . -exec rename 's/JPG/jpg' {} \; 
```
do this inside the photo folder, or replace the "." with /the/path/to/the/pics/

---

### Post by bondo101 on 2010-06-30
Iv'e got 9.10 what picasa works with karmic . iI downloaded a version 3.0
its in the listof aplications . When you click on it it does nothing. Any ideas or did do something rong when downloading it. Please help i'm an old man who loves to get lost in the Ubuntu neighborhood.:confused:

---

### Post by nicjasno on 2010-06-30
> **justleen said:**
> yea, there is..
```

find . -exec rename 's/JPG/jpg' {} \; 
```
do this inside the photo folder, or replace the "." with /the/path/to/the/pics/

When i do this in the pics folder, i get 

```

Substitution replacement not terminated at (eval 1) line 1.

```

---

