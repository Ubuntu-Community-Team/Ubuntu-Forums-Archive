---
title: "Exclude file from terminal command."
date: 2010-07-12
forum: General Help
---

### Post by pato wlmc on 2010-07-12
Well i downloaded a program with many .deb files ( At least 15 )  so i wanna execute them all trough the terminal so i typed

```
patowlmc@patowlmc-desktop:~$ cd /home/patowlmc/Downloads/i386

patowlmc@patowlmc-desktop:~/Downloads/i386$ sudo dpkg -i *.deb

Readme.deb: command not found
```

As you can see all files in the folder are .deb packages, but one: The Readme file, wich is a text file.

I know I just have to move the file to somewhere else, and everything should work, but i wanna know if there's a command for excluding a file or something.

I hope i explained my self.

P.D. I totally trust the program, so don't worry about so many .deb files.

P.D.2 Sorry for the bad english jeje =p

---

### Post by Telengard C64 on 2010-07-12
If it is the only .deb file in the directory which begins with capital letter R then you can do this:

```
dpkg -i [^R]*.deb
```

Otherwise you may need to do something like this:

```
for i in *.deb ; do if [ "$i" != "Readme.deb" ] ; then dpkg -i "$i" ; fi ; done
```

There are probably many other ways.

---

### Post by gadolinio on 2010-07-13
Sorry, I don't get it: why does the readme file end in .deb? Why not change it to .txt?

---

### Post by Lampi on 2010-07-13
try this:

```
file /home/patowlmc/Downloads/i386/Readme.deb
```
if file shows sth like this:
```
Readme.deb: Debian binary package
```
then this indeed is a debian installer package - and there's sth wrong with it, otherwise it would install fine

It's more likely you'll get sth similar to this output:
```
Readme.deb: ASCII text
```
and you're good to rename it to sth better than Readme.deb - I recommend Readme.txt or Readme.debian is also quite common, just never call sth .deb if it is not a debian installer package :)

---

### Post by Telengard C64 on 2010-07-13
The option to move (aka rename) the file was rejected in the OP. The subject line and OP both state that an acceptable solution will *exclude* certain files.

Another possible solution occurs to me now. This should work if all the *.deb files you want to install are in a single folder:

```
find -maxdepth 1 -name '*.deb' -not -name 'Readme.deb' -exec dpkg -i {} +
```

---

### Post by gadolinio on 2010-07-13
> **Telengard C64 said:**
> The option to move (aka rename) the file was rejected in the OP. The subject line and OP both state that an acceptable solution will *exclude* certain files.


You're right. I was asking because I don't fully understand the situation, I mean why the readme file had the .deb extention in the first place.

---

### Post by gadolinio on 2010-07-13
> **Telengard C64 said:**
> 
```
for i in *.deb ; do if [ "$i" != "Readme.deb" ] ; then dpkg -i "$i" ; fi ; done
```

+1.
This should do the job.

---

### Post by Telengard C64 on 2010-07-13
> **gadolinio said:**
> why the readme file had the .deb extention in the first place.

TBH I was wondering the same thing. Only pato wlmc could answer the question. I do think there is more to the problem than we can guess.

---

### Post by sisco311 on 2010-07-13
```
sudo dpkg -i !(Readme.deb)
```

EDIT: Sorry for posting just a command. See the explanation below.

---

### Post by Telengard C64 on 2010-07-13
> **sisco311 said:**
> ```
sudo dpkg -i !(Readme.deb)
```

Nifty! I've never used that one before. According to The GNU Bash Reference Manual:

> `!(PATTERN-LIST)'
     Matches anything except one of the given patterns.

:D

---

### Post by gadolinio on 2010-07-13
> **sisco311 said:**
> ```
sudo dpkg -i !(readme.deb)
```
great!

---

### Post by sisco311 on 2010-07-13
> **Telengard C64 said:**
> According to The GNU Bash Reference Manual:

> `!(PATTERN-LIST)'
Matches anything except one of the given patterns.

:D

D'oh! :)

For those who have difficulties using man pages:
```
man bash | less +/"If the extglob shell"
```
:evil:

---

### Post by Telengard C64 on 2010-07-13
why so mad sisco311?

---

### Post by sisco311 on 2010-07-13
> **Telengard C64 said:**
> why so mad sisco311?

I'm mad at me, because I made a mistake, I posted just a command without explaining it.

---

### Post by Telengard C64 on 2010-07-13
Don't be too hard on yourself. I've done the same.
;)

---

### Post by gadolinio on 2010-07-13
> **sisco311 said:**
> I'm mad at me, because I made a mistake, I posted just a command without explaining it.
Yes, I noticed that.. It was strange :P

---

