---
title: "Moving Files by Type in Terminal"
date: 2010-01-30
forum: General Help
---

### Post by msa85 on 2010-01-30
Is there a command for moving a certain amount-or all files-of a certain type? I know how to move files around but I can't find anything that explains how you would move multiple files at once.

Writing this, I wonder, is it possible to move files by their size-moving all files under or over a certain size-rather than by type or name?

I've looked but can't find how to do this, or if it's possible. Can't find anything on google with any combination of search terms.

Thanks

---

### Post by hyperandy on 2010-01-30
I haven't seen that ability without a script of some sort. or maybe using grep to filter and then move the found items but I don't see a size argument for grep [http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep) Obviously you can always use the wild card (*) to clear most of the files. it's not exactly clear what you are doing but for quick dirty easy I would just use the wildcard *

---

### Post by msa85 on 2010-01-30
> **hyperandy said:**
> I haven't seen that ability without a script of some sort. or maybe using grep to filter and then move the found items but I don't see a size argument for grep [http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep) Obviously you can always use the wild card (*) to clear most of the files. it's not exactly clear what you are doing but for quick dirty easy I would just use the wildcard *

Thank you!

---

### Post by Johnny B on 2010-01-30
try the find command
> find . -size +56M exec cp {} /home/
this will go through all subdirectories unless you use: -maxdepth 1

---

### Post by msa85 on 2010-01-30
> **Johnny B said:**
> try the find command

this will go through all subdirectories unless you use: -maxdepth 1

What is the function of the '{' brackets?

Can you recommend an up to date terminal manual? Ubuntu-specific, if possible. I'd like to barrel through this and learn as much as I possibly can, and get really good using just the terminal, but there are so many different sites, and the ones I have used give conflicting information. If there is something I can read that can serve as a foundation, so I can figure out why one guy is telling me something different from the other guy, I'd like to get my hands on it. I love that there is so much info, but much of it is conflicting. I understand there are many different ways to do things in Linux and that's one of it's strengths, but it can be a bit much.

So if there is something to read, or a programming language to learn, then please, someone, point me in the right direction.

---

