---
title: "View file extensions"
date: 2009-06-26
forum: General Help
---

### Post by jpfalet on 2009-06-26
Hello,

In windows, I know how to select the option to view the file extensions...for example:

blank >> blank.txt

But where can you select this option in ubuntu?

Thank you

---

### Post by DeMus on 2009-06-26
> **jpfalet said:**
> Hello,

In windows, I know how to select the option to view the file extensions...for example:

blank >> blank.txt

But where can you select this option in ubuntu?

Thank you

You want to turn them of? Here they are standard on which makes it easier to know which file is which.

---

### Post by Tyke91 on 2009-06-26
many files don't actually have extensions.

they don't serve a purpose in linux except to tell the user what kind of file they are

---

### Post by jpfalet on 2009-06-26
> **Tyke91 said:**
> many files don't actually have extensions.

they don't serve a purpose in linux except to tell the user what kind of file they are

Oh really? Why is that?

---

### Post by Tyke91 on 2009-06-26
what a file does is decided by what it contains. Usually the first few bits of a file give information about what it actually is. The extension is just so that humans can easily tell what it does (for instance, .rc is usually a configuration text file)


another example. I could write a short script, foo
```
#!/usr/bin/python
print "This script prints a string"
```and save it with no extension, the extension for python (.py) or even .pl (perl) or .odt

if i were to call that script from the command line
```
./foo
or
./foo.py
or
./foo.pl
or
./foo.odt
depending on what its name is
```it would always do the same thing.

for example. you have a file in your home folder called ".bashrc" the '.' in front makes it a hidden file and it has no extension. This file is used to tell bash what aliases to use and other global definitions.

---

### Post by jpfalet on 2009-06-26
I see, so is that why I do not see an extension when I create a text file?

---

### Post by Tyke91 on 2009-06-26
yep. it doesn't have one unless you give it one.

---

### Post by jpfalet on 2009-06-26
And to give it an extension, is it as simple as just writing the extension directly with the file name? After I press "rename", can I just write "blank.extension"? Or do I need to give it its extension through a command in the terminal?

---

### Post by Tyke91 on 2009-06-26
an extension is just part of the name. Sometimes they are useful (for instance, the text editor vim can use the extension of a file to determine how to highlight it)

rename will work fine.

---

### Post by jpfalet on 2009-06-26
Ok, and finally, talking about vim, I wanted to know if vim surpasses gedit (which comes with ubuntu).

---

### Post by Tyke91 on 2009-06-26
I love vim (and gvim) and use them instead of gedit.

learning curve is tougher, but in the end you can edit an entire program quickly and without even touching the mouse :)


btw - to all you EMACS fanboys, we claim this one, take your five finger salute and go find someone else!

---

### Post by synapsys on 2009-06-26
Just remember, learn how to quit without saving before opening vim.....

---

### Post by jpfalet on 2009-06-26
Well thanks to you all. You have been of great help.

:)

---

### Post by Tyke91 on 2009-06-26
hehe yes. just to save you the work

:q!    quits without saving
:w    saves (write)
:wq  (save and quit)

press escape and then the colon (:) key to write those

---

### Post by jpfalet on 2009-06-26
and what about ZZ? doesn't that do the same job to save?

---

### Post by Tyke91 on 2009-06-26
to be honest, there are so many ways to do things that i just stick with the ones that are simple.

ZZ requires using shift and hitting z twice... w and q are right next to each other, so i find it easier to type.

---

### Post by blueridgedog on 2009-06-26
As an aside, I find that vim in ubuntu, while in insert mode, using the arrow keys causes A or B or C or D to be inserted followed by a new line.  To move the cursor around, I have to escape out of insert mode.  This is not how I am used to vim working...any tweaks to get back to being able to move the cursor in insert mode with my arrow keys?

---

### Post by geirha on 2009-06-26
> **blueridgedog said:**
> As an aside, I find that vim in ubuntu, while in insert mode, using the arrow keys causes A or B or C or D to be inserted followed by a new line.  To move the cursor around, I have to escape out of insert mode.  This is not how I am used to vim working...any tweaks to get back to being able to move the cursor in insert mode with my arrow keys?

Sounds like you are running vim-tiny which runs in vi-compatible mode. Install the [vim](vim) package, then to enable syntax highlighting and similar: ```
sudo vim /etc/vim/vimrc
```

Or alternatively copy /etc/vim/vimrc to ~/.vimrc and edit that instead.

---

### Post by blueridgedog on 2009-06-26
Ahh...now that better.  Thanks.

---

