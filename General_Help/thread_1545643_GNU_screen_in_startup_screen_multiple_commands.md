---
title: "GNU screen in startup screen: multiple commands"
date: 2010-08-04
forum: General Help
---

### Post by MadeR on 2010-08-04
Greetings,
I am searching for a way to run multiple commands at boot time using the gnu screen utility. 

A solution could be:
screen -dm -t title1 command1
screen -dm -t title2 command2
.
.
.
screen -dm -t titlen commandn

but the result would be many sessions, each one with just one child. What I need is just one session with many children, one child per command.

Can anybody help me?

Thanks

---

### Post by Flimm on 2011-09-15
Try this:

```

screen -dm -t title1 bash -c 'command1 ; command2 ; command3'

```

This will run command1, command2 and command3 in sequence in one screen session.

---

### Post by gmargo on 2011-09-15
I think the OP wanted to run a single screen program with multiple internal "screens", each running a different program.  

Here's one way to do it.  **screen(1)** has a "-c" option to provide a startup file instead of $HOME/.screenrc.  And that startup file can start new internal screens.

Example input file:
```

# Screen startup file to start multiple commands under multiple screens.
# Start with "screen -c thisfilename"

# Screen 0: Start 'top'
# Screen 1: Start 'tail -F /var/log/syslog'

screen -t top    0 top
screen -t syslog 1 tail -F /var/log/syslog

```Save the above to a file, say "fancy.screenrc".  Then start screen with:
```

screen -c fancy.screenrc

```

---

