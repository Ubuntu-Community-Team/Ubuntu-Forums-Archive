---
title: "shell scripting help - spawn a new terminal"
date: 2010-08-24
forum: General Help
---

### Post by vttay03 on 2010-08-24
--I need help with designing a shell script to spawn a new terminal and run a sequence of commands.

For example, I know the following will execute a command in a new terminal:

```

gnome-terminal -e top

```

But I want to do something like:

Open a new terminal and run ALL of the following:

```

echo "This is a test."
date
read -p "Press any key to exit."

```

But if I call 'gnome-terminal -e command' for each line, a new shell will be spawned for each process.  I just want one shell for all of the commands.  I'm sure this is going to be really easy for someone...

---

### Post by Vaphell on 2010-08-24
gnome-terminal -e "sh -c 'echo This is a test; date; read a' "

i have no idea how to embed more layers of '' and/or "" to achieve that read -p "", it seems to have problems with proper parsing. I tried to escape them with \, but to no avail

gnome-terminal -e "sh -c 'echo \"This is a test\"; date; read a'" seems to work but that read -p "..." - no idea, new window flashes and closes

script containing these steps would be a much cleaner solution, **gnome-terminal -e /path/myscript.sh** doesn't look as hardcore

---

### Post by vttay03 on 2010-08-24
> **Vaphell said:**
> 
script containing these steps would be a much cleaner solution, **gnome-terminal -e /path/myscript.sh** doesn't look as hardcore


You're right...I had a brain fart, I just need to throw everything into a script and call the script with 'gnome-terminal -e /path/to/script'.  Thanks for the help...

---

### Post by cinohpa on 2010-08-24
OK. There are two things that come to mind:

1. in your script, creating a script with the code you want to run in the spawned terminal

2. multiplexing processes running in different terminals with screen.

For 1:

```

touch stnt #here you are making the script you want to run in a new terminal
echo one_line_of_code >> stnt
echo another_line >> stnt
....
chmod +x stnt
gnome-terminal -e ./stnt #kick of stuff running in a new terminal
#continue on with your script


```

For 2:
Read man screen. Screen is really useful, although it takes some getting used to. It is worth playing around with, but it is more of a long term commitment depending on your familiarity with the shell.

---

