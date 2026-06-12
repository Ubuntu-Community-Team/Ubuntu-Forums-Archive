---
title: "Simple Script help...listing files..."
date: 2009-10-08
forum: General Help
---

### Post by x C0MMAND0 x on 2009-10-08
I have a folder with 1,000+ files in it.  I want to have a list of all of the files so I can have them in a text file.  When I go to terminal, and run "ls", it seems to be cutting off the list.  I see the last half or so of the files.

Is there a way to either have ls display ALL of the information, or a simple script that can do this?

---

### Post by eric3_14159 on 2009-10-08
What you want to do is redirect the output of ls into a file. This can actually be done with any command at all by using the > symbol.

If you put > and then a filename at the end of any command you type at the prompt, all of the output will be written to that file instead of being shown. so,
```
ls > file_list
```
should do what you want. Most likely, ls was only printing about half the files because your terminal was truncating the output. That shouldn't be a problem in the file.

Oh, if you just want to be able to see all of the output in the terminal, you can use
```
ls | less
```
This will buffer all the output and you can use the arrow keys to look up and down the list, space to page down, type a / and then a pattern to search, and q to quit.

Hope this helps!

---

### Post by x C0MMAND0 x on 2009-10-08
That is EXACTLY what I was looking for.  Thank you very much!

---

