---
title: "Bash Question"
date: 2011-09-05
forum: General Help
---

### Post by ragul40 on 2011-09-05
Hi I have an okay experience with ubuntu and can fix most driver problems.
I'm trying to make script to due multiple jobs each in a different terminal. Is is possible to do this. BTW the command have to be run as root.

---

### Post by ragul40 on 2011-09-05
Hi I have an okay experience with ubuntu and can fix most driver problems.
I'm trying to make script to due multiple jobs each in a different terminal. Is is possible to do this. BTW the commands have to be run as root.

[COLOR="Red"]Moderator Edit: Threads merged.[/COLOR]

---

### Post by sanderd17 on 2011-09-05
if you add an '&' sign to the command, it will be executed in a separate thread. 

So if you do
```

gnome-terminal -e "command-to-execute" &

```

it will start a new terminal and continue with the script without waiting for the new terminal.

But why exactly do you need a new terminal? Isn't a new thread enough?

---

### Post by ragul40 on 2011-09-05
well i'm really new to bash and don't know what a thread is. 
What are threads?

---

### Post by sisco311 on 2011-09-05
You can use & to run a job in the background.

See: [http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)

---

### Post by ragul40 on 2011-09-05
thank you

---

