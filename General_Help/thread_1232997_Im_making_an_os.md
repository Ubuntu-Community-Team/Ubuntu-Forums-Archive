---
title: "Im making an os"
date: 2009-08-06
forum: General Help
---

### Post by Tclarkie on 2009-08-06
For school i need to do a major science assignment
it does not identify what type of science
i chose to build a computer from spare parts and build an os
i have a kernel, but i need some help working out how to add a command line interface (as gui is way beyond me, unless you can help me with that)

---

### Post by NotJustANewbie on 2009-08-06
Try [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
:)

---

### Post by Nuticulus on 2009-08-06
I think he already has a kernel.

You'll need a keyboard driver. There are several well-written tutorials for these on the internet. I would work on getting the keyboard driver perfect.

Then, what sort of commands do you want to execute? If it's just stuff like 'version' to print the version no., 'pacman' to play pacman, etc. then you can use a switch statement, at least in c++.

If you want a more complicated shell, I would use a parser that generates a tree of commands to execute. Then execute the commands at the bottom of the tree first, and pass the results up the tree to the next command.

Good luck!

---

### Post by sandy8925 on 2009-08-06
Making an OS for a science assignment ? lol. Wish I could have thought of doing stuff like that.

---

### Post by Tclarkie on 2009-08-06
i dont need everything, but id like most ubuntu commands, i thought they were built into the kernel

---

### Post by Tclarkie on 2009-08-06
what is / how do i make   a parser

---

### Post by muteXe on 2009-08-06
What kind of parser?  Command line?
[http://www.google.co.uk/search?hl=en&q=%22command+line+parser%22&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=%22command+line+parser%22&btnG=Search&meta=)

---

### Post by Tclarkie on 2009-08-06
Yes, im not going into gui, this isn't going to depend on any vital school marks, but i want it to have most ubuntu commands

---

### Post by Tclarkie on 2009-08-06
Where do i get i parser (please be a .deb, my pc doesn't compile well)

---

### Post by Tclarkie on 2009-08-06
these are the sorts of commands i want
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

---

### Post by Simian Man on 2009-08-06
OK so are you building a computer or an OS?

If a computer, then what type of processor are you using and what parts are you actually building?

If an OS, then you should start with a simple, single user kernel for a very simple CPU architecture.

In either case you wouldn't rewrite things like a "command parser", top, kill etc.  You'd just compile the GNU versions on your project and use bash for the shell.

In truth, from your posts it sounds like you have no idea what you're doing and should pick a simpler project.

---

### Post by BslBryan on 2009-08-06
> **Simian Man said:**
> In truth, from your posts it sounds like you have no idea what you're doing and should pick a simpler project.
+1, but he really might learn from this.  Depending on the due date, he might pull it off.

---

### Post by Tclarkie on 2009-08-07
firstly, thanks [BslBryan]("http://ubuntuforums.org/member.php?u=797010"), its 4 terms away ( i like being prepared), im making a computer from spare parts ( i have a $0 budget, its a cool thing) and an os. i kinda know what im doing

---

### Post by Mighty_Joe on 2009-08-07
> **BslBryan said:**
> +1, but he really might learn from this.  Depending on the due date, he might pull it off.

Where I went to school, one of the required courses consisted of writing an OS, compiler and (for extra credit) interpreter.  I assure you that it was a very, very basic set of tools, but it was a very cool project that taught a lot about how computers work.  
We used an IBM mainframe for our hardware.  A few semesters later I believe they moved to using [MINIX]("http://en.wikipedia.org/wiki/MINIX") on the PC, and only writing a couple choice modules for the OS.

---

### Post by Tclarkie on 2009-08-07
thats cool as, its kinda wat im looking for, wat yr were u in


i go to school in the middle of nowhere, so we dont get any IT classes at my school

---

### Post by Tclarkie on 2009-08-07
> **Simian Man said:**
> OK so are you building a computer or an OS?
In either case you wouldn't rewrite things like a "command parser", top, kill etc.  You'd just compile the GNU versions on your project and use bash for the shell.
  So how to i do that

---

### Post by Tclarkie on 2009-08-07
im just gonna use lfs, its really good

---

### Post by Mighty_Joe on 2009-08-09
> **Tclarkie said:**
> thats cool as, its kinda wat im looking for, wat yr were u in


The class was called "Operating Systems", of course.  It was pretty much like having a full-time job on top of whatever classes one took that semester.  One had to have a very good grasp of C and some assembler experience or they quickly lost their way.  I can't imagine doing a similar effort without my professor, who could look at a memory dump and remind one to initialize a loop variable or some other innocuous programming error.
If I were going to go it alone, I'd probably buy [Tanenbaum's book]("http://www.amazon.com/Operating-Systems-Implementation-Prentice-Software/dp/0131429388/ref=sr_1_1?ie=UTF8&s=books&qid=1249818223&sr=8-1") and work through the Minix source.  There's all kinds of very arcane topics in writing an OS one would never encounter in regular programing (I'm a professional programmer and I've haven't written an interrupt handler since that class).

---

### Post by Tclarkie on 2009-08-09
have you seen lfs
[www.linuxfromscratch.org](www.linuxfromscratch.org)

how does it compare

---

### Post by Tclarkie on 2009-08-09
And blfs, for xorg window system

---

