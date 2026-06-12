---
title: "SSH question - SSH'ing into an already open terminal on host"
date: 2011-08-18
forum: General Help
---

### Post by zero2xiii on 2011-08-18
Hay all,

I am able to access my ubuntu 10.04 over the internet with SSH. My question however is how can I SSH into an already open terminal.

I want to run a script in terminal which I want to be able to access from the outside trough a SSH tunnel. This script cant be launched over the SSH as it needs to be running 24/7 and be accessable at various times (and IF possible, by different users than the one that initialized the script on the host)

Is this possible? If so, how can I proceed in setting up something like this?

Many thanks

---

### Post by electriceddy on 2011-08-18
What I do is as soon as I connect through SSH I run Screen, then I run the script or process within Screen and detatch from it using CTRL+A d
 
Patrick

---

### Post by CharlesA on 2011-08-18
> **electriceddy said:**
> What I do is as soon as I connect through SSH I run Screen, then I run the script or process within Screen and detatch from it using CTRL+A d
 
Patrick
That's what I do as well.

Not sure if you can access an already running terminal session.

---

### Post by slugmax on 2011-08-18
It sounds like GNU screen may be what you want. You start the script in a screen session, detach and logout - at that point, it will stay running and be accessible to you if you ever re-attach to the same screen session. You can start here for more details:

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

---

### Post by electriceddy on 2011-08-18
Not sure if you can either.  Great thing about screen is the next time you ssh into the box you can run screen -ls get a list of all the screens and then attach using screen -r nameOfScreen.

---

### Post by g1njackal on 2011-08-18
Agree with above, screen is the best way I've tried so far. I've been using the same screen session since the uptime of my machine despite numerous ssh logins and accidentally closing terminal.

---

### Post by zero2xiii on 2011-08-18
Wow.

Thanks for the speesy reply's.

I got this working to a point:

I opened up a terminal on host (A) and typed "screen"
Then I went to the client (B) and SSH'ed into A. It worked and im logged into a blank terminal.

When I run "screen -ls" i get:
```
There is a screen on:
31036.pts-1.zeroburn-server  (time stamp)  (Attached) 
1 Socket in /var/run/screen/S-zeroburn
```

What is the name I need to use to attach to this screen? When I try "31036.pts-1.zeroburn-server" it gives an error. Is this because the status is "attached"?

How can I detach on A without killing the running script?

---

### Post by zero2xiii on 2011-08-18
Never mind,

I got it to detach with that ctrl + A d.

Now the client is attached, but now the server cant view the terminal currently open. Can this be done (allowing two 'attaches' to the same terminal), even if one is only viewing and not interacting?

SOLVED: aaaaauhm, another thing.. How do I kill the "virtual terminal" (duno what else to call it hehe). because even after closing all terminal screens on the server, the ssh'ed (client) pc still gets a terminal with "screen -ls"

I just typed "exit".. Seemed to do the trick..

---

### Post by eentonig on 2011-08-18
> **zero2xiii said:**
> Never mind,

I got it to detach with that ctrl + A d.

Now the client is attached, but now the server cant view the terminal currently open. Can this be done (allowing two 'attaches' to the same terminal), even if one is only viewing and not interacting?

```
man screen
```


In short, yes it can be done. Read the screen manpage to see hos to configure IT to behave as you want IT. 

Ps. Google 'byobu', as this is ubuntu implementation of screen.

---

### Post by seawolf167 on 2011-08-18
> **electriceddy said:**
> What I do is as soon as I connect through SSH I run Screen, then I run the script or process within Screen and detatch from it using CTRL+A d
 
Patrick

+1 for this

---

### Post by zero2xiii on 2011-08-18
> In short, yes it can be done. Read the screen manpage to see hos to configure IT to behave as you want IT. 

Ps. Google 'byobu', as this is ubuntu implementation of screen.

Oka, Im lost.

I read the man page and found:

>  C-a M       (monitor)     Toggles monitoring of the current window.

and when I do it, it gives me a notice that monitor mode is enabled, but the client still cant connect?

I googled that byobu but cant make head or tale, when i run byobu in the terminal, (detached) it attaches me to the fisrt availible screen it seems, but non of the byobu bindings work (the F keys).

But screen seems to work fine, so i dont want to mess with yet another application over this one.. all i wish is to be able to view the terminal on the server while being SSH'ed into the same terminal from another computer... haha.. Ouch, my brain is starting to hurt.. :confused:

---

### Post by CharlesA on 2011-08-18
byobu is just "screen" with some extra stuff.

I've had problems with it so I just use screen.

I think the "monitor" option for screen is used to listen for output / null output and send a bell if it sees it.

---

### Post by zero2xiii on 2011-08-20
Hay all,

Thanks for the input.

I will just detach from the running terminal. Being able to view activity in the script is not a huge issue. As this will only be used by two people (myself and one other person), I don't see the need to go to great lengths to get this working.

Thanks for all your insets. greatly appreciate it :D

---

### Post by Habitual on 2011-08-20
I know it says solved, but here's what I have done for the same task-based solution:

Launch gnome-terminal locally and then type screen and connect to Server1. Detach from Server1 (Ctrl+A+D)
Type screen -ls and note the screen session identifier.

type screen again and connect to Server2. Detach from Server2. Detach from Server2 (Ctrl+A+D)
Type screen -ls and note the screen session identifier.
Screen for Server1 in this example is 5128
(actual here is "28504.pts-1.My-Kungfu	(Detached)" **28504** is what you are looking for.
Screen for Server2 in this example is 5150

Make an qscreens.sh file in your $PATH somewhere and add these 2 commands:

```
#!/bin/bash
gnome-terminal --tab-with-profile=default --title=Server1 -e "screen -x 5128" --tab-with-profile=default --title=Server2 -e "screen -x 5150"
```
Save the file and open terminal > 
```
chmod 700 /path/to/qscreens.sh
```

Now you can type qscreens.sh or Alt+F2 and run qscreens.sh and you are instantly (re)connected to Server1 in one tab and Server2 in another tab.

NOTE: if you close the "new" gnome-terminal window with these 2 tabs open, just re-run qscreens.sh and you're back in business.

Hope that helps.

Enjoy.

---

