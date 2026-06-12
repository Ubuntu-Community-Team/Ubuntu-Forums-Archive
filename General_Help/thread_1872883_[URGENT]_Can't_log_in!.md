---
title: "[URGENT] Can't log in!"
date: 2011-10-31
forum: General Help
---

### Post by Zortis on 2011-10-31
[FONT=Trebuchet MS]When I try log in I get some terminal output that flashes so fast I can't read it, then it just returns me to the log in screen again!
[/FONT]

---

### Post by Slim Odds on 2011-10-31
> **Zortis said:**
> [FONT=Trebuchet MS]When I try log in I get some terminal output that flashes so fast I can't read it, then it just returns me to the log in screen again!
[/FONT]

That's going to be a little hard to troubleshoot. Maybe you can take a video of it and freeze frame to see the error message.

---

### Post by lykwydchykyn on 2011-10-31
hit ctrl-alt-f1 to go to a text terminal.

Log in, then check your .xsession-errors file, like so:

```

less ~/.xsession-errors

```

---

### Post by Zortis on 2011-10-31
Thanks for the help, I checked the xsession errors and found something to do with the .ICEauthority file. I searched around and found out that a simple fix is to delete this file and upon logging in next time it would recreate itself error free - which worked!

---

### Post by Paddy Landau on 2011-10-31
That's useful to know.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so others with the same problem can find it more easily.

---

### Post by Zortis on 2011-10-31
Solution for other users:

Enter the terminal (Ctrl + alt + F1).
Log in with the account you're experiencing difficulties with.
Type ```
rm .ICEauthority
```
And confirm deletion by typing 'y' and pressing enter.

---

