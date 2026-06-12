---
title: "how to remove file ?"
date: 2012-05-08
forum: General Help
---

### Post by winzip on 2012-05-08
In my **/home/user**  folder I have many files.

I want to remove files  whose name contains text "spring"   and has file extension ".jar"  

I want to print name of files being removed in the console so that I can track what are the files are being deleted.

[COLOR=Blue]** Whats the command ?**[/COLOR]



Here are sample file names which the command should be capable to delete.
[U]
Example:[/U]

spring.jar  //delete
cas-spring.jar  //delete
org.springframework.jar  //delete

System: Ubuntu Server 10.04 OS (no GUI)

---

### Post by papibe on 2012-05-08
Hi winzip.

You can use this expression: *spring*.jar

To list all those files:
```
ls *spring*.jar
```
and, to actually remove them:
```
rm -rf *spring*.jar
```
Hope it help.
Regards.

---

### Post by winzip on 2012-05-08
> **papibe said:**
> Hi winzip.

You can use this expression: *spring*.jar

To list all those files:
```
ls *spring*.jar
```and, to actually remove them:
```
rm -rf *spring*.jar
```Hope it help.
Regards.

OK. Thanks. But your command will not print  actual file names getting deleted in the console ...can you please upgrade your command so that it can also print the file names being deleted ?


By the way , Why do you need **rf**  here ?   all files are in same directory .

---

### Post by Bolverksson on 2012-05-08
If ownership is an issue, just add sudo befor the comand.

---

### Post by papibe on 2012-05-08
> **winzip said:**
> OK. Thanks. But your command will not print  actual file names getting deleted in the console ...can you please upgrade your command so that it can print the file names being deleted ?
Sure.

For printing what's going on use the verbose option:
```
rm -v *spring*.jar
```
You can also add a confirmation question (interactive option):
```
rm -i *spring*.jar
```

> **winzip said:**
> Why do you need **rf**  here ?   all files are in same directory .
-f is to force (don't ask question)
-r is for recursive. In this case it may be not necessary, unless the are also directories you want to delete.

I hope that helps, and tell us if you have more questions.
Regards.

---

### Post by winzip on 2012-05-08
Thanks . That was very much helpful.

I am planning to use this ..

```
rm -vr *spring*.jar
```
v = verbiage to print whats going on

r= recursive ... good have this recursive.


Shall I write  ...

rm -[COLOR=Blue]**vr**[/COLOR] *spring*.jar

Or

rm -[COLOR=Blue]**rv**[/COLOR] *spring*.jar

Does the ordering matter here ?

---

### Post by papibe on 2012-05-08
> **winzip said:**
> Does the ordering matter here ?

:) Not in this case.
Regards.

---

