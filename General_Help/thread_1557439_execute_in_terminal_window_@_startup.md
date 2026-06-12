---
title: "execute in terminal window @ startup"
date: 2010-08-20
forum: General Help
---

### Post by haxxx on 2010-08-20
I'm a two day old ubuntu baby, ver 9.04
I have two applications in my home folder (pgs & pgt) that run fine in a terminal window. I just enter ./pgs and ./pgt in their individual terminal windows and all is well.
I tried adding them to my startup list, but only the empty terminals open at 
startup. (missed windows for a minute). I've done some reading about
[COLOR=black][FONT=Courier New]gnome-terminal -x but couldn't follow it.[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]How do i get these two commands to run @ startup.[/FONT][/COLOR]
[COLOR=black][FONT=Courier New][/FONT][/COLOR] 
[COLOR=black][FONT=Courier New]Thanks[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]Haxxx.[/FONT][/COLOR]

---

### Post by silbak04 on 2010-08-20
Try going into startup applications (located in System-> Preferences -> Startup applications) then click on add and type this in the command /home/user_name/.pgs and do the same for ~./pgt...and let me know if that works if not, I'll come up with another solution

---

### Post by ScarletWyvern on 2010-08-20
You want these to programs to run in a terminal window at start up, right...?

gnome-terminal -e '~/.pgs'

Add that as a start up program.

---

### Post by haxxx on 2010-08-20
Sorry guys neither of those worked. Terminals open with error message
"there was an error creating the child process for this terminal.
silbak04, was i supposed to put my user name where you had user_name in your command. I didn't just wondered.
any other ideas?

---

### Post by ScarletWyvern on 2010-08-21
> **haxxx said:**
> Sorry guys neither of those worked. Terminals open with error message
"there was an error creating the child process for this terminal.
silbak04, was i supposed to put my user name where you had user_name in your command. I didn't just wondered.
any other ideas?
Yes, you should have put your name in there.

Try this as the startup command:

```
sleep 5 && gnome-terminal -e '~/.pgs'
```

---

### Post by silbak04 on 2010-08-21
> **ScarletWyvern said:**
> Yes, you should have put your name in there.

Try this as the startup command:

```
sleep 5 && gnome-terminal -e '~/.pgs'
```

or I think you might want to make a shell script first...```
#!/bin/bash
sleep 5 && gnome-terminal -e '~/.pgs'
```...after making a shell script...then add that into the start up application...

---

### Post by silbak04 on 2010-08-21
and yes you were supposed to put your user name where I had user_name...if you haven't tried that...do that first before making the shell script

---

### Post by haxxx on 2010-08-26
Had some hard drive problems, so i was out for a few days.
Here's what i've tried so far with no success.

Tried
1.gnome-terminal -e '~/.pgs'

The terminal window does open but has no text inside.
Error message: There was an error creating the child process for this terminal. 

2.sleep 5 && gnome-terminal -e '~/.pgs'
same result as #1.

Nothing happened.

3. created a new document in home folder
pasted the following text :

 #!/bin/bash
sleep 5 && gnome-terminal -e '~/.pgs'

saved it as pgs.sh

added the command: sleep 5 && gnome-terminal -e '~/.pgs'
to System-> Preferences -> Startup applications
same error message and blank terminal window. (also tried sleep 5 && gnome-terminal -e '~/.pgs.sh')

Oh by the way i also tried /home/dingo/.pgs (where dingo is my username) as silbak04 had suggested again nothing happened.
Any ideas left? By the way if i do manage to get it to run i want the terminal windows to remain open.

---

### Post by Vaphell on 2010-08-26
try /home/yourname/pgs, maybe invoked terminal doesn't recognize path aliases like ~ or . or has them wrong when given -e "command", sleep is not necessary imo.

i assume you want the window to stay to see the output?

try this
gnome-terminal --tab -e "sh -c '/home/user/app1; read a'" --tab -e "sh -c '/home/user/app2; read a'"

it's fugly (terminal execute " sh execute stuff ") but launcher with such command works, 2 tabs are created and both wait for user input to close - i tested it on pwd and ls

---

### Post by haxxx on 2010-08-27
Ok that worked splendidly thanks a whole lot Vaphell.
I wanted to make a change which would make everything smoother.
Unsure of the difficulty involved. The command you gave me opens both terminals in one window at the same time. Is it possible to have terminal A boot 8 seconds b4 terminal B
and stay open, then termial B loads but is temporary 5 seconds or so then closes. I suppose u would slip a sleep command in there somewhere. Thanks again everyone for the help.

Haxxx

---

