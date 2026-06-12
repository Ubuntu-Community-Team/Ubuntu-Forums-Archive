---
title: "Run program from CLI then return?"
date: 2011-01-09
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2011-01-09
Hey guys, I'm trying to figure out the syntax needed to run a command that will spew out output (which I don't need) but go back to allowing me to run other commands without closing that program.

Basically I run:

```
 ./utserver 
```and it starts and gives output but I want to run other commands without needing to open a new tab or close that program. Ideas?:popcorn:

---

### Post by Dark_Stang on 2011-01-09
Add an "&" to the end of the command.

```
./utserver &
```

---

### Post by s_h_a_d_o_w_s on 2011-01-09
> **Dark_Stang said:**
> Add an "&" to the end of the command.

```
./utserver &
```

That seemed to assign it a PID but now is there a way to get it to return back the the prompt? It's still in "focus" is that makes sense.

---

### Post by sisco311 on 2011-01-09
EDIT:
[s]```
fg
```[/s]

See:
```
man bash | less +/"^JOB CONTROL"
```

---

### Post by Dark_Stang on 2011-01-09
Just hit Enter to get yourself a new clean line. That terminal will still receive console output from the application you start.

---

