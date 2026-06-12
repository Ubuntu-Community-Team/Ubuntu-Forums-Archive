---
title: "Keep a proccess running from ssh"
date: 2010-05-21
forum: General Help
---

### Post by Vrekk on 2010-05-21
Ok the title is a little bit missleading, and I didn't know how to say it in a few words, so here is the whole storry.

I recenlty set up a headless linux home server by my router will my spare computer parts.  I have NFS and even a COD4 server running on it for my friends and me.  Because the box is headless, I take controll over it with ssh and start the COD4 server from there, but the problem is, if I close the terminal I have the ssh running from, it closes my server, meaning my desktop needs to be up and running the entire time.  That kinda ruins the point of my server :(

So my question is, is there a way for me to run the command so that it will not close with the terminal AND that I can still send commands to the server.

Sorry if I wasn't clear in the title.

---

### Post by DougieFresh4U on 2010-05-21
I am not sure, but a long time ago I used the **nohup** with the command and I was able to close terminal. Sorry if that's not what you are needing.

---

### Post by BoneKracker on 2010-05-21
nohup is supposed to be able to do this, but I've had problems using it.

The best way I've found is to use screen (which is an awesome little tool and a real godsend if you work remotely on servers):

[http://nathan.chantrell.net/old-stuff/linux/an-introduction-to-screen/](http://nathan.chantrell.net/old-stuff/linux/an-introduction-to-screen/)

After you connect via ssh, you just type 'screen'.
Then you do your work.
When you have to leave, but you want that login session to continue uninterrupted, you just "detach" (ctrl+a d).
Then you can terminate your ssh connection.

Later you connect via ssh again, and you "re-attach" by typing 'screen -r', and there's your last session, still running.

It can do a hundred other things too, like give you multiple shells in the same window without having to open multiple ssh connections.  You can also use it from the server itself, go to another machine or home, and continue working (or monitoring a long-running process).  You can also use it to let someone else simultaneously access the same terminal session you are working in.

---

### Post by amauk on 2010-05-21
```
nohup /path/to/program 2>&1 > /path/to/logfile.log &
```

Runs program in background
program will not "hang up" when controlling terminal hangs up
instead, will continue running as a daemon process

Because there is no controlling terminal, any output produced by program needs to be directed somewhere

above redirects everything to a file
Can, if desired, direct everything to /dev/null instead

---

### Post by Vrekk on 2010-05-21
> **amauk said:**
> ```
nohup /path/to/program 2>&1 > /path/to/logfile.log &
```

Runs program in background
program will not "hang up" when controlling terminal hangs up
instead, will continue running as a daemon process

Because there is no controlling terminal, any output produced by program needs to be directed somewhere

above redirects everything to a file
Can, if desired, direct everything to /dev/null instead

Thanks that almost does it! I tested it and the server stayed online even when I closed the shell or even powered off the computer that started it, but with nohup I can't give any input to that daemon, like to kick a player or change the map

---

### Post by gsgleason on 2010-05-21
Normally a server would be set up like a service, with an init script in /etc/init.d that you start and it runs in the background.

I have no knowledge of the COD server itself, or how it comes, but for normal services like a web server, file server, etc, that is how it's done.

If that's not available, you could run it from a screen session and detach before logging out.  Maybe you could just run it in the background with an ampersand?

---

### Post by gsgleason on 2010-05-21
> **Vrekk said:**
> Thanks that almost does it! I tested it and the server stayed online even when I closed the shell or even powered off the computer that started it, but with nohup I can't give any input to that daemon, like to kick a player or change the map


Ah.  Use a screen session then.  That should do the trick.

---

### Post by BoneKracker on 2010-05-21
> **Vrekk said:**
> Thanks that almost does it! I tested it and the server stayed online even when I closed the shell or even powered off the computer that started it, but with nohup I can't give any input to that daemon, like to kick a player or change the map

Use screen I tell you.  :)

---

### Post by amauk on 2010-05-21
Ah,
yes this assumes a non-interactive program

Maybe best to use screen in that case

ssh into server
then
```
screen -R
```
this creates a new screen session
run command
then CTRL+A, CTRL+D to detach the screen
close ssh session (even reboot your local machine)
re-ssh in
```
screen -R
```
to resume the screen session

---

### Post by Vrekk on 2010-05-21
> **gsgleason said:**
> Ah.  Use a screen session then.  That should do the trick.
> **BoneKracker said:**
> Use screen I tell you.  :)

Screen did it flawlessly!  I can detach it and still reopen it to give it any input it needs! Thanks everyone!

The cod4 server was built for windows and kinda hacked onto linux, so when you start up the cod4 server you just get a console with nothing loaded into it lol, but with screen I can give it all the info I need and manage it without having to open a cod4 client. 

There is a reason I will never leave these forms, even though I never really use Ubuntu anymore :guitar:

---

