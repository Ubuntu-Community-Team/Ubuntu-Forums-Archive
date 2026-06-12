---
title: "Java Problem"
date: 2005-03-15
forum: General Help
---

### Post by motuvaa on 2005-03-15
I have done everything what is in the tutorial.
But when I start my ubuntu and open terminal it says: 
bash: /usr/java/jdk1.5.0_02/: is a directory
Tutorial says that Ill have to append next lines : 

JAVA_HOME=/usr/java/jre1.5.0_01
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

I don't know what to do.. (Newbie, using ubuntu for 3days)  ](*,)

---

### Post by tomchuk on 2005-03-15
You've put "/usr/java/jdk1.5.0_02/" in one of your shell's profile scripts. Did you edit ~/.bashrc, ~/.bash_profile, /etc/profile, /etc/bash.bashrc - check these for the line you quoted.

If you put those lines into /etc/profile they should take effect for newly spawned shells. Make sure you change JAVA_HOME to the path where you installed your jdk or jre - it looks like /usr/java/jdk1.5.0_02, not /usr/java/jre1.5.0_01

---

### Post by the Blow Leprechaun on 2005-03-15
[QUOTE=motuvaa]
Tutorial says that Ill have to append next lines : 

JAVA_HOME=/usr/java/jre1.5.0_01
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

I don't know what to do.. (Newbie, using ubuntu for 3days)  ](*,)[/QUOTE]

All you have to do is open up /etc/bash.bashrc in whatever text editor you like (I use vim, but you could just as easily use nano or something else) and add those lines. I put them at the end, and it's worked for me. 

The way I read your post, you seemed to feel like it wanted you to append those lines to the directory... notice the last line of the instructions before that, gedit /etc/bash.bashrc - that's opening the file where it goes in a text editor (though I think gedit is an ugly program).

Maybe I don't understand your confusion?

---

### Post by motuvaa on 2005-03-16
I append those lines end of  the /etc/bash.bashrc but it says 
bash: /usr/java/jdk1.5.0_02/jre: is a directory
Its weird because howto says that all I need to do is append those lines..  :-s

---

### Post by tomchuk on 2005-03-16
Can you post the output of the following commands:
```

grep -H "/usr/java/jdk1.5.0_02/jre" {/etc/{bash.bashrc,profile},~/.bashrc,~/.bash_profile}

grep -A4 "JAVA_HOME" /etc/bash.bashrc

echo $JAVA_HOME

echo $PATH

```

---

