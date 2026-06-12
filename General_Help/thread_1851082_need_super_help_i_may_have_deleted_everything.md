---
title: "need super help i may have deleted everything"
date: 2011-09-27
forum: General Help
---

### Post by RichardC400 on 2011-09-27
Okay, i was trying to delete oracle off my 11.04 ubuntu because somehow i forgot the sudo password for oracle
so i went around deleting things with command: rm
i deleted:

oratab in /etc/
and
rm -Rf admin doc jre o*
and a few other things i think

anywho i go into my home folder and all i see is
Desktop

however if i show hidden files, everything that was a hidden file is still there, so i can't have deleted everything in my home folder... or else hidden files would have been removed too right?

....any chance a reboot might help, or, not?

---

### Post by matt-fender on 2011-09-27
Open a Terminal, press up on the keyboard, to view the last command, press up to view the command before that. Could you list the commands you used?

---

### Post by geo909 on 2011-09-27
> **RichardC400 said:**
> Okay, i was trying to delete oracle off my 11.04 ubuntu because somehow i forgot the sudo password for oracle
so i went around deleting things with command: rm
i deleted:

oratab in /etc/
and
rm -Rf admin doc jre o*
and a few other things i think

anywho i go into my home folder and all i see is
Desktop

however if i show hidden files, everything that was a hidden file is still there, so i can't have deleted everything in my home folder... or else hidden files would have been removed too right?

....any chance a reboot might help, or, not?

Hi,

Where did you do the "rm -Rf admin doc jre o*"? In /etc?
(Anyway, I would avoid wildcards inthere, you deleted 
everything that starts with an "o".)

There is a good chance that I say stupid things now, but
in case you need data recovery, I may have heard that you
should avoid writing (or even using?) the disk.

You have another computer to access the internet until 
somebody more comfortable with those things gives an 
opinion?

---

### Post by geo909 on 2011-09-27
> **matt-fender said:**
> Open a Terminal, press up on the keyboard, to view the last command, press up to view the command before that. Could you list the commands you used?

Or just give the output of 

```
history | tail -20
```

In the end you may have given the rm command in the
wrong place?

---

### Post by matt-fender on 2011-09-27
> **geo909 said:**
> Or just give the output of 

```
history | tail -20
```In the end you may have given the rm command in the
wrong place?


Even easier! look at that!

---

### Post by RichardC400 on 2011-09-27
[upto where i started going on a delete rampage ^^"  ]
history | tail -30

```

 
 1190  sudo su oracle
 1191  sudo su
 1192  sudo su
 1193  # oemctl stop oms user/password
 1194  # agentctl stop
 1195  # lsnrctl stop
 1196  sudo kill -9 pid 
 1197  killall
 1198  killall -l
 1199  # cd $ORACLE_HOME
 1200  # rm -Rf *
 1201  cd $ORACLE_HOME
 1202  rm -Rf *
 1203  # cd $ORACLE_BASE
 1204  # rm -Rf admin doc jre o*
 1205  # cd $ORACLE_BASE
 1206  # rm -Rf admin doc jre o*
 1207  # rm /etc/oratab /etc/emtab
 1208  su
 1209  sudo su
 1210  cd ..
 1211  dir
 1212  cd lib
 1213  dir
 1214  sudo su
 1215  foremost-h
 1216  foremost -h

```

---

### Post by geo909 on 2011-09-27
Hmm.. My only guess is that the variables that you
were using are not the same any more when you are 
a different user.  Maybe $ORACLE_HOME is not set 
for root? 

So for instance could you do

```

sudo su
echo $ORACLE_HOME

```

If you get nothing, then that means that you probably did
a "rm -rf" inside the folder that you were into. That would
explain the fact that everything is deleted (except the
dot files -those are not affected by rm -rf - and the desktop
that was probably created again by your file manager or whatever).

---

### Post by RichardC400 on 2011-09-27
yeah i got nothing back

That means it's gone?

---

### Post by geo909 on 2011-09-27
> **RichardC400 said:**
> yeah i got nothing back

That means it's gone?

Hmmm.. My guess would be that you went to the root's home directory.. If you do "cd $VARIABLEWHICHISNOTSET" where
the last variable is not set, then it's the same as giving
a plain "cd". That would go to the home directory of the 
current user (in your case that would be root I think? You 
did a "sudo su" a little bit before).

In which folder are you missing your stuff? From 
*/home/yourusername* or from */root*?

---

### Post by RichardC400 on 2011-12-28
Sorry for the late getting back, I didn't solve it, I just got everything from a backup I made.

(At least I was clever doing that lol)

---

