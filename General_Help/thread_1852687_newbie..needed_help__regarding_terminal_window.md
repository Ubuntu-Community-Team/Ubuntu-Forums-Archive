---
title: "newbie..needed help  regarding terminal window"
date: 2011-09-30
forum: General Help
---

### Post by sureshmani on 2011-09-30
Hi, am new to linux..i tried to access a subdirectory in terminal but am getting error here are the commands that i used..
pwd - it showed my current directory as "suresh@ubuntu:~$"
ls  - it showed 
               Desktop
               Documents
               Downloads
now i ran cd /desktop,but it didnt worked got error as no such directory exists.

please help me out.

---

### Post by haqking on 2011-09-30
> **sureshmani said:**
> Hi, am new to linux..i tried to access a subdirectory in terminal but am getting error here are the commands that i used..
pwd - it showed my current directory as "suresh@ubuntu:~$"
ls  - it showed 
               Desktop
               Documents
               Downloads
now i ran cd /desktop,but it didnt worked got error as no such directory exists.

please help me out.

Linux is case senstive, as you can see from your ls the ouptu has capital letters at the beginning.

so should be

cd Desktop

not 

cd desktop

and dont do a /Desktop because that indicats that Desktop is in the root and it isnt it is in ~

---

### Post by seawolf167 on 2011-09-30
Yup, as said - it is case sensitive.

Also note that if you use [TAB] competition, if nothing autocompletes for you, then something is spelled wrong or in the wrong case.

i.e.

```
cd desk[TAB]
```

will yield no results, but

```
cd Desk[TAB]
```

will autocomplete to

```
cd Desktop
```

---

### Post by haqking on 2011-09-30
> **seawolf167 said:**
> Yup, as said - it is case sensitive.

Also note that if you use [TAB] competition, if nothing autocompletes for you, then something is spelled wrong or in the wrong case.

i.e.

```
cd desk[TAB]
```

will yield no results, but

```
cd Desk[TAB]
```

will autocomplete to

```
cd Desktop
```


also if you hit tab once and nothing shows, then hit it again and it will show your options of what it thinks you may be looking for if its valid input such as capital D

---

### Post by sureshmani on 2011-09-30
Hi,Thanks for your help guys..its working..:popcorn:

---

### Post by haqking on 2011-09-30
> **sureshmani said:**
> Hi,Thanks for your help guys..its working..:popcorn:

cool glad we could help.

remember to mark the thread as solved using the thread tools menu.

cheers

---

