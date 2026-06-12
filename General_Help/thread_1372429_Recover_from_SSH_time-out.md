---
title: "Recover from SSH time-out?"
date: 2010-01-04
forum: General Help
---

### Post by the real omni on 2010-01-04
Hi,

Now and then I'll run a script or command on a remote system via SSH. Sometimes the script or command will run for quite some time, spewing output all the while. The command will continue to spit out lines and I'll walk away from the computer. When I come back, the SSH session will have timed out due to lack of user input, but if I log in again I can see in the process list that the script is still running.

Is there a way to hop back onto my old SSH session so I can continue to view the output of the script? Or do I actually have to type a random letter every N-minus-one minutes, N being the default SSH timeout value, in order to prevent the original SSH session from timeing out in the first place?

---

### Post by cariboo on 2010-01-04
Use screen, it is in the repositories. [Here]("http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/") is a howto.

---

### Post by bodhi.zazen on 2010-01-04
+1 to screen.

You can also use "keepalive" to keep your ssh sessions active.

---

### Post by doas777 on 2010-01-04
> **the real omni said:**
>  Or do I actually have to type a random letter every N-minus-one minutes, N being the default SSH timeout value, in order to prevent the original SSH session from timeing out in the first place?

I've written one of those before. I imagine a whole generation of CICS programmers can relate to your quandry, and have done the same.

---

### Post by prem1er on 2010-01-04
Not sure but wouldn't

```
nohup <command>&
```

do the same thing?

---

### Post by the real omni on 2010-01-05
> **cariboo907 said:**
> Use screen, it is in the repositories. [Here]("http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/") is a howto.


Many thanks, but this doesn't seem to do what I want.. From what I can tell, you have to launch the script through screen. This means I'd have to run every command through screen unless I knew ahead of time it was going to run longer than my ssh timeout value.

Adding 'screen' before every command is even worse than adding 'sudo' before every command ;) The latter I'm willing to put up with, the former I'm not.

I'm specifically looking for something that can pick up a process from a former tty session on the current tty session.

---

### Post by bodhi.zazen on 2010-01-05
> **the real omni said:**
> Many thanks, but this doesn't seem to do what I want.. From what I can tell, you have to launch the script through screen. This means I'd have to run every command through screen unless I knew ahead of time it was going to run longer than my ssh timeout value.

Adding 'screen' before every command is even worse than adding 'sudo' before every command ;) The latter I'm willing to put up with, the former I'm not.

I'm specifically looking for something that can pick up a process from a former tty session on the current tty session.

No, screen is what you want (I do not think there is a way to bring a BG process from another tty or detached application back to the foreground), I just think you misunderstand how to use screen.

See this link for additional information:

[http://www.damirkucic.com/2009/08/process-detaching-in-linux.html](http://www.damirkucic.com/2009/08/process-detaching-in-linux.html)

You start screen and it starts a new bash session.

You detach the screen session with Ctrl-a-d

You then retach with

screen -X

You may run multiple screen session if you wish.

---

### Post by prem1er on 2010-01-05
Bodhi, While you're around. Would you mind shedding some light on my post about nohup (2 or three posts up). Thanks.

---

### Post by bodhi.zazen on 2010-01-05
> **prem1er said:**
> Bodhi, While you're around. Would you mind shedding some light on my post about nohup (2 or three posts up). Thanks.

The link I gave in my last post discusses nohup nicely =)

But since you asked nicely :twisted:

Basically, if you wish to run programs in a terminal (tty or X) , when you log out or close the terminal it will also close the child processes.

To run a process in the background, we all know the & , but bg apps will be terminated when the terminal is closed. Try it:

```
xeyes &
```Now close the X terminal =)

To keep a process running if you wish to close a terminal you can use nohup or detach

```
nohup xeyes &
```OR

```
dtach xeyes
```Now what happens if you close your X terminal ?

Use disown if you want to keep an already bg process running.

```
xeyes &
disown -h %1
```Now what happens when you close the terminal ?

=)

EDIT: Reading the man page, you can use dtach similar to screen (normally I use nohup) :lolflag:

[http://linux.die.net/man/1/dtach](http://linux.die.net/man/1/dtach)

---

### Post by prem1er on 2010-01-05
\\:D/ Thank you!

---

### Post by the real omni on 2010-01-05
> **bodhi.zazen said:**
> No, screen is what you want (I do not think there is a way to bring a BG process from another tty or detached application back to the foreground), I just think you misunderstand how to use screen.

My understanding is that in order to bring a process to the current tty from an old tty, the process would have had to be started in a screen session. Is that correct? If so, that's not what I want, as it would require doing everything inside a screen session from the start.

I don't want to have to perform an extra step for every remote shell session, I just want to be able to call up a process in a shell session that has timed out.

I'd be quite surprised to find out that there's no way to do something as simple as that - linux has been around for a while now! ;)

---

### Post by bodhi.zazen on 2010-01-05
> **prem1er said:**
> \\:D/ Thank you!

You are welcome. The OP is asking not only how to keep a process running, but also how to reconnect to it.

To do this you need screen or dtach, I do not know how to reconnect to a process you started with nohup or disowned.

---

### Post by The Cog on 2010-01-05
> **the real omni said:**
> My understanding is that in order to bring a process to the current tty from an old tty, the process would have had to be started in a screen session. Is that correct? 
Yes, it is.
> If so, that's not what I want, as it would require doing everything inside a screen session from the start.

I don't want to have to perform an extra step for every remote shell session, I just want to be able to call up a process in a shell session that has timed out.You can't. When the session times out, the teminal is disconnected and all its attached processes are killed. If you know beforehand that your session might timeout, then you can disown it, but then you can't reconnect later. If you start it in screen, you can disconnect and reconnect as often as you want.
> I'd be quite surprised to find out that there's no way to do something as simple as that - linux has been around for a while now!It's not simple to reconnect to a process that has been killed.

---

### Post by bodhi.zazen on 2010-01-05
> **the real omni said:**
> I don't want to have to perform an extra step for every remote shell session, I just want to be able to call up a process in a shell session that has timed out.

As far as I know your options are to :

1. Learn to use the keepalive option with ssh. I think you would likely prefer this.

There are many how-to's on this, you can do it server side or client side.

[http://embraceubuntu.com/2006/02/03/keeping-ssh-sessions-alive/](http://embraceubuntu.com/2006/02/03/keeping-ssh-sessions-alive/)

clients depend on if you are on Linux or Windows (Putty, although putty will run on Linux as well).

2. Use screen. It is not *that* hard and the vast majority of people find screen to be extremely useful, especially with ssh. Is it really *that* much hassle to type screen or screen -x when you ssh in ? If so, why not write a simple script in .bashrc or .profile to automatically start or reconnect to a screen session ?

3. Use dtach. Probably more hassle then screen, but doable. I linked the man page above.

4. Keep doing what you are doing and suffer the occasional inconvenience of a ssh session that times out.

I am unaware of any additional options, you get to choose the lesser of the 4 evils.

---

