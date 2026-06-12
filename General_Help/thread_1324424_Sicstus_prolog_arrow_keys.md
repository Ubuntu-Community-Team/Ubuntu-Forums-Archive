---
title: "Sicstus prolog arrow keys"
date: 2009-11-12
forum: General Help
---

### Post by nfilip on 2009-11-12
Hello, 
I know this isl ittle  software  specific question but i think that the reason that i cannot solve this is due to lack of linux knowledge so some gurus here may provide the answer.

When I run sicstus prolog it starts up in my XTERM and when I press up arrow it is supposed to navigate back in commands' history. However instead of that it just prints ^[[A on the screen. 

Why is that? And how to solve it? Is there some Xterm settings or linux enviro settings to tackle this obstacle?

---

### Post by zimbone on 2010-01-24
Hi

Don't know if you are still interested, but maybe others are.
I've googled for several hours to find a solution. In the end I found this:

> After about eight seconds of using Sicstus under Linux, you will notice that it doesn't do command-line history or editing. Four seconds later, this will make you want to break something. Don't. Installed on the lab machines is a utility called rlwrap which will make your life much easier. If you run sicstus with the command:
```
rlwrap sicstus
```command-line editing will be enabled. It even remembers the commands you used last session
Found it here: [https://www.doc.ic.ac.uk/lab/mac-msc/](https://www.doc.ic.ac.uk/lab/mac-msc/)

Just works perfectly :D

---

### Post by shaikh on 2011-02-25
perfect! thank you for saving my monitor :D

---

