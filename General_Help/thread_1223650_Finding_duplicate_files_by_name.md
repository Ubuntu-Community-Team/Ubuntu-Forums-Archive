---
title: "Finding duplicate files by name"
date: 2009-07-26
forum: General Help
---

### Post by frunns on 2009-07-26
I want to find duplicate files by name, but not exactly the same name necessarily, not by content as it might not be exactly the same. Anyone know of a fairly simple way to do this? All solutions I've found have been by searching the content of the files...

---

### Post by madsmeg on 2009-07-26
I have a script to do this, but am on my works PC, if you PM me I can let you know the details when I get home.

---

### Post by wojox on 2009-07-26
In a terminal:

```
locate file.txt
```

---

### Post by SuperSonic4 on 2009-07-26
> **wojox said:**
> In a terminal:

```
locate file.txt
```

You may want to update the database before running it ```
sudo updatedb
```

---

### Post by frunns on 2009-07-26
> **wojox said:**
> In a terminal:

```
locate file.txt
```


Ok, yeah, that's for finding a file. I want a script or program to go through a couple of thousand files and check if there are any other files with ROUGHLY (I didn't specify that in the first post, sorry) the same name.

---

### Post by madsmeg on 2009-07-26
Be home in 2 hours and have a script I think will work for you...

---

### Post by madsmeg on 2009-07-27
```
#! /bin/bash
echo "Please type the name of the file you would like to look for:"
echo -n ""
read -e FILE
echo "Searching for all instances of \"$FILE\", please be patient..."
sudo find / -type f -name "*$FILE*"
echo "Done!"
```

I am not a big scripter, so let me know if the above just plain sucks...

---

### Post by DaithiF on 2009-07-27
probably slightly better to use -iname rather than -name, so as to do a case insensitive match.

---

### Post by decoherence on 2009-07-27
> **frunns said:**
> I want to find duplicate files by name, but not exactly the same name necessarily, not by content as it might not be exactly the same. Anyone know of a fairly simple way to do this? All solutions I've found have been by searching the content of the files...

Well, there are two possibilities here. If you have files with similar names of the sort "myfile01" "myfile02" etc and you already know, more or less, what the variations on the name are going to be, then it's a matter of writing the right regular expressions. In this case, give us some sample names and we can write an expression for you.

If you don't know specifically what the other names are, you want to do fuzzy expression matching. I'm not aware of any such functionality in bash... I'm sure there's a way to do it with enough masochistic monkeys and keyboards.

You'll probably have better luck looking for something pre-made in perl or python to do this. Here is a module on CPAN that might do it for you [http://search.cpan.org/dist/String-Approx/Approx.pm]("http://search.cpan.org/dist/String-Approx/Approx.pm") and here is a usage example [http://snipplr.com/view/16365/fuzzy-string-matching-with-perl/]("http://snipplr.com/view/16365/fuzzy-string-matching-with-perl/")

madsmeg's script is a wrapper for the find command. If you wanted to run find directly, something like

```
sudo find / -type f -iname "**Search_String**"
```

might get you what you want. It will find things like

12345Search_String5431
sEaRch_STriNG_BARFARGHUCKALUCKACHUCK

but it won't find

SearchString
search-string

so as long as "Search_String" (case insensitive) appears somewhere in the file name, you're good. If not, go check out the perl solution!

---

### Post by frunns on 2009-07-28
Ok, I'll check out the perl solution when I have time.

Let's think of an example. Let's say I have different revisions of a file, maybe a picture, all named similiar, but not really in any pattern.

holiday-picture.2008.001.jpg
bw.holiday-picture.2008.001.jpg
holiday-picture.001.jpg

In this hypothetical situation I've been fairly inconsistent in my naming and would just need a script or program with large enough error margin to find all these files. Considering going nuts with some Python or something when I have the time, but it feels stupid having to reinvent the wheel. :P

---

### Post by decoherence on 2009-07-29
> **frunns said:**
> Ok, I'll check out the perl solution when I have time.

Let's think of an example. Let's say I have different revisions of a file, maybe a picture, all named similiar, but not really in any pattern.

holiday-picture.2008.001.jpg
bw.holiday-picture.2008.001.jpg
holiday-picture.001.jpg

In this hypothetical situation I've been fairly inconsistent in my naming and would just need a script or program with large enough error margin to find all these files. Considering going nuts with some Python or something when I have the time, but it feels stupid having to reinvent the wheel. :P

You've been inconsistent in the naming, but one part of the name remains consistent and that allows you to use the find command.

```
sudo find / -type f -iname "*holiday-picture*"
```

will match any of those. 

matching:
holiday-picture.2008.001.jpg
bw.holiday-picture.2008.001.jpg
holiday-picture.001.jpg
HoLiDaY-piCTure

non-matching:
holidaypicture.2008.001.jpg
bw.holiday-pics.2008.001.jpg

hope that helps illustrate how it works. sounds like you can get by just with find (or perhaps multiple passes of find if you need to write a 'heuristic' for a particular variation)

---

### Post by frunns on 2009-07-30
> **decoherence said:**
> You've been inconsistent in the naming, but one part of the name remains consistent and that allows you to use the find command.

```
sudo find / -type f -iname "*holiday-picture*"
```

will match any of those. 

matching:
holiday-picture.2008.001.jpg
bw.holiday-picture.2008.001.jpg
holiday-picture.001.jpg
HoLiDaY-piCTure

non-matching:
holidaypicture.2008.001.jpg
bw.holiday-pics.2008.001.jpg

hope that helps illustrate how it works. sounds like you can get by just with find (or perhaps multiple passes of find if you need to write a 'heuristic' for a particular variation)

Ah, yes. I'm quite aware of find's capabilities, what I'm after is a way to do this automatically, and in more variations. Feels like there should be a program out there for it.

---

### Post by decoherence on 2009-07-31
> **frunns said:**
> Ah, yes. I'm quite aware of find's capabilities, what I'm after is a way to do this automatically, and in more variations. Feels like there should be a program out there for it.

How would you like to automate it?

Are you talking about having the program automatically identify all the files with similar names? (as opposed to being similar to a filename you provide?)

I think your best bet, at least that I'm aware of, is the perl thing. The extension is in ubuntu's repository.... it's called libstring-approx-perl.

EDIT:

Hold on.... I just remembered "agrep." It's in the repository and it's basically 'grep' except you can tune it to tolerate certain inaccuracies. It would still need to be tuned for certain kinds of searches but in combination with a script perhaps it'll do the job?

I totally forgot about that!

---

### Post by frunns on 2009-08-01
> **decoherence said:**
> How would you like to automate it?

Are you talking about having the program automatically identify all the files with similar names? (as opposed to being similar to a filename you provide?)

I think your best bet, at least that I'm aware of, is the perl thing. The extension is in ubuntu's repository.... it's called libstring-approx-perl.

EDIT:

Hold on.... I just remembered "agrep." It's in the repository and it's basically 'grep' except you can tune it to tolerate certain inaccuracies. It would still need to be tuned for certain kinds of searches but in combination with a script perhaps it'll do the job?

I totally forgot about that!

As soon as I sober up I'm going to check this out. :) Thanks for the suggestions.

---

### Post by Hilko on 2011-03-19
To find files matching a pattern recursively in a directory you can do
```
ls -R /path/to/directory/ | tee listOfFiles
egrep PATTERN listOfFiles
```
Replace 'PATTERN' with a suitable regular expression (That is the hardest part).

---

