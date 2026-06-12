---
title: "Seemingly unusual problem whilst installing compiz plugins"
date: 2009-08-28
forum: General Help
---

### Post by pkchips on 2009-08-28
Hello all,

I'm having a difficult time installing the compiz ghost plugin, and I couldn't find any solution on google.

I'm new to Linux so it may be something simple I've done wrong.

Essentially, I followed the guide on this page word for word [http://blogs.myspace.com/index.cfm?fuseaction=blog.view&friendId=114797592&blogId=448251479](http://blogs.myspace.com/index.cfm?fuseaction=blog.view&friendId=114797592&blogId=448251479)

and installed all the dependencies, and then git cloned the ghost plugin.

Then I went into the ghost directory using "cd ghost" and then proceeded to type "make". I get the error "make: *** No targets specified and no makefile found. Stop."

I don't understand what's going on as I used git clone like everyone else seems to, but it doesn't seem to work. Inside the directory are 2 files, "cmakelists.txt" and "ghost.xml.in". There are also 2 directories, one called "src" and one hidden directory called ".git" The src directory contains a cpp and h file, whilst the .git directory contains a lot of stuff.

Could anyone please help me get the installation to work?

---

### Post by pkchips on 2009-08-28
I understand that this might seem like a basic or simple problem compared to some others, but I would appreciate at least a reply from someone?

Is there any alternative way to install this compiz plugin?

---

### Post by pkchips on 2009-08-28
Rebumped.

I really would like an answer to this question.

---

### Post by P4man on 2009-08-28
A basic question? Heh. not many new linux users start by asking questions about compiling modules they pulled in through git.

I dont have a direct answer, id have to follow the how to myself and see what happens, but ill just note that howto is a year old, and its possible that plug in is simply not compatible with current compiz. There is a reason ubuntu uses repositories, and anything outside that, well, may or may not work.

---

### Post by pkchips on 2009-10-03
Hello again,

Any chance of a solution to this problem?

If not, is there any other way to allow clicks to pass through the active window into the one behind it?

---

### Post by P4man on 2009-10-04
No idea. All I can suggest is making sure you have "build-essential" installed (sudo apt-get install build-essential). If you can't make it work, perhaps try on compiz forums?

---

### Post by pkchips on 2009-10-19
Answer was found here:

[http://forum.compiz.org/showthread.php?p=75435#post75435](http://forum.compiz.org/showthread.php?p=75435#post75435)

Need to do this:

cd ~/compiz/ghost
git checkout 30b482c506354c95bab9feb5a40b9c9f0ea4de50
make
sudo make install

---

