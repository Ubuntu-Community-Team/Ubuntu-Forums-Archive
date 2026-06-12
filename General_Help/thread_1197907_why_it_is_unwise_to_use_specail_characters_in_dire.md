---
title: "why it is unwise to use specail characters in directory naming"
date: 2009-06-26
forum: General Help
---

### Post by hero1900 on 2009-06-26
i notice while i am reviewing some linux notes that it is unwise to name directories with special characters like g#a*es
why is that?? is their any good reason for that or it is just for simplicity

---

### Post by siryuhan on 2009-06-26
In a way, for simplicity. You can still access the files, but it is very annoying to do so. # means "the rest of the line is a comment" and * means "everything" in the terminal. You can imagine that playing around with these filenames could be a bit stressful...

---

### Post by lisati on 2009-06-26
Some special characters have special meanings, which is why it's best to avoid them in file names. ? means "any character".

On one computer system I used many years ago, /* at the start of a line meant "end of data" and // meant "this line's a job control instruction" - potentially confusing to the OS if you were to have C code in the input stream. Once at work, after the team had updated something in the network, I decided to check out the remote job submission system. Out of curiosity, of course, not malice or any sense of mischief. I chose the character sequence "%%" to mark the end of the stuff I wanted to run remotely. Unknown to me at the time, "%" had a special meaning to the networking software they were using, and there was a bug that caused an infinite loop, preventing other work getting through. After a bunch of comments from colleagues of the "WTF were you doing? Don't do it again!" variety, the bug was fixed.

---

### Post by hero1900 on 2009-06-27
got it thank you very much
:KS

---

### Post by niteshifter on 2009-06-27
Hi,

Every character - with the exception of / and nul (the zero byte) is legal in ext2 / ext3 file systems for naming purposes.

Having said that, there is some trickiness here. The characters * ? & < > and | have special meaning to the shell - files (directories are files) whose name has those characters must be quoted (or escaped - preceded with a \), lest the shell intercept them and do it's thing with them.

In other words:
afile* is legal, but you'd better use 'afile*' or "afile*" when referring to the file. same for b?file, must be 'b?file' or "b?file". Not using quotes: afile* will expand to all files whose names begin with afile. b?file will refer to all files whose names fit the pattern b<any character here>file.

The & tells the shell "treat everything before as a command, run it in the background". Disastrous in a shell script. 

The < > and | should also be quoted or escaped if used (don't!). They're the redirection characters (< >). The | is the pipe operator, connects the output of one program to the input of another. 

Hence the "prohibition" in Linux lore about those characters. Truth be told - it is safer not to. To do so ... there will come a day, you're in a hurry using one of the three 'deadly' commands (rm, chmod, chown) or a string of commands and you forget the quotes. Or you find some script "out there" that doesn't do a good job at guarding supplied arguments. Very bad times will follow.

It's one of nice things about Linux, being able to name things pretty much any way you want - with some care and common sense ;)

---

### Post by 3rdalbum on 2009-06-27
It can also be annoying when you put a folder fill of essential files onto a flash drive, take them to a Windows machine and then find that you can't use them because the folder's name contains a character that can't be used in Windows.

What spins me out is that NTFS supports characters in filenames that Windows doesn't! That's where this situation occurs.

---

