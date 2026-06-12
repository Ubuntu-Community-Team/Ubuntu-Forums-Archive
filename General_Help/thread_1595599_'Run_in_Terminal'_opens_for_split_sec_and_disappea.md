---
title: "'Run in Terminal' opens for split sec and disappears? (dbgl)"
date: 2010-10-13
forum: General Help
---

### Post by Jonatello on 2010-10-13
Hi everyone, I hope I'm not reposting something that is asked a lot. I used the search feature first to try and find the same issue, and found nothing that truly matches what I'm experiencing.

(also: I'm brand new to Ubuntu this week. love it so far!)

Here's the current issue:

I'm supposed to run this dbgl file (front end for dosbox) in terminal like the tutorial i'm viewing says, but everytime i click "Run in Terminal", the Terminal shows up for a split-second and then disappears. Nothing else shows up. Nothing else opens.

Is this common? How do i solve this?

---

### Post by emoguitarist06 on 2010-10-13
Can you post the link for that tutorial?

---

### Post by oldos2er on 2010-10-13
You need to open a terminal (Applications, Accessories, Terminal), change directory to where dbgl.sh is, and run it from there.

---

### Post by emoguitarist06 on 2010-10-13
> **oldos2er said:**
> You need to open a terminal (Applications, Accessories, Terminal), change directory to where dbgl.sh is, and run it from there.

What Jonatello is doing should work the same as your method

---

### Post by Jonatello on 2010-10-13
> **emoguitarist06 said:**
> Can you post the link for that tutorial?

sure, here you go: [http://www.youtube.com/watch?v=WLRg7cvqPWY](http://www.youtube.com/watch?v=WLRg7cvqPWY)

---

### Post by Jonatello on 2010-10-13
> **oldos2er said:**
> You need to open a terminal (Applications, Accessories, Terminal), change directory to where dbgl.sh is, and run it from there.

lol i'm such a terminal newbie...i've changed to the proper directory, but not sure what syntax/grammar to use in order to run dbgl.sh

---

### Post by emoguitarist06 on 2010-10-13
> **Jonatello said:**
> lol i'm such a terminal newbie...i've changed to the proper directory, but not sure what syntax/grammar to use in order to run dbgl.sh

This should do it
```
./dbgl.sh
```

Unfortunately I'm at work and we don't have flash :c

---

### Post by Jonatello on 2010-10-13
> **emoguitarist06 said:**
> This should do it
```
./dbgl.sh
```Unfortunately I'm at work and we don't have flash :c

hmm, it said "no such file or directory"

here's where i'm at in terminal:

```
Jonatello@Spartacus:~/DosBoxGameLauncher$ 
```

(Spartacus is my computer's name. the dbgl file is in the DosBoxGameLauncher folder)

from there i went like this: 

```
Jonatello@Spartacus:~/DosBoxGameLauncher$ ./dbgl.sh
```

that's when it said no such file or directory

...as for the flash video, no problemo...i just really appreciate the help so far!

---

### Post by oldos2er on 2010-10-13
You may need to make it executable first. **chmod a+x dbgl.sh** Then **sh ./dbgl.sh**

---

### Post by Jonatello on 2010-10-14
> **oldos2er said:**
> You may need to make it executable first. **chmod a+x dbgl.sh** Then **sh ./dbgl.sh**

when i type **chmod a+x dbgl.sh** after changing to the proper directory, it says "no such file or directory"

i must not be doing it right?

also, any thoughts to what might be causing the terminal to only flash open for a split second and disappear when i click "run in terminal"?

---

### Post by oldos2er on 2010-10-14
> **Jonatello said:**
> when i type **chmod a+x dbgl.sh** after changing to the proper directory, it says "no such file or directory"

i must not be doing it right?

We just need to find out where it is. Can you post the output of **ls -R ~/DosBoxGameLauncher** ?

> **Jonatello said:**
> also, any thoughts to what might be causing the terminal to only flash open for a split second and disappear when i click "run in terminal"?

The problem with 'Run in terminal' is when the task completes, the terminal closes so fast you can't see what's going on, whether there were errors, etc. Working with shell scripts is much easier in an CLI environment, in my opinion.

---

### Post by gandaran on 2010-10-14
> **Jonatello said:**
> Hi everyone, I hope I'm not reposting something that is asked a lot. I used the search feature first to try and find the same issue, and found nothing that truly matches what I'm experiencing.

(also: I'm brand new to Ubuntu this week. love it so far!)

Here's the current issue:

I'm supposed to run this dbgl file (front end for dosbox) in terminal like the tutorial i'm viewing says, but everytime i click "Run in Terminal", the Terminal shows up for a split-second and then disappears. Nothing else shows up. Nothing else opens.

Is this common? How do i solve this?
Jonatello
open the terminal, go to edit » profile preferences » command tab and choose to keep the terminal open in the command box.
run that command now, the terminal wont close.

---

### Post by Jonatello on 2010-10-15
> **gandaran said:**
> Jonatello
open the terminal, go to edit » profile preferences » command tab and choose to keep the terminal open in the command box.
run that command now, the terminal wont close.

aha! 

ok i think we may be getting somewhere...i followed your guidance and then "ran in terminal"

it stayed open this time, and this is what it says:

/home/myuser/DosBoxGameLauncher/dbgl: 4: /usr/bin/java: not found

i'm guessing this means i need to install some kind of java somewhere?

---

### Post by oldos2er on 2010-10-15
Enable the partner repository, System, Administration, Synaptic Package Manager, Settings, Repositories, Other Software tab, tick 'Canonical Partners' boxes. Reload the sources list, and install sun-java6-jre.

---

### Post by Jonatello on 2010-10-15
> **oldos2er said:**
> We just need to find out where it is. Can you post the output of **ls -R ~/DosBoxGameLauncher** ?



The problem with 'Run in terminal' is when the task completes, the terminal closes so fast you can't see what's going on, whether there were errors, etc. Working with shell scripts is much easier in an CLI environment, in my opinion.

gandaran showed me how to keep the terminal from closing (edit>profile preferences>title and command>when command exits), which revealed something about java not being found. maybe we're onto something? maybe i need some kind of java installed?

here's that output (and first time i typed Is rather than ls (i rather than L) which shows you how new i am to this thing lol)


myuser@Spartacus:~$ ls -R ~/DosBoxGameLauncher
/home/myuser/DosBoxGameLauncher:
captures  db    dbgl.jar     dosroot  lib       templates
COPYING   dbgl  DOSBox-0.74  export   profiles  xsl

/home/myuser/DosBoxGameLauncher/captures:

/home/myuser/DosBoxGameLauncher/db:

/home/myuser/DosBoxGameLauncher/DOSBox-0.74:
AUTHORS  ChangeLog  COPYING  dosbox  dosbox.conf  INSTALL  NEWS  README  THANKS

/home/myuser/DosBoxGameLauncher/dosroot:

/home/myuser/DosBoxGameLauncher/export:

/home/myuser/DosBoxGameLauncher/lib:
commons-lang-2.5.jar  hsqldb.jar  J7Zip.jar  swing2swt.jar  swt.jar

/home/myuser/DosBoxGameLauncher/profiles:

/home/myuser/DosBoxGameLauncher/templates:
0.conf  1.conf  2.conf  3.conf  4.conf

/home/myuser/DosBoxGameLauncher/xsl:
fancy_html.xsl  simple_csv.xsl  simple_txt.xsl
myuser@Spartacus:~$

---

### Post by Jonatello on 2010-10-15
> **oldos2er said:**
> enable the partner repository, system, administration, synaptic package manager, settings, repositories, other software tab, tick 'canonical partners' boxes. Reload the sources list, and install sun-java6-jre.

success!! Big thanks! :) :)

---

