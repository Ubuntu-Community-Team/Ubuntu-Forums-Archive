---
title: "Recursively copy from directory to another directory"
date: 2010-03-23
forum: General Help
---

### Post by killthemyth on 2010-03-23
Hi every1, 

I'm facing a little trouble with copying a .txt file(only) from a directory and subdirectory to another directory. -R command don't work I think if I want to do this, since I don't want to copy subdirectory. 

How to do this ??

Thnks in advance...

---

### Post by nothingspecial on 2010-03-23
If using cp, try -r (lower case)

If you want to see it copying use -v (verbose)

```
cp -rv directory destination
```

-r is the usual recursive argument (notable exceptions chmod & chown use (uppercase) -R)

---

### Post by killthemyth on 2010-03-23
> **nothingspecial said:**
> If using cp, try -r (lower case)

If you want to see it copying use -v (verbose)

```
cp -rv directory destination
```

-r is the usual recursive argument (notable exceptions chmod & chown use (uppercase) -R)
Hi nothingspecial,

I don't think it will work in my case. Let me elaborate me first. 
Let say I have d1 directory in my home folder in which tere is 1.txt file and d2 directory. and in d2 directory there is 2.txt and d3 directory which contain 3.txt. 

How to copy all and only .txt file from d1 and its subdirectory to another folder into let say d4 of home directory..

According to you it shld be 
cp -r d1/*.txt d4/

m i rite.. if this is the case thn it is jst copying 1.txt to d4 rest is left uncopied.

Hope I made my point clear. How to do this ??

---

### Post by bodhi.zazen on 2010-03-23
> **killthemyth said:**
> Hi nothingspecial,

I don't think it will work in my case. Let me elaborate me first. 
Let say I have d1 directory in my home folder in which tere is 1.txt file and d2 directory. and in d2 directory there is 2.txt and d3 directory which contain 3.txt. 

How to copy all and only .txt file from d1 and its subdirectory to another folder into let say d4 of home directory..

According to you it shld be 
cp -r d1/*.txt d4/

m i rite.. if this is the case thn it is jst copying 1.txt to d4 rest is left uncopied.

Hope I made my point clear. How to do this ??

As your needs get more complex, it helps to learn to use find =)

[http://content.hccfl.edu/pollock/unix/findcmd.htm](http://content.hccfl.edu/pollock/unix/findcmd.htm)

---

### Post by nothingspecial on 2010-03-23
> **killthemyth said:**
> Hi nothingspecial,

I don't think it will work in my case. Let me elaborate me first. 
Let say I have d1 directory in my home folder in which tere is 1.txt file and d2 directory. and in d2 directory there is 2.txt and d3 directory which contain 3.txt. 

How to copy all and only .txt file from d1 and its subdirectory to another folder into let say d4 of home directory..

According to you it shld be 
cp -r d1/*.txt d4/

m i rite.. if this is the case thn it is jst copying 1.txt to d4 rest is left uncopied.

Hope I made my point clear. How to do this ??

Do not just copy and paste this command

If the only .txt files in d1 d2 d3 are the ones you want to copy into d4 then

```
find ./ -name '*.txt' -exec cp '{}' ./d4 \;
```

where you are in d1 and d2 d3 & d4 are all in d1. Change d4 for the actual name.

Type man find to try to understand this before you do it. If I haven`t understood you and you do it wrong this could mess things up big time

---

### Post by killthemyth on 2010-03-23
Hi nothingspecial, 

I'm n00b to linux ...wat I want I got it from ur help. Jst need to ask u what does this line do 

-exec cp '{}' ./d4 \;

after the find command ??

---

### Post by nothingspecial on 2010-03-24
> **killthemyth said:**
> Hi nothingspecial, 

I'm n00b to linux ...wat I want I got it from ur help. Jst need to ask u what does this line do 

-exec cp '{}' ./d4 \;

after the find command ??

-exec = execute or do

cp = copy

'{}' = all the files find has found

./d4 = . means where you are in the file system, in this case d1 so it means d1/d4

\; ends the command

---

