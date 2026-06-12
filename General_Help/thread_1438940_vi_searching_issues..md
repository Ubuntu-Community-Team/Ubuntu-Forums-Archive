---
title: "vi? searching issues."
date: 2010-03-25
forum: General Help
---

### Post by jesselander on 2010-03-25
How come when I search for "vi" I get "no results"? It's a linux text editor that comes with ubuntu isn't it? I know it is cause I've used It in ubuntu server 32 bit 9.10.
 
Also, how can you sort search results by most relevant rather than most recent post?

---

### Post by linuxman94 on 2010-03-25
Gedit and nano are the default text editors in Ubuntu.  Gedit is graphical and nano is in the terminal.

---

### Post by falconindy on 2010-03-25
You probably want vim, not vi.

---

### Post by jesselander on 2010-03-25
I searched again even after I created this thread and still no matches!  I tried "vi" vi vi? Still no worky. Just to be sure for my next search attempt:  vi vi vi vi 
 
I know vi is a text editor cause I used it in ubuntu 9.10 server 32 bit.
 
I see now how to sort. You have to do it from the search menu before you click "search".
 
I also get no matches for  "9.10" or "8.04" without the quotes.

---

### Post by jesselander on 2010-03-25
Search is disfunctional for certain terms! Do these searches work for anybody else or is it just me?  Why is this not working?

---

### Post by falconindy on 2010-03-25
Oh. Searching in the forums.

Searching isn't dysfunctional. It just excludes terms that are too short. There's likely other criteria that exclude various terms from being searched on.

What is it you're trying to find about vi?

---

### Post by jesselander on 2010-03-26
Well, I wanted to find out how to use it.  I have since figured it out but mine does not do what it is supposed to.  It crashes when I try to escape from an insert command.  
 
Really though I just want to be able to search the forums before I start a new thread that already exists.  For instance I want to know if a newbie like me should be using server edition 8.04 or 9.10 but when I search for the releases I get no matches even though I see them in many threads.  So what's with the search and too short of terms?

---

### Post by falconindy on 2010-03-26
Searching on a term that's deemed too short is in your best interest because the results you get back are going to be far too broad and generally not useful. Part of searching is knowing how to search -- what terms to use, what to avoid. Be specific in your requests.

If you're looking for general help with Vim, there's far better places to look than on these forums. You can start with the man page. [www.vim.org](www.vim.org) should be helpful as well.

---

### Post by quadproc on 2010-03-26
> **jesselander said:**
> How come when I search for "vi" I get "no results"? It's a linux text editor that comes with ubuntu isn't it?

I do not know what you used to do your search, so I don't know why it failed.  But you can find out a couple of things about vi very easily:
```
which vi
``` will give you the path to the vi code file, and ```
man vi 
```will get you the manual.  Yes, it is part of the standard distribution. ```
 info vi 
```will get you the manual for vim, a newer version of vi.

As others have mentioned, there are many more text editors available and you might prefer to use one of them.

I, personally, am very glad that vi is still around and still runs: I needed it to recover a system that could not do graphics due to a software problem.

quadproc

---

### Post by rnerwein on 2010-03-26
hi
/usr/bin/vi -> /etc/alternatives/vi -> /usr/bin/vim.tiny ( symlink )
but it works like vi and i like vi too.
ciao

---

### Post by darolu on 2010-03-26
There are thousands of Vi and Vim manuals out there, most Linux books and manuals have a section/chapter about Vi too (emacs too).

A quick google search gave me this two manuals, both seem to be quite good:

[http://newbiedoc.sourceforge.net/text_editing/vim.html.en](http://newbiedoc.sourceforge.net/text_editing/vim.html.en)

[http://vimdoc.sourceforge.net/htmldoc/usr_toc.html](http://vimdoc.sourceforge.net/htmldoc/usr_toc.html)

And you can always read its manual:
```
$ man vi
```

If you have a secific question about Vi, post it, Vi is very popular and I'm sure someone will know the answer.

BTW falconindy, vim.org gives me 502

---

### Post by andrew.46 on 2010-03-26
Hi jesselander,

> **jesselander said:**
> How come when I search for "vi" I get "no results"?

vim is not installed *by default* under Ubuntu. Easy enough to install though:
```

sudo apt-get install vim
```

All the best,

Andrew

---

### Post by macogw on 2010-03-26
I think forum search strings must be *3* characters or more, if that's what you mean.

---

### Post by jesselander on 2010-03-29
> **macogw said:**
> I think forum search strings must be *3* characters or more, if that's what you mean.
 That must be why. Thanks.

---

