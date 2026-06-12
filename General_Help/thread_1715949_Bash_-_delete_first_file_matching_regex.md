---
title: "Bash - delete first file matching regex"
date: 2011-03-27
forum: General Help
---

### Post by fela on 2011-03-27
In a bash shell script, I want to do something like this:

```
if [[ $(ls -ld /some/dir/foo_* | wc -l) -gt 4 ]]; then
rm -rf **first_match_of** /some/dir/foo_*
fi

# carry on with script
```

How should I go about this? Thanks.

---

### Post by nice_like_rice on 2011-03-27
rm -rf `ls | grep -m1 foo`

or something like that?

might be a better way to do it with find -exec...
*checks man pages..*

---

### Post by fela on 2011-03-27
Don't worry, I worked it out :)

Here's how I'm now doing it:

```
rm -rf `ls -d foo_* | sort | head -1`
```

cheers :D

---

### Post by sisco311 on 2011-03-27
> **fela said:**
> Don't worry, I worked it out :)

Here's how I'm now doing it:

```
rm -rf `ls -d foo_* | sort | head -1`
```

cheers :D

Please mark this thread as UNSOLVED. :evil:

I tried your command and it fails with files (directories are files too) with spaces and/or newlines in their names.

It's an interesing question, so I will try to answer it, but right now I need a nap. :)

In the meantime please check out:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
and
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)  #1
and of course the FAQ on the same page.

HTH

---

### Post by AlphaLexman on 2011-03-27
OK, I'm on my Fedora 13 laptop now, but I'm getting this to work:
```
rm -rf `ls -d foo_* | sort | head --lines=1`
```
So check your version of 'head'```
head --version
```I'm getting 8.4

---

### Post by sisco311 on 2011-03-28
Good morning! :)

Using quotes fixes the issue with files with spaces in their name:
```
sisco@acme:xtmp$ mkdir foo_dir\ 1
sisco@acme:xtmp$ mkdir foo_dir\ 2
sisco@acme:xtmp$ ls
foo_dir 1  foo_dir 2
sisco@acme:xtmp$ rm -r `ls -d foo_* | sort | head --lines=1`
rm: cannot remove `foo_dir': No such file or directory
rm: cannot remove `1': No such file or directory
sisco@acme:xtmp$ ls
foo_dir 1  foo_dir 2
sisco@acme:xtmp$ rm -r "`ls -d foo_* | sort | head --lines=1`"
sisco@acme:xtmp$ ls
foo_dir 2

```

But lets see what happens if there is a newline in the filename:
```

sisco@acme:xtmp$ mkdir "foo_dir
> name1"
sisco@acme:xtmp$ mkdir "foo_dir
> name2"
sisco@acme:xtmp$ ls
foo_dir?name1  foo_dir?name2
sisco@acme:xtmp$ rm -r "`ls -d foo_* | sort | head --lines=1`"
rm: cannot remove `foo_dir': No such file or directory
sisco@acme:xtmp$ ls
foo_dir?name1  foo_dir?name2
sisco@acme:xtmp$ for file in foo_*
> do
>   if [[ -d "$file" ]]
>   then
>     rm -rf "$file"
>     break
>   fi
> done
sisco@acme:xtmp$ ls
foo_dir?name2

```

---

### Post by fela on 2011-03-28
Hmm, I forgot about spaces/newlines because I never put them in filenames :)

---

