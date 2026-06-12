---
title: "vim - CSS indentation does not work well in HTML files"
date: 2011-10-12
forum: General Help
---

### Post by kamaji792 on 2011-10-12
**vim** does not handle indenting CSS in an HTML file.  Like when I am trying to do the following:
```
<style type="text/css">
#menu {
   margin-left: 20px;
   color: #333;
}
</style>
```
Is auto formatted as:
```
<style type="text/css">
#menu {
margin-left: 20px;
      color: #333;
}
</style>
```

It looks to me like it is treating the code as if it was a 'c' switch statement with cases.
Interestingly vim under windows will handle CSS in a HTML file with no problem.

Any idea what the problem is? - k

---

### Post by deathadder on 2011-10-12
Looks like this post on stackoverflow has the same problem as you:

[http://stackoverflow.com/questions/1912132/messy-css-indentation-in-vim](http://stackoverflow.com/questions/1912132/messy-css-indentation-in-vim)

---

### Post by kamaji792 on 2011-10-13
OK after having yet another play around to try and find a solution mine is now behaving.  This is what I think I did:

Go to the vim indent directory **/etc/vim** backup the **vimrc** file in the directory and then edit the file to uncomment the lines associated with setting the indent system so they look like:
```
if has("autocmd")
  filetype plugin indent on
endif
```

I then had an additional problem where my local vimrc file [font="Courier new"]~/.vimrc[/font] had a line that set the option **set cindent** so I removed it.

Now it appears to behave correctly <phew! /> that has been giving me lots of grief - k

---

