---
title: "Bash script problem. Advice needed"
date: 2006-03-20
forum: General Help
---

### Post by PsYcHo_SiB on 2006-03-20
Hi,

I recently created on ubuntu 5.10 a script that delete the 4 oldest files from a directory. Somehow I have problems with filenames with spaces in it. I would need some help on the syntax of the script.
Code:

cd /var/www/archive/files/XYZ
rm `ls *.avi -1t  | tail -4`
cd /var/www/archive/files/ZYX
rm `ls *.avi -1t  | tail -4`

Thanks in advance !
- SiB -

---

### Post by engla on 2006-03-20
Okay. It's not always easy to do this.. the problem is that you will have an output like
Movie file.avi
and rm will think that this is two files "Movie" and "file.avi". This is how I would solve this:

```
 ls *.avi -1t | tail -4 | tr \\n \\0 | xargs -0 rm

```

Okay, what does this do?
```
 ls *.avi -1t | tail -4
```
This is your code, it gives the list of files to delete.

```
 | tr \\n \\0
```
This is a strange thing. "tr" replaces occurances of one char to another.. in this case we replace newlines \n with zero-bytes \0. Strange, but needed for the next step. *Instead of newline, each file will be separated by \0*

```
 | xargs -0 rm
```
xargs is a smart tool... it takes input via a pipe (the | thing that sends data between commands) and runs a command [In this case rm] on the input. The -0 switch makes sure it **sends it in chunks separated by null bytes**, \0. This way, xargs will send rm "Movie file.avi", just like we wanted.

---

### Post by PsYcHo_SiB on 2006-03-20
Woa thanks a lot, worked first shot.

Linux is very sensitive with filenames with space as I see. ;) 

- SiB -

---

### Post by cilynx on 2006-03-20
Not to downplay the solution above (I first approached this with a for loop), but this can be solved with a very simple edit

Just wrap the backticked command with quotes.

```

rm "`ls *.avi -1t | tail -4`"

```

should do the trick

EDIT:

This doesn't actually work...as pointed out below

---

### Post by engla on 2006-03-20
[QUOTE=cilynx]Not to downplay the solution above (I first approached this with a for loop), but this can be solved with a very simple edit

Just wrap the backticked command with quotes.

```

rm "`ls *.avi -1t | tail -4`"

```

should do the trick[/QUOTE]
I can't get that to work for multiple files.. it makes rm think all the four lines is one file, which is again not what we want.

---

### Post by cilynx on 2006-03-20
You're right.  My mistake.  That's what I get for answering questions on the forums while I should be doing lab writeups...

---

### Post by nanotube on 2006-03-21
you really dont even need the tr part, since your problem is spaces in filenames, not newlines in filenames (which tr wouldnt solve anyway, because it would not know a newline in filename from newline separating file listings, anyway). 

so you should be able to get away with simply
```
ls *.avi -1t | tail -4 | xargs rm
```
without any need for translating \n to \0 (and thus without needing to provide -0 argument to xargs).
have fun. ;)

---

