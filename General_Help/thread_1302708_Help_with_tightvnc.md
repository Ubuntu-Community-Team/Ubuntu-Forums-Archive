---
title: "Help with tightvnc"
date: 2009-10-27
forum: General Help
---

### Post by lronic on 2009-10-27
i did already install tightvnc 
when i type this command it give me an error
vncserver :1 -geometry 1024×768 -depth 16 -pixelformat rgb565
vncserver: geometry 1024×768 is invalid 

can someone help me ?


thank you

---

### Post by CharlesA on 2009-10-27
Try adding the display at the end.

vncserver -geometry 1024x768 -depth 16 -pixelformat rgb565 :1

---

### Post by lronic on 2009-10-27
now this error 
vncserver: Wrong type or access mode of /home/ubuntu/.vnc.

?

---

### Post by lronic on 2009-10-27
Sorry i'm new at 
Linux dont know alot of command

---

### Post by CharlesA on 2009-10-27
> **lronic said:**
> Sorry i'm new at 
Linux dont know alot of command

That's fine.

Can you post what these commands return?

```
ls -la ~/.vnc
```
```
ls -lad ~/.vnc
```

---

### Post by lronic on 2009-10-27
this what it say 


ubuntu@fast:~$ ls -lad ~/.vnc
drwx------ 2 root root 4096 2009-10-27 06:05 /home/ubuntu/.vnc
ubuntu@fast:~$ ls -la ~/.vnc
ls: cannot open directory /home/ubuntu/.vnc: Permission denied

---

### Post by CharlesA on 2009-10-27
Yeah, it's owned by root. Are you on a livecd by chance? Don't know if that would cause the problem or not.

You'd have to change the owner:

```
sudo chown -R ubuntu:ubuntu .vnc
```

---

### Post by lronic on 2009-10-27
no this is a server 
just type that command to it ?

---

### Post by CharlesA on 2009-10-27
Yeah, just run that command from your home directory. It'll ask you for your password.

---

### Post by lronic on 2009-10-27
now this what it say 
when i type the command you gave me 
ubuntu@fast:~$ ls -lad ~/.vnc
drwx------ 2 ubuntu ubuntu 4096 2009-10-27 06:05 /home/ubuntu/.vnc
ubuntu@fast:~$ ls -la ~/.vnc
total 48
drwx------  2 ubuntu ubuntu  4096 2009-10-27 06:05 .
drwxr-xr-x 32 ubuntu ubuntu  4096 2009-10-27 09:03 ..
-rw-r--r--  1 ubuntu ubuntu 11087 2009-10-26 21:45 fast:1.log
-rw-r--r--  1 ubuntu ubuntu     5 2009-10-26 21:34 fast:1.pid
-rw-r--r--  1 ubuntu ubuntu 11172 2009-10-27 06:25 fast:2.log
-rw-r--r--  1 ubuntu ubuntu     5 2009-10-27 06:05 fast:2.pid
-rw-------  1 ubuntu ubuntu     8 2009-10-26 21:15 passwd
-rwxr-xr-x  1 ubuntu ubuntu   319 2009-10-26 21:30 xstartup

---

### Post by CharlesA on 2009-10-27
Looks good, try launching the server now.

---

### Post by lronic on 2009-10-27
can you how me how ?

---

### Post by CharlesA on 2009-10-27
Same way as here:
```

vncserver -geometry 1024x768 -depth 16 -pixelformat rgb565 :1
```

---

### Post by lronic on 2009-10-27
one more thing 
when i connect to the Box 
i just enter the ip to the Vnc client and click connect right ?
i could connect to it ,but it wont ask me for the password to get in

---

### Post by lronic on 2009-10-27
this what it say 
A VNC server is already running as :1

but i cant connect to it 
did i do anything wrong ?

what the connamd to kill it and start it back up ?

---

### Post by CharlesA on 2009-10-27
That's correct.

Did you run just vncserver first so that it prompts to set a password?

vncserver -kill :1

to kill the server.

---

### Post by lronic on 2009-10-27
i set a password to it 
[FONT=monospace]vncserver -geometry 1024x768 -depth 16 -pixelformat rgb565 :1

is rgb565 a password ?


[/FONT]

---

### Post by CharlesA on 2009-10-27
Nope, that's not the password. Are you able to get connected and interact with the GUI?

---

### Post by lronic on 2009-10-27
ok now i could connect to it you know why 
i cant conectrol it it wont like me to anything ?

what i have to do now ?

---

### Post by lronic on 2009-10-27
i mean 
i could connect to it already 
but it wont let me control it 
i cant click on anything 
it just letting view

---

### Post by CharlesA on 2009-10-27
Gotcha. Are you able to get to a terminal prompt? If you can (which I think you can), run this:

```
sudo apt-get remove tightvncserver
sudo apt-get autoremove
rm -rf ~/.vnc
sudo apt-get install tightvncserver
vncserver
```

That'll remove vncserver and reinstall it.

---

### Post by lronic on 2009-10-27
i for got to reboot 
thanx alot for the help

---

### Post by lronic on 2009-10-27
good very good =)
your the best

---

### Post by lronic on 2009-10-27
one more thing the key bord is not the same 

number 1  is a letter s

---

### Post by CharlesA on 2009-10-27
Are you tunneling VNC over SSH?

---

### Post by lronic on 2009-10-27
hmmmmm dont know what that mean 
Sorry i'm new at this 
i connect to it by a VNC client 
but when i intsall it i use via SSH

---

### Post by CharlesA on 2009-10-27
Not sure if it's being tunneled over SSH or not, but try this:

> 1. edit ~/.vnc/xstartup
2. put the line "export XKL_XMODMAP_DISABLE=1" before your gnome-session.
3. restart vncserver.

[Source.]("http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html")

---

### Post by lronic on 2009-10-27
when i type 
restart vncserver
it say 
-bash: restart: command not found

---

### Post by CharlesA on 2009-10-27
Lol, whoops. The command should be:

vncserver -kill :display

Then start it up again.

---

### Post by lronic on 2009-10-27
thank you i got it to work now 

very thing is working now 

you just save me $150 =)
cuz i'm renting this linux box
when i want a admin to do something they change like $150/hours 

thanx alot

---

### Post by tacom6 on 2012-01-19
> **CharlesA said:**
> Lol, whoops. The command should be:

vncserver -kill :display

Then start it up again.

Just wanted to add to the info bank.

Once you have installed everything and it works. If you wanted to only offer VNC server on 127.0.0.1 (to avoid sharing the ports to the world/public internet) then execute it with the following options:

sudo /usr/local/bin/vncserver -localhost -nolisten tcp -interface 127.0.0.1 -alwaysshared -depth 24 -geometry 1280x1024 :1

Feel free to change the geometry, it's kinda high i know. :KS

---

### Post by oldos2er on 2012-01-19
Closed, necromancy.

---

