---
title: "sudo timing question:"
date: 2006-05-03
forum: General Help
---

### Post by Cirrocco on 2006-05-03
I wrote a script that has to use sudo [command] several times.
I know sudo is good for 15 minutes.  so here's the situation:

first sudo is called and password is entered.  start 15minute counter.
5 minutes later, sudo is called again, and a password isn't needed.  does this restart the 15 minute counter? or do I have 10 minutes left to get all of my sudo calls in place before I have to be present to enter my password again?

---

### Post by nanotube on 2006-05-03
hehe interesting question.
i am not 100% sure, but i think the counter is for 15 minutes of "no sudo activity", so the counter gets reset to 15 min when you use sudo.
there is only one way to be sure - run an experiment. :) make a shell script that looks like
```
sudo echo "blabla"
sleep 10m
sudo echo "blabla2"
sleep 10m
sudo echo "blabla3"
```
and see if sudo asks for password before echoing "blabla3". let us know how it goes.

---

### Post by Cirrocco on 2006-05-03
If I created a launcher and called the whole script using gksudo (and removed all the sudo prefixes from my code) would I have sudo access for the duration of script regardless of how long each line takes to complete?

---

### Post by nanotube on 2006-05-03
hmm, my guess on that is a "no", but again, you should experiment and see if i am right.

---

### Post by Cirrocco on 2006-05-04
Last night I tried: 
```
sudo echo "blabla"
sleep 10m
sudo echo "blabla2"
sleep 10m
sudo echo "blabla3"
```

and it continued to the end without asking for my password.
this suggests that every consecutive sudo call (provided it's within 15minutes of the last sudo) restarts the counter at 15 minutes.

---

### Post by nanotube on 2006-05-04
[QUOTE=Cirrocco]Last night I tried: 
```
sudo echo "blabla"
sleep 10m
sudo echo "blabla2"
sleep 10m
sudo echo "blabla3"
```

and it continued to the end without asking for my password.
this suggests that every consecutive sudo call (provided it's within 15minutes of the last sudo) restarts the counter at 15 minutes.[/QUOTE]

yes, it does suggest that indeed. nothing like a good experiment to figure things out. :)

---

