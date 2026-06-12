---
title: "Prevent writing new characters in beginning of previous command's output lines"
date: 2011-08-05
forum: General Help
---

### Post by Intrepid Ibex on 2011-08-05
Hey,

Not sure if you got what I meant from the Title. I'll try to 'particularise' (looked this up in a dictionary).

In Windows's CMD when you execute a command and then start writing the next one (while still executing the former one) the characters remain in the buffer and they all come up nicely to the new line once the previous command has been executed.

In Ubuntu when I do this the newly typed characters annoyingly get in the beginning of the previous command's output lines.

I don't really understand why isn't the default method as in Windows's CMD. I mean otherwise almost _everything_ sucks with it when compared to Unix/Linux shells/terminals (commands are longer, syntax is annoying, etc.)

So I'd like to know how to do this in both Bash and Zsh.

Thanks for your time, and have a nice day!
(Not that it'd mean anything anymore)

---

### Post by dcstar on 2011-08-05
> **Intrepid Ibex said:**
> Hey,

Not sure if you got what I meant from the Title. I'll try to 'particularise' (looked this up in a dictionary).

In Windows's CMD when you execute a command and then start writing the next one (while still executing the former one) the characters remain in the buffer and they all come up nicely to the new line once the previous command has been executed.

In Ubuntu when I do this the newly typed characters annoyingly get in the beginning of the previous command's output lines.
..........

This is because Unix/Linux is a multi-tasking environment and DOS isn't.

If you type in a shell session then what you type will be echoed immediately while whatever you have running in the session still goes on (and possibly outputs in the same session).

In DOS your input (apart from things like CTRL/C) is buffered because it can only do one thing at time in its session.

---

