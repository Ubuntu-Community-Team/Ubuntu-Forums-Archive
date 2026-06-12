---
title: "grep question"
date: 2010-06-17
forum: General Help
---

### Post by nerdy_kid on 2010-06-17
Im trying to scan all files in a folder for the line X-Ubuntu-Gettext-Domain=* but not pick up files that have something before that line, e.g. #X-Ubuntu-Gettext-Domain=something.  I cant get grep to do it!  help please?  (ultimatly i want to append the "#" to all lines that dont have it)

---

### Post by quadproc on 2010-06-17
> **nerdy_kid said:**
> Im trying to scan all files in a folder for the line X-Ubuntu-Gettext-Domain=* but not pick up files that have something before that line, e.g. #X-Ubuntu-Gettext-Domain=something.  I cant get grep to do it!  help please?  (ultimatly i want to append the "#" to all lines that dont have it)
I do not really understand what you are trying to do, but I think that you want discard all file names that occur before you encounter a target expression.  If so, _grep_ will not be useful; instead, I suggest using _awk_.  _Awk_ works well for such tasks.

If you know _perl_ then that may be a better choice.

quadpoc

---

### Post by nerdy_kid on 2010-06-17
i want to find all files in a folder that have only the phrase X-Ubuntu-Gettext-Domain=* but NOT the phrase #X-Ubuntu-Gettext-Domain=*
I dont know how to use awk and the man page looks very complicated :(

---

### Post by quadproc on 2010-06-18
> **nerdy_kid said:**
> i want to find all files in a folder that have only the phrase X-Ubuntu-Gettext-Domain=* but NOT the phrase #X-Ubuntu-Gettext-Domain=*
I dont know how to use awk and the man page looks very complicated :(
Please don't be intimidated by awk - it actually uses a very simple concept: each line of an awk program has a pattern part and an action part.  If the pattern part matches the line of input that it just read then the action is performed.  Of course, awk has lots of bells and whistles so it can seem overwhelming but you don't need much to solve your problem.

I suggest something like this:
```
cd the_directory_of_interest
ls X-Ubuntu-Gettext-Domain=* > flist
```Copy the following code into a file called awkpgm:
```
BEGIN {s="#Xubuntu-gettetxt-domain="}

!($0 ~ s) {printf "%s\n",$0}
```Then run the awk program using
```
gawk -f awkpgm flist
```This will send a list of the files to standard output; you can redirect that if you like.

---

### Post by nerdy_kid on 2010-06-19
thanks :)

---

### Post by NevynH on 2011-02-19
> **quadproc said:**
> I do not really understand what you are trying to do, but I think that you want discard all file names that occur before you encounter a target expression.  If so, _grep_ will not be useful; instead, I suggest using _awk_.  _Awk_ works well for such tasks.

If you know _perl_ then that may be a better choice.

quadpoc
Oh come on...

This is a really simple regular expressions question. The OP wants to find a match at the beginning of the line - i.e.

grep -i "^X-Ubuntu-Gettext-Domain" *

No awk required.

---

