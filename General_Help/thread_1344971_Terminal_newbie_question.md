---
title: "Terminal newbie question"
date: 2009-12-03
forum: General Help
---

### Post by maximilianyuen on 2009-12-03
Sometime when I typed some commands in terminal, and after it display some messages, the terminal stop functioning as terminal
(especially when those are some errors message)

i.e. this thing will disappear:
```

        ubuntu@ubuntu-laptop:~$
```

and anything I typed will become plain text, all usual command will have no effect

is there any simple way to recover that "ubuntu@ubuntu-laptop:~$" without restarting terminal?

---

### Post by endBc on 2009-12-03
Have you tried Ctrl+Z ?

---

### Post by maximilianyuen on 2009-12-03
> **endBc said:**
> Have you tried Ctrl+X ?

o? i just tried ctrl+c

when I am in this situation again then I will try....

i forgot what command I used render this situation

thanks

---

### Post by NoaHall on 2009-12-03
> **endBc said:**
> Have you tried Ctrl+X ?

Ctrl + c. Ctrl + x doesn't kill it. Ctrl +z pauses it.

---

### Post by endBc on 2009-12-03
> **maximilianyuen said:**
> o? i just tried ctrl+c

when I am in this situation again then I will try....

i forgot what command I used render this situation

thanks

Sorry for the typo - not X but Z. Like if you open a man page, Ctrl+C will not help you, tough you'll be able exit with Ctrl+Z.

---

### Post by maximilianyuen on 2009-12-03
I will ctrl x or ctrl z next time , whichever working :)

---

### Post by blackened on 2009-12-03
> **endBc said:**
> Sorry for the typo - not X but Z. Like if you open a man page, Ctrl+C will not help you, tough you'll be able exit with Ctrl+Z.

You only need to press Q (for quit) to exit viewing of a man page.

---

### Post by renkinjutsu on 2009-12-03
if CTRL+C doesn't work, you can:

CTRL+Z to pause whatever process and send it to the back
then you can kill it with: kill %1

---

### Post by maximilianyuen on 2009-12-03
> **blackened said:**
> You only need to press Q (for quit) to exit viewing of a man page.



nope, that is not a man page, nor the Q button work....

I really forgot what kind of error message and what type of command I ran, but definitely not man page

---

### Post by blackened on 2009-12-03
> **maximilianyuen said:**
> I really forgot what kind of error message and what type of command I ran, but definitely not man page

What you're describing typically happens when you start a program or executable file from the terminal. When you do this, said program runs as a sub-process of that particular terminal window. As was previously pointed out, use CTRL+C to quit, or CTRL+Z to pause, that process and return you to a command prompt.

---

### Post by endBc on 2009-12-03
> **blackened said:**
> You only need to press Q (for quit) to exit viewing of a man page.
 
That was just an example, tough I'm a little bit confused now. 
If I run a Python application ( GUI ) and press Ctrl+Z, it simply crashes ( *application not responding* ) :-s

---

### Post by blackened on 2009-12-04
> **endBc said:**
> That was just an example, tough I'm a little bit confused now. 
If I run a Python application ( GUI ) and press Ctrl+Z, it simply crashes ( *application not responding* ) :-s

Remember, ctrl+z pauses the program, so it will stop responding. In fact, you should get a message in the terminal window that reads 
```
[1]+  Stopped                 *Application Name*
```

Once this happens you have a couple of options:

since you will typically have only one job suspended, you can reactivate the application and bring it to the forground with
```
fg
```

alternatively, you could reactivate the application in the background with
```
bg
```

you can list all jobs by typing simply
```
jobs
```

and finally you can kill a job with (%N is the job number)
```
kill %N && fg
```

Hope that makes it a little more clear.

---

### Post by maximilianyuen on 2009-12-04
> **blackened said:**
> What you're describing typically happens when you start a program or executable file from the terminal. When you do this, said program runs as a sub-process of that particular terminal window. As was previously pointed out, use CTRL+C to quit, or CTRL+Z to pause, that process and return you to a command prompt.


um....ya you are right. 

but let's say I opened terminal then typed pidgin

then my terminal will become useless unless I stop or pause pidgin?
that's kind of defeat the purpose....

so 
1) how can I open an application like pidgin, and continue to use the terminal without stopping / pausing pidgin or close and re-open terminal?

or I must pause it first and then type bg ?


i know there is alt f2 for this but lets say I want to just use terminal

---

### Post by maximilianyuen on 2009-12-04
just randomly tried and seems typing
```
pidgin &
```

is the answer?

---

### Post by endBc on 2009-12-04
> **maximilianyuen said:**
> just randomly tried and seems typing
```
pidgin &
```is the answer?

It'll fork the process in background and once you'll close the Terminal, it'll die.

---

### Post by maximilianyuen on 2009-12-04
> **endBc said:**
> It'll fork the process in background and once you'll close the Terminal, it'll die.


so really no answer to my question? :(

---

### Post by whitethorn on 2009-12-04
you could also try

```
nohup programname &
``` 

Press enter after the prgram starts to get to your promt line back.

---

### Post by maximilianyuen on 2009-12-04
> **whitethorn said:**
> you could also try

```
nohup programname &
```Press enter after the prgram starts to get to your promt line back.

thanks[ whitethorn!]("http://ubuntuforums.org/member.php?u=424805")
exactly the answer I am looking for :)


and thanks everyone helping as well ;)

---

### Post by bodhi.zazen on 2009-12-04
A popular alternate to nohup is screen. There is also disown ;)

---

### Post by maximilianyuen on 2009-12-04
> **bodhi.zazen said:**
> A popular alternate to nohup is screen. There is also disown ;)


ok you make me confuse and hate you. in a good way ;)

how come terminal got so many commands mixing and overlaping each another....

even just need a help can be man, can be -h, can be --help....
shutdown can be shutdown, halt.....reboot can be reboot, shutdown -r....

thanks to you (in a positive, appreciative way, of course):popcorn:

my new problem:

1)  when I use screen, or disown pidgin after I started it, using jobs or ps will not list the opened app
then how should I close them without leaving the terminal?

I dont want to use gnome-system-properties  to check out the ID.....

---

### Post by blackened on 2009-12-04
> **bodhi.zazen said:**
> A popular alternate to nohup is screen. There is also disown ;)

I second the use of screen. Especially if you like ncurses-based applications.

---

### Post by maximilianyuen on 2009-12-04
a quick update of my question: (same as #20)

my new problem:

1)  when I use screen, or disown pidgin after I started it, using jobs or ps will not list the opened app
then how should I close them without leaving the terminal?

I dont want to use gnome-system-properties  to check out the ID.....

---

### Post by chaanakya_chiraag on 2009-12-04
can't you just use ```
killall <name of program>
``` to kill it without even knowing the PID (process ID) of the application?  Or does that not even work?

---

### Post by maximilianyuen on 2009-12-04
> **chaanakya_chiraag said:**
> can't you just use ```
killall <name of program>
``` to kill it without even knowing the PID (process ID) of the application?  Or does that not even work?


thanks, thats work :)

I wish I knew the keyword of finding answer in google...

---

### Post by bodhi.zazen on 2009-12-04
> **maximilianyuen said:**
> a quick update of my question: (same as #20)

my new problem:

1)  when I use screen, or disown pidgin after I started it, using jobs or ps will not list the opened app
then how should I close them without leaving the terminal?

I dont want to use gnome-system-properties  to check out the ID.....

For screen see :

[http://www.cyberciti.biz/tips/linux-screen-command-howto.html](http://www.cyberciti.biz/tips/linux-screen-command-howto.html)

There are several cheat sheets available as well.

disown is used after you start a process in the background.

```
pidgin &

#list jobs
jobs

# disown
disown %1
```Example :

> # Start sleep in the background
bodhi@ufbt:~$ sleep 30 &
[1] 15169 <- See the number 1 here ? that is job 1 ;)

#list running jobs This lists tasks "owned" by the current shell
bodhi@ufbt:~$ jobs
[1]+  Running                 sleep 30 &

# disown
bodhi@ufbt:~$ disown %1

# sleep is not longer listed as a job and will continue if I close the terminal
bodhi@ufbt:~$ jobs

# sleep shows with ps aux :
bodhi@ufbt:~$ ps aux | grep sleep
[COLOR=green]**bodhi    15169  0.0  0.0   9444   808 pts/0    S    14:28   0:00 sleep 30**[/COLOR]
bodhi    15171  0.0  0.0   7524   892 pts/0    R+   14:28   0:00 grep sleep

---

### Post by bodhi.zazen on 2009-12-04
> **chaanakya_chiraag said:**
> can't you just use ```
killall <name of program>
``` to kill it without even knowing the PID (process ID) of the application?  Or does that not even work?

If that fails ...

```
kill -9 `pidof pidgin`
```

Those are back tics ` , on my keyboard by the number 1 , and not single quotes '

---

### Post by maximilianyuen on 2009-12-04
>>>>For screen see :
[http://www.cyberciti.biz/tips/linux-...and-howto.html]("http://www.cyberciti.biz/tips/linux-screen-command-howto.html")

this is too advance for me at the mean time :)


>>>kill -9 `pidof pidgin`

killall works fine for me :)
but this kill thing can be handy when I can can use -sigkill if needed

thanks!

---

