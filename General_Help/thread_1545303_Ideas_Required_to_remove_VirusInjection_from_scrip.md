---
title: "Ideas Required to remove Virus/Injection from script files"
date: 2010-08-03
forum: General Help
---

### Post by ranatanveer on 2010-08-03
Hi Everyone

I need to remove virus/injections from hindered of files from my web server, infected due to virus/injection.

i am working on simple idea.

1. script ask pattern as input from user OR pattern as input file.
2. script ask the specific path as input OR or list of infected file to be provided to remove pattern from path/list files.
3. find awk sed to remove pattern.

is there any better way ?

I can write bash script, can community help me in to give ideas about the outline of my script ?

i need just ideas not the code.

---

### Post by David Andersson on 2010-08-03
> **ranatanveer said:**
> 
I need to remove virus/injections from hindered of files from my web server, infected due to virus/injection.


Are you sure that you know what the virus looks like in all types of files it might have invaded? In .txt, .htm, .php...?  Are you sure it has not invaded non-text-files, like executables, databases?

> **ranatanveer said:**
> 
is there any better way ?


It seems much safer to restore from a backup, obviously.

**Anyway**, to answer the specific question. You can search and replace patterns in hundreds of files in one sweep with e.g. perl and sed.

```
perl -i 's/FROM/TO/g' *.txt *.htm
```

```
sed -i 's/FROM/TO/g' *.txt *.htm
```

The -i flag tells perl and sed to save the changed file in the same filename as it read from. With -i~ they will also save the original files in filenames ending with "~".

The "FROM" part in the examples above are "regular expressions". Do you need help with their syntax?

---

### Post by lisati on 2010-08-03
Here's a word from someone who has done a small amount of reading over the years: [Polymorphic]("http://en.wikipedia.org/wiki/Polymorphic_code").

Rough translation: some malware is sneaky. It can change its appearence in a way that makes the task of recognizing it more difficult.

I'd be inclined to have a backup of your important data and keep it somewhere that the script kiddies can't touch it. Then if you suspect that something nasty has happened, the task of recovering a healthy production environment is made a lot easier.

---

### Post by ranatanveer on 2010-08-04
> Are you sure that you know what the virus looks like in all types of files it might have invaded? In .txt, .htm, .php...?  Are you sure it has not invaded non-text-files, like executables, databases?


Yes, i have lot of patterns already in file, and some times, we can dig out simply keen searching in few files specially index.php style.css etc.

> It seems much safer to restore from a backup, obviously.


obviously if backup is available :)

> **Anyway**, to answer the specific question. You can search and replace patterns in hundreds of files in one sweep with e.g. perl and sed.

```
perl -i 's/FROM/TO/g' *.txt *.htm
```

```
sed -i 's/FROM/TO/g' *.txt *.htm
```

The -i flag tells perl and sed to save the changed file in the same filename as it read from. With -i~ they will also save the original files in filenames ending with "~".



Thanks  for the code tips.

> The "FROM" part in the examples above are "regular expressions". Do you need help with their syntax?


No. thanks a lot.

---

