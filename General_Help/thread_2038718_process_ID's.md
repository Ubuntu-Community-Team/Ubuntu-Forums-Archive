---
title: "process ID's ?"
date: 2012-08-07
forum: General Help
---

### Post by winzip on 2012-08-07
Here is jboss process ID's ...


[IMG]http://i218.photobucket.com/albums/cc298/curseofgoldendragon/jboss.png[/IMG]


if I want to kill  jboss process which process ID  I should use ?   kill -9 <which_process_id>  ?

---

### Post by Grenage on 2012-08-07
Indeed, PID and Parent PID (PPID).  You'll generally want to kill the process rather than its parent, unless you need to kill the parent - obviously.

---

### Post by squaregoldfish on 2012-08-07
The first PID is for the process itself. The second one is the PID of the parent process, i.e. the one that started it.

So JBoss was started with PID 23440, which then started a child process 23498. So if you kill the parent process 23440, all its children will be killed too.

Steve.

*Of course, you're aware that you should shut down processes using their quit functions where at all possible ;)*

---

### Post by winzip on 2012-08-07
> **Grenage said:**
> Indeed, PID and Parent PID (PPID).  You'll generally want to kill the process rather than its parent, unless you need to kill the parent - obviously.

I  guess first column  represents is PID  and second column represents PPID ....right ?

IF so ...I see jboss showing 3 process ID's  in first  column ....i.e 23440 , 23496 , 25182 

so which ID I should use with kill command ?

kill -9 <which_process_ID_to_use_to_Kill_Jboss_In_This_Example>  ?

---

### Post by Grenage on 2012-08-07
> **winzip said:**
> I  guess first column  represents is PID  and second column represents PPID ....right ?

Bingo; if you use the command without piping into grep, you'll see the column headers.

Take a read of [this]("http://linuxfordummies.org/kill-9-why-you-should-not-use-it-unless-absolutely-necessary/"); as Steve rightly says, killing a process is not ideal, and kill -9 is a last resort.

---

### Post by winzip on 2012-08-07
> **Grenage said:**
> Bingo; if you use the command [COLOR=Red]without piping into grep[/COLOR], you'll see the column headers.



did not get you....[COLOR=Red]without piping into grep ?  
[COLOR=Black][/COLOR][/COLOR][COLOR=Black]
Could you please post the command ?
[/COLOR]
> 
Take a read of [this]("http://linuxfordummies.org/kill-9-why-you-should-not-use-it-unless-absolutely-necessary/"); as Steve rightly says, killing a process is not ideal, and kill -9 is a last resort.

I know.  I am asking for a last resort !

you did not answer which ID (there are several ID's )  to pick here to kill jboss for this example....I need that information.

---

### Post by Grenage on 2012-08-07
> **winzip said:**
> did not get you....without piping into grep ?  

Could you please post the command ?

```
ps -ef | grep jboss
```

That command pipes the output of *ps -ef* into grep, which outputs lines containing *jboss*.  to view a list without grep (which would have given you column headers), you would use:

```
ps -ef
```

> **winzip said:**
> I know.  I am asking for a last resort !

you did not answer which ID (there are several ID's )  to pick here to kill jboss for this example....I need that information.

I would guess you want to end 23440, but that's just a guess.

---

### Post by Vaphell on 2012-08-07
> did not get you....without piping into grep ?

Could you please post the command ?

if you run ps alone (ps -ef), you get tidy columns with labels
once you grep the desired phrase in ps output (ps -f | grep jboss), you see only rows containing that phrase and everything else is thrown out, including first row with labels.

---

