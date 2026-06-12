---
title: "How to rename a large number of messed up file names."
date: 2012-08-22
forum: General Help
---

### Post by ATSC on 2012-08-22
Hello lads :)


I've  screwed up the names of a **large** batch of pdf-files with Krename with the result that the filenames  contain the original name twice. They look like this:

```
10 ways to show off your ubuntu skills.pdf10 ways to show off your ubuntu skills.pdf
```Does anybody here know some magic that clears this up? I *think* it may be possible with rename (the pearl-script) but I'm a bit unsure about the syntax. Any help would be much appreciated.  :)

---

### Post by nehalem04 on 2012-08-22
You can try 'pyRenamer' available in software center.

---

### Post by steeldriver on 2012-08-22
how about

```
rename -nv 's/(.*\.pdf)(.*\.pdf)/$1/' *.pdf
```(if it appears to match correctly take out the -n to run it for real)

---

### Post by CharlesA on 2012-08-22
> **steeldriver said:**
> how about

```
rename -nv 's/(.*\.pdf)(.*\.pdf)/$1/' *.pdf
```(if it appears to match correctly take out the -n to run it for real)

This would work wonders. Perl is pretty awesome. :D

I used that same command to replace underscores with spaces. ;)

---

### Post by ATSC on 2012-08-22
That seems to do the trick. Many, many thanks! :D



/addendum: Is it possible to rename also all files in the subdirectories?

---

### Post by ATSC on 2012-08-31
[IMG]http://img100.imageshack.us/img100/1301/tumbleweeds01.jpg[/IMG]

---

### Post by steeldriver on 2012-08-31
I *think* that with bash 4.x you should be able to use 'rename' with the bash globstar

```
rename -nv 's/(.*\.pdf)(.*\.pdf)/$1/' **/*.pdf
```However I have always used 'find -exec' for this kind of thing

```
find /path/to/top/dir -name '*.pdf' -exec rename -nv 's/(.*\.pdf)(.*\.pdf)/$1/' {} \;
```[although if there are MANY files this may overflow in which case you'd need to do something more clever (either using xargs or using a while loop to read the output from 'find' line-by-line)]

---

### Post by ATSC on 2012-08-31
That gives me a
```
Bareword "v" not allowed while "strict subs" in use at (eval 1) line 1.

``` :(

I also had a look onto pyRenamer and Krenamer again but I have difficulties to find the correct renaming pattern. :-(

---

### Post by steeldriver on 2012-08-31
Which variant (the globstar version or the find version - or both)?

For the globstar version, you will need bash > 4.something with globstar enabled, I think

```
$0 --version
shopt globstar
```FWIW I tried both syntaxes before posting (Ubuntu 12.04 / bash 4.2.24) and they both appeared to work

The error you are getting would appear to be from perl btw

---

### Post by ATSC on 2012-08-31
I tried both - the result was the same. I use bash 4.1-2ubuntu3 and perl 5.1. (under Lucid).

---

### Post by steeldriver on 2012-08-31
Hmm... that's odd - just in case it is to do with the number of files you could try

```
find . -name '*.pdf' -print0 | xargs -0 rename -nv 's/(.*\.pdf)(.*\.pdf)/$1/'
```

or

```
while read -r -d $'\0' filename; do rename -nv 's/(.*\.pdf)(.*\.pdf)/$1/' "$filename"; done < <(find . -name '*.pdf' -print0)
```Replace the '.' in the find with the appropriate path if you're not doing this relative to the current directory

FWIW my perl is 5.14.2

---

### Post by hakermania on 2012-08-31
Hmmm... As I see it, all the filenames have been doubled... This means that all of them are an even number (because 2k (when k is Natural) is even).

With this in mind, you could use this bash script so as to rename the files you have in a directory with that exact effect that you described..

Please name the script rename.sh and put it to the same directory as your messed up files. Also, give it executable permissions by hitting Right-click->properties->permissions->allow executing the file as program or, via the terminal, by giving:
```

chmod +x rename.sh

```

First of all, you can run this so as to see what the result will be:

rename.sh script:
```

#!/bin/bash

for file in */*/*/*/*; do
   if [[ "$file" != "rename.sh" ]]; then #<--- please here put the filename of this script (e.g. rename_all.sh)
      extra_chars=$(echo -ne $((${#file}/2)))
      new_file=${file:$extra_chars}
      echo "The file $file ehas ${#file} chars and so it has $extra_chars extra chars, so, it has to become $new_file"
   fi
done

```
This will output the changes that are to be made.

And this script will apply these changes:

```

#!/bin/bash

for file in */*/*/*; do
   if [[ "$file" != "rename.sh" ]]; then #<--- please here put the filename of this script (e.g. rename_all.sh)
      extra_chars=$(echo -ne $((${#file}/2)))
      new_file=${file:$extra_chars}
      mv "$file" "$new_file"
   fi
done

```

It is important the script to be named rename.sh so as not to apply this renaming thing to itself. If you choose a different name for the script, the change it correspondingly from inside the script.

***_Be sure to keep backups!!!_***

---

### Post by ATSC on 2012-09-13
> **hakermania said:**
> 

[/code]First of all, you can run this so as to see what the result will be:

rename.sh script:
```

#!/bin/bash

for file in */*/*/*/*; do
   if [[ "$file" != "rename.sh" ]]; then #<--- please here put the filename of this script (e.g. rename_all.sh)
      extra_chars=$(echo -ne $((${#file}/2)))
      new_file=${file:$extra_chars}
      echo "The file $file ehas ${#file} chars and so it has $extra_chars extra chars, so, it has to become $new_file"
   fi
done

```Thanks for your suggestions. I'm afraid that I get loads of these:```
rename.sh: 9: [[: not found
```Did I do anything wrong?

---

### Post by ATSC on 2012-10-11
Any further thoughts? :(

---

### Post by ATSC on 2012-10-12
Theoretically speaking, the command that I'm searching for would need to count the number of chars that the filename(s) has/have, subtract (the first half) of the characters and move on to the next file, right?

Is that possible with pyrename, Krename or in any other way?

---

### Post by steeldriver on 2012-10-12
Can you please run one of the commands I posted previously e.g.

```
shopt -s globstar; rename -nv 's/(.*\.pdf)(.*\.pdf)/$1/' **/*
```

and this time copy the EXACT command as you run it AND the exact error? Let's see if we can figure out why it's not working

Thanks

---

### Post by ATSC on 2012-10-12
^^ Thank you. :)

I took one example folder, used the command above, including the```
-n
``` and got positive results (e.g. the filenames were corrected). Afterwards, I used the same command without the "-n" and got this error:
```
Bareword "v" not allowed while "strict subs" in use at (eval 1) line 1.
```

---

### Post by drmrgd on 2012-10-12
The error suggests you removed both the '-' and the 'n'.  So, now 'v' looks like something other than the option that it was originally intended to be.  So, put the '-' back in front of the 'v' and you should be good to go.

---

### Post by steeldriver on 2012-10-12
Ah! yes my apologies - when I said "take out the -n" I meant for you to remove the -n (no action - i.e. trial run mode) option leaving **[COLOR=Red]-[/COLOR]**v (verbose)

```
shopt -s globstar; rename [COLOR=Red]**-v**[/COLOR] 's/(.*\.pdf)(.*\.pdf)/$1/' **/*
```although in fact you may want to remove -v as well if you have so many files that it's tedious to watch the verbose progress scroll through

```
shopt -s globstar; rename 's/(.*\.pdf)(.*\.pdf)/$1/' **/*
```

---

### Post by ATSC on 2012-10-12
> **drmrgd said:**
> So, put the '-' back in front of the 'v' and you should be good to go.
That did the trick. :)

There are a few files were the filenames are ok. Is it safe to leave them where they are while I try to rename the others or do I have to move them elsewhere?

---

### Post by steeldriver on 2012-10-12
It's supposed to ignore everything except the double-named pattern - if the trial run worked OK you should be good

Unless by "filenames are OK" you mean that you want to keep some names of the form *.pdf*.pdf

---

### Post by ATSC on 2012-10-12
Perfect :)

Many thanks for your fantastic support.  =D> Without these support forums, I'd get stuck continously.
I'd buy you a beer if I just could so here's a virtual one instead!


[IMG]http://imageshack.us/a/img402/6631/beermugd.jpg[/IMG]


Have a GREAT weekend! :popcorn::guitar:

---

### Post by steeldriver on 2012-10-12
glad to help and thanks for the virtual beer - fwiw I just cracked a (real) Griffon Blonde before reading this :)

sorry it took so long to iron out the final wrinkle for you

---

