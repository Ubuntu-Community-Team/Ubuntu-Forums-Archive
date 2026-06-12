---
title: "How to delay command execution @ startup"
date: 2010-08-29
forum: General Help
---

### Post by haxxx on 2010-08-29
I have two applications that run in terminal @ startup. I got a command from a helpful member here, which makes them run both side by in one terminal. Problem is i need application 1 to start b4 Application 2. The command is:

gnome-terminal --tab -e "sh -c '/home/user/app1; read a'" --tab -e "sh -c '/home/user/app2; read a'"

Also App1 terminal needs to remain open while app2 could close after a few seconds.
Any help would be greatly appreciated.
thanks

Haxxx.

---

### Post by Smart Viking on 2010-08-29
You could somehow use the "sleep" command, you enter sleep followed by how many secounds:

```
sleep 3 && gnome-terminal
```Will wait three secounds before launching gnome-terminal. :)

---

### Post by Vaphell on 2010-08-29
nah, it's not what he needs. He wants to launch the 2nd tab with a delay and it's tricky. IIRC gnome-terminal is unable to add a tab to itself later so the only choice i see in this form is to add a sleep to the 2nd command (sleep n; /home/user/app2; ...) but it will require setting the delay big enough to app1 to finish. I don't know how to communicate between the tabs without adding some additional mechanism. That mechanism could work like that:
1. file 'app1.ok' is created after successful execution of app1

```
 app1 && touch app1.ok
```

2. while app2 is inside the script and before the app2 there is a loop that checks the file existence every lets say 5 secs and only success breaks the loop so app 2 can be executed.

```

#!/bin/sh

while [ ! -f 'app1.ok' ]
do
  echo 'waiting for App1 to finish...'
  sleep 5  
done 

echo App1 finished, starting App2.
app2
rm app1.ok

```

the same thing in a one-liner form, you can try to paste it into the sh -c part:

```
file=`echo app1.ok`; while [ ! -f $file ]; do echo waiting for App1 to finish...; sleep 5; done; echo App1 finished, starting App2; app2; rm $file
```
read a is to wait for the user input to close, replace it with sleep 10 if you want so it will wait 10s and then close automatically.

---

### Post by haxxx on 2010-08-29
Ahhh.. Vaphell, I should've mentioned, this is just my third week using Linux.
i'm not sure i understand much of what u wrote. Also I don't have a problem with both apps running in individual terminals if it makes it easier.

---

### Post by Vaphell on 2010-08-29
my idea was:
app1 and app 2 are run separately and it's not so easy to synchronize them so one is after the other
trick: app1 announces completion by creating a file, which simply acts a signal for that fancy script with app2 inside to break from the loop (waiting for app1 to finish) and to run app2 finally
app1: run, send a signal 'ok, it's your turn, app2'
app2: wait for signal, wait for signal, ..., ok got signal, run


simply get into the bash scripts, stuff i used is fairly basic, it's like 1hr of learning :)

a && b means 'run b if a was successful'

while [ ! -f 'app1.ok' ]; do echo 'waiting for App1 to finish...'; sleep 5; done;  
means do stuff between do and done when file app.ok does not exist ( -f = file exists, ! = negation)
every time file is not found, print 'waiting' wait 5 secs and try again
once the condition is met (file exists = app1 is finished) script moves forward and finally executes app2 part thus making sure that app2 is after app1
 
you can do the same without the file - grep command looks for occurences of a given pattern, so running ps ux (list all processes of the user) and letting the output through grep app1 would result in an empty string if the app1 process is no more.
ps ux | grep <name>


opening another terminal makes it easier because you can do app1; gnome-teminal -e app2 so the window with app2 will be always opened after app1 is finished

either way if you created the script app2_launcher with that code (app2 would need to be a valid path/name of course) you'd be able to run
```
gnome-terminal --tab -e "sh -c '/home/user/app1 && touch app1.ok; read a'" --tab -e "sh -c '/path/app2_launcher; sleep 10'"
```
or with oneliner with no additional scripts
```
gnome-terminal --tab -e "sh -c '/home/user/app1 && touch app1.ok; read a'" --tab -e "sh -c 'file=`echo app1.ok`; while [ ! -f $file ]; do echo waiting for App1 to finish...; sleep 5; done; echo App1 finished, starting App2; /home/user/app2; rm $file; sleep 10'"
```
scripts make the whole thing cleaner though, you can put all the stuff inside them and your command becomes a simple  terminal --tab -e "/path/script" --tab -e "/path/script2" :)

edit:
version without file but with grep
```
gnome-terminal --tab -e "sh -c '/home/user/app1; read a'" --tab -e "sh -c 'while `ps ux | grep app1 | grep -vq grep`; do echo waiting for App1 to finish...; sleep 5; done; echo App1 finished, starting App2; /home/user/app2; sleep 10'"
```

---

### Post by haxxx on 2010-08-31
Hey Vaphell i appreciate all ur efforts, ur a trooper, but i think the problem is that app 1 never really ends, its listening on a port. so there's a loop in app2 terminal just waiting for app1 to end. if ur tired i understand it's a stressing me out watchin u work!

thanks

---

### Post by haxxx on 2010-09-04
:DThanks a lot Vaphell, I eventually went with the command you gave 
below. ran that for both apps (separate terminals) with a 10s sleep in app2 terminal.
 
 
gnome-terminal --tab -e "sh -c '/home/user/app1; read a'"
 
Thanks a lot again for your patience.

---

