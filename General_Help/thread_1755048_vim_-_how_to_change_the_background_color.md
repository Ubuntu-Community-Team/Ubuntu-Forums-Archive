---
title: "vim - how to change the background color?"
date: 2011-05-10
forum: General Help
---

### Post by agrayray on 2011-05-10
OK, I realize this more of vim question than an Ubuntu one but figured this would make more sense here...

I really love my purple/transparent terminal window and do many things in it that I love with the color scheme of my terminal window (its default) with one exception...

I started to use vim recently to code with this and the purple background does not mesh well with the color scheme for vim.  For ex, all my #include's show up as purple also and almost makes them invisible to me....and I like the color coding in vim...

what would be ideal for me is to have my background white when using vim only and when I exit out of vim, go back to my normal color scheme in shell window.  

Anyone know how to do this?

PS - I have tried changing the set background=light and dark and not happy with that either, again would just to have a white background while using vim only.

---

### Post by TeoBigusGeekus on 2011-05-10
Add this line
```
hi normal   ctermfg=black  ctermbg=white
```
in your ~/.vimrc file.

---

### Post by agrayray on 2011-05-10
Thanks for the reply..however still need help sorry...

I don't have a ~/.vimrc file.   I do have a .viminfo thats pretty much it...I tried setting this here and didnt work furthermore it looks this file gets overwritten when I exit vim (it contains history and such)...

should I create a .vimrc or do something else....on Ubuntu 10.04 GNOME btw using vim that was installed via the Ubuntu Software Center.

?

Thanks again in advance!

---

### Post by TeoBigusGeekus on 2011-05-10
Create a .vimrc file and put the line in it. Restart vim and tell us how it went.

---

### Post by WorMzy on 2011-05-10
Without a .vimrc file you may as well be using vi. I suggest that you run through the vimtutor program:

```
vimtutor
```

It'll give you some examples of what to put into your .vimrc file to enable some of vim's features.

---

### Post by agrayray on 2011-05-10
Thanks for the replies guys...putting that in the .vimrc file worked.  I wouldnt say it quite looks white (attached a screenshot if you want to see) in fact im fooling around with the colors and seems to me white looks same as lightgray but oh well much better improved...if you have any final tip on getting the same 'white' for ex that I get in gedit that would be great to have otherwise I can live with this OK...

thanks again for the help and yes will check out the vimtutor...

!!!

---

### Post by WorMzy on 2011-05-10
The colours depend on your colour scheme, which you can set in the profile preferences.

---

