---
title: "Copying from an ssh location to my desktop"
date: 2006-01-24
forum: General Help
---

### Post by Eric_T on 2006-01-24
Hello

I've managed to copy files to another machine using:
scp filename username@location:folder

But could someone tell me how to get the file back to my own machine again?(I edited the file on that location, and now I need the updated version here...)
I'm probably missing something really obvious here....

Thanks!

---

### Post by alamba on 2006-01-24
man scp      

scp [-aAqQprvBCL] [-S path-to-ssh] [-o ssh-options] [-P port] [-c cipher] [-i identity]     [[user@]host1:]filename1...  [[user@]host2:]filename2

---

### Post by Eric_T on 2006-01-24
[QUOTE=alamba]man scp      

scp [-aAqQprvBCL] [-S path-to-ssh] [-o ssh-options] [-P port] [-c cipher] [-i identity]     [[user@]host1:]filename1...  [[user@]host2:]filename2[/QUOTE]

That didn't really help me much. I've read the man file, but didn't get anything out of it. I guess what I'm looking for is the host name of my own computer...?

---

### Post by kaamos on 2006-01-24
```
rsync user@server:folder/file ~/Desktop/
```

---

### Post by katu on 2006-01-24
[QUOTE=Eric_T]That didn't really help me much. I've read the man file, but didn't get anything out of it. I guess what I'm looking for is the host name of my own computer...?[/QUOTE]

You don't need the name of your computer ;-)

```
scp  username@location:folder/filename ./ 
```

./  is the indication of the current directory on your home computer. You need to specify the name and the folder on the different machine. That's all.

Cheers,
Katu

---

### Post by Eric_T on 2006-01-24
Thanks! Both of the two last solutions work. :)

---

### Post by charlieg on 2006-01-24
You can even tweak bash_completion to perform tab-completion over ssh tho I forget how (google will remember, I'm sure).

---

