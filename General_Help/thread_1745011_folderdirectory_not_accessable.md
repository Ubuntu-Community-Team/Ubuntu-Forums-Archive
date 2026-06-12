---
title: "folder/directory not accessable"
date: 2011-04-30
forum: General Help
---

### Post by rsnow on 2011-04-30
I have a folder/directory that I can find and see its contents by browsing but when I try to access it by the terminal, I get the message that there is no such directory. I have been very careful to type the name exactly as shown in the browser window; I have even tried copy/paste to be sure the name is correct. When I look at the properties, it says the owner is "nobody". But I can't change anything or even delete it because I can't access it. 

When I right click on it in the browser, the 'rename' and 'move to trash' functions are blacked out.

Can someone please tell me what is causing this or what I can do to access or remove this? 

I have tried 'rm', 'rmdir', 'rm -rf', 'rm -R', and 'rmdir --ignore' commands. The folder was transferred in from another machine and its name does not include the "_" between words. I mention this because  I have gotten the return message naming each word and saying it is not a file or directory.

---

### Post by oldos2er on 2011-05-01
And its name is...?

---

### Post by idoitprone on 2011-05-01
does the directory has a space is it?

then you need to add quotes

```
ls whatever
words1 word2
cd word1 word2
no such directory
cd "word1 word2"
pwd
whatever/word1\ words2
```

---

### Post by rsnow on 2011-05-04
Sorry to take so long in getting back to this. The real world keeps interrupting. I will try using the quotes and see what happens.

---

### Post by rsnow on 2011-05-06
Yes, the quotation marks seem to do the trick. Thanks!

I am on page 482 in the book on using the command line and I don't recall seeing that information in what has been covered up to this point. Anyway, thanks again. One more frustration removed.

---

