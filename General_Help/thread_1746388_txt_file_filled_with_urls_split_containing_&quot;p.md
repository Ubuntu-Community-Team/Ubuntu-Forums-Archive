---
title: "txt file filled with urls split containing &quot;post&quot;"
date: 2011-05-01
forum: General Help
---

### Post by webcabbie on 2011-05-01
So I have a text file that is 183 mb. I want to split off all of the urls that contain the word "post" in the url line. 

This is an example of one of the urls that contain what I want. I need another simple command to put into the terminal that is idiot proof. The file is on my desktop and named url.txt

---

### Post by manzdagratiano on 2011-05-01
How about this fairly simple command in the desktop (Open a terminal. Then 'cd Desktop'):

```
cat url.txt | grep post > url2.txt
```

This should do the trick, and the file size is not too huge to be handled. 'grep' will give all the lines that have 'post' in them. The trouble will be if you do **NOT** have all the urls in separate lines. That can also be handled but will require more complicated code.

---

### Post by webcabbie on 2011-05-01
michael@michael-desktop:~$ cd Desktop
michael@michael-desktop:~/Desktop$ cat url.txt | grep post > url2.txt
michael@michael-desktop:~/Desktop$ 

It did its thing but the file is empty..

I am guessing this might not be working because when I try to open the file ubuntu doesnt like the encoding and wont open it?

---

### Post by webcabbie on 2011-05-01
manz 

I split it into multiple files and put them in a folder called urlfolder
can you tell me how to run that command for the whole folder so i dont have to do it one at a time?

---

### Post by Doug S on 2011-05-02
I think this might do what you want:
```
cd urlfolder
grep post * >has_post.txt
```Note that grep is case sensitive so it will only find lines with "post", not "Post" or "POST" or pOst" ... If you want to ignore case add the -i switch.

---

