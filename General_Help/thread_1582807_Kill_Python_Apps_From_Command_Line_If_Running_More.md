---
title: "Kill Python Apps From Command Line If Running More Than One"
date: 2010-09-27
forum: General Help
---

### Post by dodo3773 on 2010-09-27
How do I kill a python application from the command line? For an example I have 2 applications running. The first is bleachbit and the second is furiusisomount. They are both python applications so they both come up as python under process name. I could kill them by ID number but I was hoping there was another way to do it so that it could be automated in a bash script. Does anyone know? Thank you in advance.

---

### Post by harrismh777 on 2010-09-27
Who wrote the python app?   Is it yours?

What are you *really* trying to do?

You can have your processes start so that they have unique names in ps. But you can also have your process write its process id to a unique file in /var/lock someplace by unique name so that you can retrieve the process id number from the named lock file. The latter technique is the one I default to on my own programs. There are other creative things you could do but....


... why do you want to *kill* these jobs rather than having them exit normally?  How are you killing them?  which signal?

:-k

---

### Post by niteshifter on 2010-09-27
Hi,

```
ps -f -C python
```
With a bit of AWK-ing, should get you what you need.

---

### Post by harrismh777 on 2010-09-27
no, that won't quite get it...

ALL of his python scripts will show as python. The ps -f -C python 
command will show all of the process ids in full formatting for every python script... but "which one" (by kind, type, function) matches each process number?

Either the processes need a unique name, or better, each process needs to write its process number to a lock file (by name) so that the automated script knows how to retrieve the process number for the "python" script of choice.

---

### Post by niteshifter on 2010-09-27
> **harrismh777 said:**
> no, that won't quite get it...

ALL of his python scripts will show as python. The ps -f -C python 
command will show all of the process ids in full formatting for every python script... but "which one" (by kind, type, function) matches each process number?

Either the processes need a unique name, or better, each process needs to write its process number to a lock file (by name) so that the automated script knows how to retrieve the process number for the "python" script of choice.

Let's see ...

Test case: 3 python app running, two from GNOME, one is mine, result of ps -f -C python shown below:
```
dlk@dlk-lt-1420:~$ ps -f -C python
UID        PID  PPID  C STIME TTY          TIME CMD
dlk       6882  6660  0 Sep26 ?        00:00:00 python /usr/share/system-config-printer/applet.py
dlk       6901     1  0 Sep26 ?        00:00:00 python /usr/lib/timer-applet/timer-applet --oaf-activate-iid=OAFIID:TimerApplet_Factory --oaf-
dlk      14918     1  0 02:22 ?        00:00:00 python /home/dlk/bin/pwg
dlk@dlk-lt-1420:~$

```

There is everything needed to tie a python script's name - **which the OP stated he knows** (and path, not hard to find) to it's PID and parent PID (if applicable). Even returns args supplied to the python script (second entry, truncated by gnome-terminal).

Lock files come with lock file maintenance requirements. Which can become complex. Not to mention what to do with not-written-by-you apps: Edit them and have them break on update / upgrade? 

I gave a KISS approach to the problem. YMMV.

---

### Post by dodo3773 on 2010-09-27
Wow thanks for the quick responses. I should elaborate a little more though. I am not writing or trying to write a python script. I am trying to write a bash script to kill python programs.  I already made a script to open multiple programs. It was simple I just used the "&" command i.e. firefox & evolution & bleachbit & furiusisomount". Now in order to close them with a different script I would use "pkill firefox evolution " but when I get to bleachbit the process name is python it is not bleachbit,  furiuiso mount is also called python. What I want to do is to know how to close one without closing the other. So pkill is probably out. Also, I do not want to use the ID number because from what I have seen that number changes every time and I want this to be a script that I can use on a regular basis. So the only option that I have left as far as I know is killall. But when I type in "killall python /usr/bin/bleachbit" bash does not know what I am talking about. I have also tried "python_/usr/bin/bleachbit" and just "/usr/bin/bleachbit". Still no luck. I hope that clears it up a little thank you.

---

### Post by harrismh777 on 2010-09-27
niteshifter missed my point...

... but don't miss his point !

Niteshifter's KISS approach (thanks) is too simple. In other words, it doesn't quite get it. The point he missed is that while the command:

   ps -f -C python

... will give you the process id you need to kill (by name and path) it is only not quite half the battle. It is easy (KISS) to tell someone to do a little awking, unless the person doesn't know how to awk. The second half of the problem (which has multiple solutions) is to pipe the output of the "ps -f -C python" command to grep, or pearl(regular expressions) or awk script, etc, in order to parse the process id based on the path and name you know like bleachbit. Using niteshifter's KISS approach will require you to write a parsing script to filter out the python's you don't want from the python /path/path/bleachbit that you do want. 

   The assumption that you know what to do with the output from

   ps -f -C python

    is too simple.  So, do you need help parsing the output from ps, or can you take it from here?


8-[

---

### Post by dodo3773 on 2010-09-27
> **harrismh777 said:**
> niteshifter missed my point...

... but don't miss his point !

Niteshifter's KISS approach (thanks) is too simple. In other words, it doesn't quite get it. The point he missed is that while the command:

   ps -f -C python

... will give you the process id you need to kill (by name and path) it is only not quite half the battle. It is easy (KISS) to tell someone to do a little awking, unless the person doesn't know how to awk. The second half of the problem (which has multiple solutions) is to pipe the output of the "ps -f -C python" command to grep, or pearl(regular expressions) or awk script, etc, in order to parse the process id based on the path and name you know like bleachbit. Using niteshifter's KISS approach will require you to write a parsing script to filter out the python's you don't want from the python /path/path/bleachbit that you do want. 

   The assumption that you know what to do with the output from

   ps -f -C python

    is too simple.  So, do you need help parsing the output from ps, or can you take it from here?


8-[
No I still need help if you would please. I figured it would be something like search for process id number then kill that id. Is that what you mean? Could you please tell me what to do? I do not know much about "awk". I will look it up now while I wait to hear from you. Thanks again.

---

### Post by envygeeks on 2010-09-27
I don't know what the point of all the replies in this thread are, since they provide no real input other than a small riff between the two users, but use pkill -f to kill the process so that you can kill it easily.

```

pkill -f "python script.py"

```

So if ps auxf returns: python /home/envygeeks/test.py
Do:

```

pkill -f "python /home/envygeeks/test.py"

```

Work out your pattern a bit so you don't end up killing accidental processes but that's the jist of it all.

---

### Post by dodo3773 on 2010-09-27
> **envygeeks said:**
> I don't know what the point of all the replies in this thread are, since they provide no real input other than a small riff between the two users, but use pkill -f to kill the process so that you can kill it easily.

```

pkill -f "python script.py"

```So if ps auxf returns: python /home/envygeeks/test.py
Do:

```

pkill -f "python /home/envygeeks/test.py"

```Work out your pattern a bit so you don't end up killing accidental processes but that's the jist of it all.
Thank You. This did it. This is exactly what I was trying to do. Worked perfectly. Problem solved.

---

### Post by niteshifter on 2010-10-01
> **envygeeks said:**
> I don't know what the point of all the replies in this thread are, since they provide no real input other than a small riff between the two users, but use pkill -f to kill the process so that you can kill it easily.

```

pkill -f "python script.py"

```

So if ps auxf returns: python /home/envygeeks/test.py
Do:

```

pkill -f "python /home/envygeeks/test.py"

```

Work out your pattern a bit so you don't end up killing accidental processes but that's the jist of it all.

Well, I was working toward a point but other stuff required my time. Sorry about that.

What was the point? The utility of the ps command. I was going to cover the awk that was needed along with bash's regex capabilities, possibly a bit of Perl as well.

But even pkill won't work as a general-case solution:

Problem 1: What to do with multiple instances of a python script?

Problem 2: What to do with an intermediate python script, that is a script started by a script?

Problem 3: How the Python interpreter was invoked matters. See following snip from a console:
```
dlk@dlk-lt-1420:~$ ps ax -f | grep -v grep | grep python
dlk       6932  6715  0 14:37 ?        S      0:00 python /usr/share/system-config-printer/applet.py
dlk       7026     1  0 14:38 ?        S      0:00 python /usr/lib/timer-applet/timer-applet --oaf-activate-iid=OAFIID:TimerApplet_Factory --oaf-ior-fd=29
dlk       7191     1  0 14:38 ?        Sl     0:01 /usr/bin/python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:Deskbar_Applet_Factory --oaf-ior-fd=81
dlk@dlk-lt-1420:~$ 

```
Note the last entry.

If there's any interest I'll post solutions.

---

### Post by dodo3773 on 2010-10-02
> **niteshifter said:**
> 

But even pkill won't work as a general-case solution:

Problem 1: What to do with multiple instances of a python script?

Problem 2: What to do with an intermediate python script, that is a script started by a script?

Problem 3: How the Python interpreter was invoked matters. See following snip from a console:


If there's any interest I'll post solutions.

I am still interested. Especially interested in Problem 1 above.

---

