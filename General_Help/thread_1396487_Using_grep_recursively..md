---
title: "Using grep recursively."
date: 2010-02-02
forum: General Help
---

### Post by zozza on 2010-02-02
I cannot figure out how to use grep as I want.

I want to take a word - let us say "madness" and scan every file in a series of directories for files that contain it. 

For example the directory is /home/myname and there are 20 subdirectories and I want all files in the myname directory and its directories to be searched.

Can someone please post the command.

Thanks.

---

### Post by squaregoldfish on 2010-02-02
From the pages of RTFM, the answer is in grep's man page.

-R, -r, --recursive
Read all files under each directory, recursively; this is equivalent to the -d recurse option.

Steve.

---

### Post by Umang on 2010-02-02
I use rgrep, but it's the same as grep -r.

---

### Post by clovold on 2010-02-02
sorry, i'm an idiot.

> **squaregoldfish said:**
> From the pages of RTFM, the answer is in grep's man page.

-R, -r, --recursive
Read all files under each directory, recursively; this is equivalent to the -d recurse option.

Steve.

---

### Post by Umang on 2010-02-02
> **clovold said:**
> That would be nice if it worked in Ubuntu, but it doesn't.  The grep in Ubuntu has no -r or -R option.  You RTFM, but it was the wrong FM.

Also, where is rgrep?  I don't see it on my system or in the package manager.
I works for me. I just tried a "grep "copyright" . -r" in a project directory and got loads of results including from subdirectories.

EDIT: Missed your edit. I guess it would be included with grep (you aren't going to make a new package for an alias!)

---

### Post by squaregoldfish on 2010-02-02
> **clovold said:**
> sorry, i'm an idiot.

Don't worry - happens to the best of us!

Steve.

---

### Post by jharris1993 on 2012-02-11
> **squaregoldfish said:**
> From the pages of RTFM, the answer is in grep's man page.

-R, -r, --recursive
Read all files under each directory, recursively; this is equivalent to the -d recurse option.

Steve.

Steve:

[LIST=1]
[*]Thank you for that tip!
[*]All too often someone asks a question and gets the "RTFM!!!!" answer.
Now, I consider myself a reasonably literate person and, yes, I have perused my share of man pages.  Unfortunately, many of these pages are not unlike the Minoan Labyrinth, I honestly expect to meet some dude with a bulls head as I try to read it! (*i.e.* Try the man page for "mdadm".  If **that's** not a chewy man page, then I don't know what is!)
[*]Not everyone is a graduate of the Evelyn Woods Speed Reading class.  Likewise, not everyone speaks English as their primary language.  And for many people, the simple act of reading itself is not a trivial exercise.  (Can you say "Dyslexia"?  Ahhh!  I **KNEW** you could!)
[*]There are not a few man pages that run something like this:

[FONT=Courier New]--------------------------------------------
man "foo"

FOO - a program that makes users wish for the sanity of Windows.[/FONT] [FONT=Courier New]

Usage:  foo [qwertyuiopasdfghjkl] [argument] [. . . . .][/FONT] [FONT=Courier New]

where qwertyuiuiopasdfghjkl is one of a host of possible options, (many of which are mutually exclusive, but we don't want to tell you which ones they are), and [argument] is the required argument for this command.  (You'd really like to know what this argument actually is - and we could tell you, but then we'd have to kill you.)[/FONT] [FONT=Courier New]

The documentation for FOO has been provided as a TEXINFO page.
Sucks being you if you expected useful information here.
And it's a lead-pipe-cinch that the package installed by your distribution's package manager didn't bother to include the TEXINFO data.[/FONT] [FONT=Courier New]

BUGS:  Report bugs to [/FONT] [FONT=Courier New]"dev.null@bogus.com"
-----------------------------------------------
[/FONT]

Even if you are an experienced Unix/Linux user, you end up throwing your hands up in frustration, going on the web, and hoping for an answer from a group like this.
[/LIST]
I, myself, have been blown-off fora where I asked what I believed was a perfectly reasonable question.  Therefore, when I try to answer a user's question - even if it appears that he is an absolutely pure-blind idiot - I really try not to use "RTFM".

What say ye?

Jim (JR)

---

### Post by squaregoldfish on 2012-02-12
[Discussion taken to a different location]

---

### Post by sisco311 on 2012-02-12
[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

Thread closed.

---

