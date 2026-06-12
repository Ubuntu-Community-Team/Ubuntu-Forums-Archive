---
title: "I need help automating a Minecraft server"
date: 2011-06-29
forum: General Help
---

### Post by Zukaro Travon on 2011-06-29
I'm trying to fully automate a Minecraft server, and I decided to use Ubuntu 11.04 on this computer.  The computer I'm using for it is an old computer (it's the old family PC, it's about 5 years old (and running amazingly now that I've formatted the hard drive (compared to how it used to run))) so it won't run the Unix environment (or something like that) and runs the Gnome environment instead.

Anyways; the server auto-starts when my computer turns on (my computer also automatically turns on).  Now all I need to do is have my computer auto-shutdown at 12:00AM as well as enter the command "stop" into the running terminal.  I plan to later add more commands (such as automatically welcoming people to the server when they connect, but that's not important right now and I'll likely be able to figure out if I can get this working).

This is the command I'm using to shutdown the computer:
sudo shutdown -P 24:00

However, it doesn't work.  First of all, I need to enter my password, so I need some way to have the shell file enter my password for me whenever the terminal asks for it.  Second of all, it just plan doesn't work, even if I enter my password (like, the countdown doesn't appear).

As for entering commands into the terminal, the only way I can think of is:
echo "stop"

But the problem is that doesn't work because it wont enter into the running terminal (and I don't know how to do that).




(I'm a noob when it comes to Linux :P)

---

### Post by seawolf167 on 2011-06-29
I haven't set up a Minecraft server before, but why are you shutting down the computer? Why not just stop the Minecraft server at midnight?

There are lots more options for the *shutdown* command - take a look at the man page

```
man shutdown
```

you can also remotely access your server via *ssh*. First install the *openssh-server*

```
sudo apt-get install openssh-server
```

then from the remote computer you can log in via

```
ssh -l *username* ip.address.of.machine
```

---

### Post by Zukaro Travon on 2011-06-29
> **seawolf167 said:**
> I haven't set up a Minecraft server before, but why are you shutting down the computer? Why not just stop the Minecraft server at midnight?

There are lots more options for the *shutdown* command - take a look at the man page

```
man shutdown
```you can also remotely access your server via *ssh*. First install the *openssh-server*

```
sudo apt-get install openssh-server
```then from the remote computer you can log in via

```
ssh -l *username* ip.address.of.machine
```


I'm shutting down the computer so it doesn't overheat.  It wasn't built to stay on 24/7, if it was I wouldn't be trying to automate stuff.  As for remotely accessing it, I have no need (all I need to do is pickup the keyboard basically (and my other computer is in the same room as this one)).  I want to have it fully automated; starting up is good, it's just the shutting down part I'm having trouble with.

Basically I just need two things; a way to enter commands at specific times into the running terminal (as on startup the terminal is opened automatically to run the server), and a way to automatically shutdown at whatever time.

---

### Post by seawolf167 on 2011-06-29
Take a look at the "crontab" link in my signature. You can automate commands to run whenever you want by adding entires there. Just run the script as 'root' and you shouldn't have a problem with this command (or whatever you decide to use):

```
sudo shutdown now
```

---

### Post by Hovercat on 2011-06-29
Shouldn't you use 00:00 instead of 24:00?

---

### Post by Zukaro Travon on 2011-06-29
> **Hovercat said:**
> Shouldn't you use 00:00 instead of 24:00?


True.  :U
(is somewhat an idiot when it comes to the 24 hour clock)

---

### Post by Zukaro Travon on 2011-06-29
> **seawolf167 said:**
> Take a look at the "crontab" link in my signature. You can automate commands to run whenever you want by adding entires there. Just run the script as 'root' and you shouldn't have a problem with this command (or whatever you decide to use):

```
sudo shutdown now
```


Okay; thanks.

---

### Post by Zukaro Travon on 2011-06-29
The auto shutdown works (thank you).  Now all I need is a way to have a shell file enter commands into a running terminal (I have no clue how to do this, the way I've tried either does nothing or opens a new terminal).

---

### Post by seawolf167 on 2011-06-29
> **Zukaro Travon said:**
> Now all I need is a way to have a shell file enter commands into a running terminal (I have no clue how to do this, the way I've tried either does nothing or opens a new terminal).

This is why I suggested using SSH to manage the Minecraft server. You can't "inject" commands to a running terminal process. You may want to take a look at [BashScripting]("http://mywiki.wooledge.org/BashGuide").

---

### Post by Zukaro Travon on 2011-06-29
I have no clue what I'm doing.  x_x

Can anyone help me somehow give a command to the thing?  or something; idk.
(I've basically given up; I've been trying to get this working for 3 days or so)

---

### Post by seawolf167 on 2011-06-30
A command for what thing? SSH command from a remote computer to your machine? A crontab entry?

---

### Post by sandman887 on 2011-06-30
> **Zukaro Travon said:**
> I'm trying to fully automate a Minecraft server, and I decided to use Ubuntu 11.04 on this computer.  The computer I'm using for it is an old computer (it's the old family PC, it's about 5 years old (and running amazingly now that I've formatted the hard drive (compared to how it used to run))) so it won't run the Unix environment (or something like that) and runs the Gnome environment instead.

Anyways; the server auto-starts when my computer turns on (my computer also automatically turns on).  Now all I need to do is have my computer auto-shutdown at 12:00AM as well as enter the command "stop" into the running terminal.  I plan to later add more commands (such as automatically welcoming people to the server when they connect, but that's not important right now and I'll likely be able to figure out if I can get this working).

This is the command I'm using to shutdown the computer:
sudo shutdown -P 24:00

However, it doesn't work.  First of all, I need to enter my password, so I need some way to have the shell file enter my password for me whenever the terminal asks for it.  Second of all, it just plan doesn't work, even if I enter my password (like, the countdown doesn't appear).

As for entering commands into the terminal, the only way I can think of is:
echo "stop"

But the problem is that doesn't work because it wont enter into the running terminal (and I don't know how to do that).




(I'm a noob when it comes to Linux :P)


Why did you make a second topic about the same thing? Also, have you studied crontab? I provided a great resource for it. If you want to be an administrator of a server, you're going to have to learn crontab. Reading is essential. Also, I don't know why you want to insert commands into a running terminal, whether it's a tty or a pts. 

Give that article a read and then let me know how it worked for you. :)

---

### Post by sandman887 on 2011-06-30
One more thing...I don't know what you mean by inserting commands into a running terminal, but if you use crontab, you won't need to worry about a terminal. It will automagically just run at the scheduled time.

---

### Post by sandman887 on 2011-07-01
Actually, you could write directly to a /dev/tty, or /dev/pts, since everything in UNIX is a file, as long as you are the one running that device/terminal.

---

### Post by sandman887 on 2011-07-01
I typed this same message in your other topic. I'm reposting it in this one also in case you didn't see the other post:

Well if you really need to use that terminal, what you can do is write to that tty or pts. 

First, do this in a second terminal window:
```
who
```

This shows what users are running what processes in what tty or pts it's running in. 

TTY means teletype and an example is when you do something like CTRL-ALT-F2 or another F key. It takes you to an actual console on the machine. If you actually do try this, just remember that the graphical X session that you're on right now reading this is probably tty7. So if you want to get back to the graphical side of things after trying CTRL-ALT-F2 or whatever F key you choose, just hit CTRL-ALT-F7, and you'll come back to the friendly graphical user interface. You might want to print this page off in case you forget what button combination to press to get back to the graphical user interface.

PTS means pseudoterminal, and it's when you start an instance of gnome-terminal on your desktop once you've logged in under Gnome, for example. 

Anyway, once you see what tty/pts your server or program is running in, then you're halfway there. 

From another TTY or PTS, do this: 
```
yourcommandgoeshere > /dev/pts/0
```

Or if it's a TTY instead, then change /dev/pts/0 to /dev/tty/0

I don't know what number it's going to be. Zero was just an example. It may be any number. 

You can test this out by opening 2 gnome terminals. In one of them, type this:
```
tty
```

This tells you what terminal it is. So on the other terminal, type this:
```
ls -l > yourterminalid
```

"yourterminalid" would actually be the result of the tty command on the other terminal. Hopefully this helps you. 

If you truly need to insert a command into a running terminal, this will do it. Just remember: your-command > the-target-tty-value

Let me know if this works for you :)

---

### Post by arius13721 on 2011-07-01
Hrm.. I posted on something like this yesterday, but can't seem to find that post. Well, in short, my recommendation is to use screen to wrap the MC instance. Once you do that you can ssh in and reconnect to the screen for admin, or you can do it outside of the screen session.

This blog post explains what you would need to know to accomplish what I've just described.

[http://blog.lathi.net/articles/2008/09/13/scripting-screen](http://blog.lathi.net/articles/2008/09/13/scripting-screen)

Edit: Oh.. I found it, and it was you I was responding to it seems:
[http://ubuntuforums.org/showthread.php?t=1793730](http://ubuntuforums.org/showthread.php?t=1793730)

---

