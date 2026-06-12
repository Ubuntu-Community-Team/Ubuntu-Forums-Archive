---
title: "minimise and maximise on left hand side"
date: 2010-07-23
forum: General Help
---

### Post by groeswenphil on 2010-07-23
Hi, 
Just upgraded Ubuntu.....now I find that the minimise and maximise icons are on the left hand side. Is there a way to get them to the right hand side?

Phil

---

### Post by sisco311 on 2010-07-23
Customize a theme on which the buttons are on the right side:
[http://wojox.homelinux.org/?p=65](http://wojox.homelinux.org/?p=65)

---

### Post by prakhar_garg009 on 2010-07-23
which version you are using

---

### Post by Vaphell on 2010-07-23
open terminal, run:
gconf-editor
in apps->metacity->general change button_layout variable to :minimize,maximize,close

:stuff = on the right, stuff: = on the left
of course you can put buttons in whatever order you want

---

### Post by NTHQ on 2010-07-23
You can use Ubuntu Tweak to change it.

---

### Post by sisco311 on 2010-07-23
EDIT: 

Or use the CLI :shock: to create a new custom theme with the buttons on the right:
```
mkdir -p ~/.themes/ && \
cp -r /usr/share/themes/Ambiance ~/.themes/Ambiance-right && \
sed -i \
-e 's/^Name.*/Name=Ambiance-right/' \
-e 's/ButtonLayout.*/ButtonLayout=:minimize,maximize,close/' \
~/.themes/Ambiance-right/index.theme && \
gconftool-2 --type string --set /apps/metacity/general/theme "Ambiance-right"
```

---

### Post by warfacegod on 2010-07-24
Another option is to install Ubuntu Tweak and change it from there. Tweak also has allot of other useful functions. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by stuartwood89 on 2010-07-24
> **Vaphell said:**
> open terminal, run:
gconf-editor
in apps->metacity->general change button_layout variable to :minimize,maximize,close

:stuff = on the right, stuff: = on the left
of course you can put buttons in whatever order you want

This is the best way to do this.  I did pretty much the same, but a little different:

Hit Alt+F2 to open run dialogue.
Type 'gconf-editor' and hit Enter.
On the left hand side, go into 'apps'.
Then metacity.
Then general.
Once you've clicked 'general', a list of properties should appear on the right hand side, find 'button_layout' and double click on it.
In the value box, delete what's already in there and replace it with 'menu:maximize,minimize,close'

That will fix that problem. and like Vaphell said, you can change the order of the buttons simply by reordering the words.  As long as 'menu:' is on the left, the buttons will be on the right.

---

### Post by groeswenphil on 2010-07-25
Ubuntu Tweak fixed the problem. Easy to install and figure out what to do. Thanks :O)
Phil

---

### Post by sisco311 on 2010-07-25
Cool!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

