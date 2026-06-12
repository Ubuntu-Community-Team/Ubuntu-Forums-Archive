---
title: "Understanding Directories in Ubuntu."
date: 2006-04-09
forum: General Help
---

### Post by junglemike on 2006-04-09
Hi all. I'm already 7-day Kubuntu user. Like it really much.
I've already learned basic Kubuntu configuration process
I'm now trying to undertand the directory structure. I.e - which folder means what.
I've installed Krusader which is very excellent program, but it won't let me create directories in the root of the disk. It says "no permission". I guess i need sudo command, How do i pass "sudo" command to Krusader, every time i want to move or create directories.
Where would be the best place for user files, such as .doc .pdf  and .mp3  files?

---

### Post by adam.mech09 on 2006-04-09
Hi

When I was just learning linux I had the same problems.  

For learning the basic structure of linux, as well as how to work your way around the command line, I started at [http://www.linuxcommand.org/]("http://www.linuxcommand.org/"), though there are plenty of how-to's and help tutorials here.  The Search field will quickly become your best friend :).

As far as the best place to put documents and any other personal files, your home folder (/home/yourusername/) is the best place.  If you are coming from windows, think of it as your"My Documents" folder.

-Adam

---

### Post by incubus on 2006-04-09
If you're all about details, I'd sugest these ones:
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)
[http://en.wikipedia.org/wiki/Filesystem](http://en.wikipedia.org/wiki/Filesystem)

If you prefer it quick 'n dirty, how about this:
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

As Adam pointed, in Unix-like systems you'd prefer to save normal things, such as your data, in your home directory. It's a "Ulysses tying himself to the mast"-kind of strategy. :-)

incubus

EDIT: I just checked Adam's link and it's pretty good, probably more useful than the ones I posted!

---

### Post by incubus on 2006-04-09
By the way, if you want to run KDE (or other GUI) programs using sudo, it's a better practice to run "kdesu" instead.

$ kdesu krusader

...for example.

Now, I don't know if there's an easy way of making it ask you for sudo credentials (I still do these things in the command line). But if you can, just create your folders in your use "home".

incubus

---

### Post by feathers on 2006-04-10
Do not create, move or delete folders that need root access unless you are very sure what you are doing. Especially as a beginner, you may render your system useless. 
You may edit configuration files with the sudo command but everything else should be left alone. The package management on Debian system, of which kubuntu is part, is very sophisticated and leaves you with a usable configuration afterwards.

---

