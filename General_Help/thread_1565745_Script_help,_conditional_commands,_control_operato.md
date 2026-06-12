---
title: "Script help, conditional commands, control operator"
date: 2010-09-01
forum: General Help
---

### Post by eriktheblu on 2010-09-01
I've been employing a script that sets up everything I need to dualbox in World of Warcraft. The script launches two instances of WoW, Keyclone, G15macro, and metacity --replace.

I often just use one instance of WoW, so I would like for the script to behave differently if I already have WoW running.

What I managed to come up with is
```
top -n 1 | grep -a wow.exe || wine "D:\World of Warcraft\wow.exe"
```
This by itself works great. If WoW is running, the command exits. Otherwise it opens WoW.

The problem I'm running into is running the rest of the script. With that line as it is, the script will pause until WoW is closed. I've tried adding the "&" to the end (as that has worked for the rest of the commands I wish to execute); that invariably causes a new instance of WoW to open regardless if there is one open already.

I welcome any advice or references.

---

### Post by Brandon Williams on 2010-09-01
It's possible that the program is showing up differently in top's output when wine was backgrounded. With the "&" on the end of that line, run the script to start "wow.exe". Then run "top -n1". Does wow.exe show up in the listing?

---

### Post by eriktheblu on 2010-09-01
You mean like
```
wine "D:\World of Warcraft\wow.exe" & top -n 1 | grep -a wow.exe
```?

---

### Post by DaithiF on 2010-09-01
Hi,
I think the problem is that the the '&' is backgrounding the entire statement, rather than the wow piece.  If/when the wow piece does get executed, it is not being backgrounded.  If a backgrounded process launches a new process, that new one is not (afaik) itself backgrounded.

so try this instead:
```
top -n 1 | grep -a wow.exe || ( wine "D:\World of Warcraft\wow.exe" & )
```

also, you could look into pgrep as a better alternative to the top / grep piece

---

### Post by jobix on 2010-09-01
Use the pidof command to get the pid of wow.exe if it's running.

> pidof wow.exe


Get the value into a variable and start wine if the value is valid.

---

### Post by eriktheblu on 2010-09-01
Good stuff!

Backbrief to make sure I understand: the & at the end of the line makes the entire line run in the background. top in the background does not see wow.exe because it's not in the background. 

Putting the conditional wine command and the & in parentheses will separate it from the rest of the command so that only the wine portion will be in the background.

Unfortunately it will be a few hours before I can apply this.

I was starting to think along the lines of 
```
top -n 1 > ~/games/top.txt
grep -a wow.exe ~/games/top.txt || wine "D:\World of Warcraft\wow.exe"
```
Which is not far from my starting point.

I like the pgrep suggestion; should be much cleaner than what I was trying to kludge together. I figured my redneck coding would be brought up sooner or later :D

---

### Post by Brandon Williams on 2010-09-01
> **eriktheblu said:**
> You mean like
```
wine "D:\World of Warcraft\wow.exe" & top -n 1 | grep -a wow.exe
```?

No. That would run wow in the background and then run top piped into grep. There would be no direct relationship between the wine command and the top-into-grep pipeline.

Instead, I meant for you to do what I thought you had already tried:
```
top -n1 | grep -a wow.exe || wine "D:\World of Warcraft\wow.exe" & 
```

As has been noted, this might background the whole line, not just the wine command, but I can't see how that would be problematic, since it would still end up doing what you want it to do ... run wow in the background.

Also as previously mentioned, pgrep would be a better choice here for a few reasons. First, your top command won't display all running processes (you need the -b switch for that). And second, top doesn't reliably display the whole command line (it might truncate it).

You'll need to use the -f switch with pgrep in order to match on wow.exe, since pgrep only matches on the command name by default.

I don't think there's a way to make it work with pidof, since wine is the program being run, not wow.exe.

---

### Post by eriktheblu on 2010-09-01
pgrep wow.exe and pgrep -f wow.exe returned the same results. so I will omit the option.

I'm now going with
```
pgrep wow.exe || wine "D:\World of Warcraft\wow.exe" &
```

Works well, and a lot cleaner than what I was coming up with.

Thanks for the support. Looks like I still have a lot to learn.

---

