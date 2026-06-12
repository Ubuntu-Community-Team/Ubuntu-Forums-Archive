---
title: "Renaiming files through bash"
date: 2011-02-10
forum: General Help
---

### Post by evan54 on 2011-02-10
hi,

I'm trying to rename ~11000 files. What has happened is I have files in the following format:

string1_100_string2_200_string3_300.log

now the numbers 200 and 300 are sometimes below 100 and the file looks like this:

string1_100_string2_99_string3_99.log

and I want to rename such files to be like this:

string1_100_string2_099_string3_099.log

I wrote a small matlab script but it seems to take forever so thought I'd try and do it bash and have got near to nowhere....

any help appreciated thanks!

---

### Post by sisco311 on 2011-02-10
Try the Perl based rename command:
```

cd /path/to/dir
rename --no-act 's/(.*_)([0-9][0-9]_.*_)([0-9][0-9]\.log)/${1}0${2}0${3}/' *.log

```

---

### Post by evan54 on 2011-02-10
duuuuude, you're beyond awsome, took less than a 1s to rename almost all files.

So just to make sure I understand this correctly:

anything inside ( ) is assigned to a variable ${num}

.* is a wildcard for anything
[0-9] is a wildcard for a single digit number

but how does it know that $1 = "string1_100_" and not "string1_". I mean I can see that if you go from the end of the string it is the only option is that how it knows which one to choose?

Also for:

string1_100_string2_199_string3_99.log

to become

string1_100_string2_199_string3_099.log

I execute:

rename 's/(.*_)([0-9][0-9]\.log)/${1}0${2}/' *.log

and for:

string1_100_string2_99_string3_199.log

I execute:

rename --no-act 's/(.*_)([0-9][0-9]_.*log)/${1}0${2}/' *.log

thanks!

---

### Post by evan54 on 2011-02-10
worked perfectly!! :D I think I get it.

I used two instructions one to add the 0 before the fist 2 number case and one to add the 0 after the second second 2 number case (this way this takes care of the cases where both need zero padding :D )

commands used:

for the 2nd number case:
rename 's/(.*_)([0-9][0-9]\.log)/${1}0${2}/' *.log

for the 1st number case:
rename 's/(.*_)([0-9][0-9]_.*log)/${1}0${2}/' *.log

---

