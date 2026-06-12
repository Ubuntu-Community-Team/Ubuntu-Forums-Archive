---
title: "Pdftk"
date: 2009-07-08
forum: General Help
---

### Post by kd0afk on 2009-07-08
There is a pdftk thread already but it is in the archives and I can't post on it.
I am wanting to combine (merge) several pdf's into one pdf. I downloaded PDFTK but I can't seem to get it to work right.
My two PDF files are on my desktop and following the instructions (which said nothing about where to put the pdf files or which directory to be it) I tried to combine two files and here is my terminal return:

[COLOR=Red]shawn@HAL:~$ pdftk Singer500-503ServiceManual-1-23.pdf Singer500-503ServiceManual-24-46.pdf Singer 500 service manual cat output 123.pdf
Error: Failed to open PDF file: 
   Singer500-503ServiceManual-1-23.pdf
Error: Failed to open PDF file: 
   Singer500-503ServiceManual-24-46.pdf
Error: Failed to open PDF file: 
   Singer
Error: Failed to open PDF file: 
   500
Error: Failed to open PDF file: 
   service
Error: Failed to open PDF file: 
   manual
Errors encountered.  No output created.
Done.  Input errors, so no output created.
shawn@HAL:~$ 


[COLOR=Black]I am guessing that I am not doing this right. Can someone help me out here?[/COLOR]
[/COLOR]

---

### Post by michy99 on 2009-07-08
If your files are on your desktop, you need to change to that directory before you use the command. Also, if there are spaces in the name of a file, you need to enclose it in quote marks.```
cd ~/Desktop
pdftk Singer500-503ServiceManual-1-23.pdf Singer500-503ServiceManual-24-46.pdf 'Singer 500 service manual' cat output 123.pdf
```

---

### Post by kd0afk on 2009-07-08
It didn't work so well. 


```
shawn@HAL:~$ cd ~/Desktop
shawn@HAL:~/Desktop$ pdftk Singer500-503ServiceManual-1-23.pdf Singer500-503ServiceManual-24-46.pdf 'Singer 500 service manual' cat output 123.pdf
Error: Failed to open PDF file: 
   Singer500-503ServiceManual-1-23.pdf
Error: Failed to open PDF file: 
   Singer500-503ServiceManual-24-46.pdf
Error: Failed to open PDF file: 
   Singer 500 service manual
Errors encountered.  No output created.
Done.  Input errors, so no output created.
shawn@HAL:~/Desktop$ 

```

At the very end of the code, what does "cat output 123.pdf" mean?

---

### Post by Chronon on 2009-07-08
The proper syntax to join two files is: 
```
pdftk in1.pdf in2.pdf cat output out1.pdf
```

cat tells the program to concatenate the two input files.  output tells the program to write the output to out1.pdf.  Change in1.pdf, in2.pdf and out1.pdf to match your needs.

However, the program is failing to find/open the files in the current directory.  Are they in the current directory or not?  If you do a "ls" does it show you the desired input files?  They need to be in the current directory or else you need to supply the path to where they are located.

---

### Post by kd0afk on 2009-07-08
Um yea, the files weren't there when I tried it :rolleyes:. It worked for me once I gave pdftk something to work with.
Thanks for the help.

---

### Post by Chronon on 2009-07-08
I'm glad I could help.    :)

---

### Post by tazztone on 2009-11-27
to merge you can also use pdfsam [http://www.pdfsam.org]("http://www.pdfsam.org/")

---

