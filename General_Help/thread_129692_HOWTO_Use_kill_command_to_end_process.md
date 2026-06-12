---
title: "HOWTO: Use kill command to end process"
date: 2006-02-14
forum: General Help
---

### Post by Garyu on 2006-02-14
As a new linux/Ubuntu user, I have had some difficulties understanding the "kill" command to end a process that has frozen or is just unwanted for some mysterious reason. I thought it was difficult to figure out, and I didn't find anything in the forum about it, so now I am writing this HOWTO to help others like myself. If you think I should add something, just reply below or send me a private message. (not sure where to post this, so moderators feel free to move)

Before we begin I might say that there is a tool in Gnome for this, called the System monitor. You can find this in your main menu at Applications -> System Tools -> System monitor. However, this tool does not list all of your processes, so the kill command might still come in handy. (Oh, and if you just want to kill something running in a window, try adding the "Force quit" to one of your panels and you get a mouse operated kill tool)

**Syntax of the kill command is:**
```
 kill [-s sigspec | -n signum | -sigspec] [pid | job]
```
The sigspec is what kind of a signal you want to send to your process. This is a value between 1 to 64. If you want to know which one is which you can type "kill -l" in a terminal. The signals are usually a range from friendly to hostile ways of saying "I don't want you running no more". For example:
**kill -1** would mean something like "please save your data and exit"
**kill -15** (default) would mean something like "just quit, will you? I don't care if you save or not"
**kill -9** would mean something like "die you bastard, die!"

So now we have to define which process we want to send this signal to. This is done by providing the PID (Process ID). So what if we don't know the PID, or maybe even don't know if the process is running or not. Well, then we have to use a different command: "ps"
```
ps -A
```
The above code will list all of the processes running on your computer. If you only run "ps" you will get a list of processes started from the terminal you are currently running. If you run "ps x" you will get a list of processes that are not connected to a terminal, like gnome components. However, "ps -A" will usually return a lengthy list of processes, and if you want to save a few seconds looking for "your" process there is an easy way of sorting out the essentials of the list: grep. 
```
ps -A | grep name_of_my_process_I_want_the_PID_of
```

The PID is the number displayed to the left of each process in the list that comes up from your command. So just find the process you want to terminate and write down the PID on that row. If I for example run "ps" in a terminal right now, I find out that bash, the shell, has PID 11424 in this terminal. So if I want to ask bash to please exit from memory I will just type:
```
kill -1 11424
```
*POOF* My terminal window is gone, because I removed it's protective shell and my gnome ate the contents. :cool: 

Now, a warning might be in place here. Do not kill processes if you don't know what it is. The consequences might be dire. Killing sprees are for games only.

**EDIT: About killall command:**
There is another command that might be useful to know, if you know the name of a process but not the PID and think "ps -A | grep process" is difficult to use, you can use killall like so:
```
killall bash
```
Is supposed to do the same as "kill -1 11424" in the above example, only that the sigterm will be 15, so it's a lot more hostile and will not allow the process to save any data. Anyhow, when I do it, guess what, nothing happens. But it's supposed to work like that. :P

---

### Post by Robgould on 2006-02-14
Very nice how to.  Well written and thourough.  Thank you.  
 
One of the reasons I am replying is that I can find this easy later.

---

### Post by gremlin hunter on 2006-02-14
Th killall command is alot more newb friendly.

---

### Post by engla on 2006-02-14
[QUOTE=Garyu]
**kill -9** would mean something like "just quit, will you? I don't care if you save or not"
**kill -15** (default) would mean something like "die you bastard, die!"
[/QUOTE]

Oops, a small typo! These two signals should be exchanged (-9 is the strongest signal, -15 is the default signal).

The signals actually both have numbers and names, and you can use either one. The default one is -15 or -TERM (for terminate). There is a stronger version called -9 or -KILL, which will do the "die bastard, die!" thing. So when -15 doesn't work, try -KILL!

---

### Post by Garyu on 2006-02-15
[QUOTE=engla]Oops, a small typo! These two signals should be exchanged (-9 is the strongest signal, -15 is the default signal).[/QUOTE]

Now that is just ridiculous. I don't know who was the brilliant mathematician behind this system, but to me it seems obvious that it is easier if the grade continues upwards rather than follow a sinus format. Also, I haven't found an explanation for the other 50 or so signals that can be sent. The short names you get from "kill -l" doesn't say very much to me...

Thanks for the head up though. :)

---

### Post by Robor on 2006-02-15
Very nice HowTo there.  I'd like to add something that I've found helpful.

If you use the 'grep' command in combo with the ps command you can search for the PID of a program from running process.  For example:  

ps -A | grep gaim

That command will search all running processes for the gaim process.  Here's the output in my case:

robor007@HOME-T42-UBUNTU:~$ ps -A | grep gaim
 8701 ?        00:01:08 gaim

So if Gaim had crashed and wouldn't close or worse yet had crashed and wouldn't allow me to reopen it I could check to see if it was already running and kill the bad process (in this case PID 8701).

---

### Post by Gustav on 2006-02-15
A little easier way to kill aps with GUI is to use xkill which just let you click at a window to kill it. You don't need to know the PID or even name of the program.

You can start it by typing xkill in terminal or you can add a xkill applet in your panel.

---

### Post by Robor on 2006-02-15
Wow, that XKill is a pretty cool tool.  I added it to my drawer.  Thanks!  :D

---

### Post by dragonflyFZX on 2006-02-15
isn't xkill the same as just pressing crtl-alt-esc (and then your pointer becomes a skull and you just click the program you want to kill)?  Or am i missing something?

---

### Post by Garyu on 2006-02-16
[QUOTE=Gustav]A little easier way to kill aps with GUI is to use xkill which just let you click at a window to kill it. You don't need to know the PID or even name of the program.

You can start it by typing xkill in terminal or you can add a xkill applet in your panel.[/QUOTE]

If you would have read everything I wrote, you might have noticed that I already mentioned this in the howto. ;)

---

### Post by Garyu on 2006-02-16
[QUOTE=dragonflyFZX]isn't xkill the same as just pressing crtl-alt-esc (and then your pointer becomes a skull and you just click the program you want to kill)?  Or am i missing something?[/QUOTE]

Yes, it is the same, BUT in Ubuntu there is no Ctrl-Alt-Esc shortcut. At least it doesn't work for me and never has. So I have used the panel applet until I had to get rid of something that wasn't in a window so I had to figure out the kill command. :)

---

### Post by kabus on 2006-02-16
[QUOTE=Garyu]
So now we have to define which process we want to send this signal to. This is done by providing the PID (Process ID). So what if we don't know the PID, or maybe even don't know if the process is running or not. Well, then we have to use a different command: "ps"
[/QUOTE]

or 

```
pidof *program*
```

---

### Post by Gustav on 2006-02-16
[quote=Garyu]If you would have read everything I wrote, you might have noticed that I already mentioned this in the howto. [/quote]

Oh, didn't see that.

---

