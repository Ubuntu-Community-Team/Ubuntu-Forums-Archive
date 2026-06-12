---
title: "tool for multiplexing input to interactive program?"
date: 2011-06-15
forum: General Help
---

### Post by Arndt on 2011-06-15
I have an interactive command line program, in which I can enter a command at a time, which will cause the program to perform some computation and display a result. It is typically started from a shell in a terminal window.

Now I want to additionally give input to the program programmatically, for example by having a program write to a particular named pipe, and the first program read from both this pipe and stdin.

(In practice, I would be the one triggering the programmatic input too, by clicking somewhere in a kind of graphic editor, which can then send a complicated command sequence to the first program, instead of me having to copy text by hand from the editor.)

Is there a tool that can do this generally? It would work similarly to the 'script' program, starting a new interactive shell in which one can do any commands, the difference being that I don't want output to be sent also to a file, I want input to also come from a file (the named pipe).

I am capable of writing such a tool, but it would be helpful if it already existed. Does it?

---

