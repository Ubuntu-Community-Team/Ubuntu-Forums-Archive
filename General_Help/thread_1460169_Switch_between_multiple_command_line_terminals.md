---
title: "Switch between multiple command line terminals"
date: 2010-04-22
forum: General Help
---

### Post by lorenrne on 2010-04-22
Does anyone know how to count how many stacked terminal sessions you have open, or know how to switch between them?

For example, you open a command line terminal and then type "sudo bash", and now you are in a second terminal as root user, but the first terminal is still open.  To return to the first terminal you can type "exit" which will close your root user terminal and put you back inside your first terminal.

I know if you run a second shell, your first shell remains open and if you type in "echo $SHLVL" it will tell you how many you have open.  Is there a similar command that will tell you how many terminals you have stacked up, and is there a way to switch between them without having to exit the top of the stack and drop down a level?

Thanks.
Loren.

---

### Post by KeyserSoze93 on 2010-04-22
Run the pstree command. This will show you the tree of processes, for example:
```

bash---bash---bash---pstree

```

Means you are running in your their subshell.

---

### Post by lorenrne on 2010-04-22
Thanks, that is a great way to see how deep your stack is.

Now... is there a way to switch between them?

---

### Post by KeyserSoze93 on 2010-04-22
> **lorenrne said:**
> Thanks, that is a great way to see how deep your stack is.

Now... is there a way to switch between them?

Not in that way, but you should really check out GNU screen.

[http://en.wikipedia.org/wiki/GNU_Screen]("http://en.wikipedia.org/wiki/GNU_Screen")

You can type the command "screen", and it will open a shell.

Then, type CTRL-a, and then c, and it will open a new shell. You can then switch between your shells with CTRL-a, n and CTRL-a p.

You can then have many shells open at the same time, since they are not subshells so they don't tie the process up.

---

