---
title: "I need help with the terminal and shell files"
date: 2011-06-29
forum: General Help
---

### Post by Zukaro Travon on 2011-06-29
I'm trying to automate a server.  Everything is working except one key part.  I need a shell file which enters the command "stop" into the terminal running the server software at a certain time.

(it's for a Minecraft server)

I'm using Ubuntu 11.04

---

### Post by Zukaro Travon on 2011-06-30
Help  :\

---

### Post by sandman887 on 2011-06-30
I would suggest creating a crontab file. Here is a good website that explains how it works [http://clickmojo.com/code/cron-tutorial.html]("http://clickmojo.com/code/cron-tutorial.html")

Here is the code from a crontab I was using a month or so ago:
```
# m h  dom mon dow   command
0,10,20,30,40,50 * * * * /home/shredder/scripts/renewip
```

You submit a cron job by typing: 
```
crontab yourscriptname
```

To see if you correctly submitted the crontab file, you can view it by typing: 
```
crontab -l
```

---

### Post by Zukaro Travon on 2011-06-30
> **sandman887 said:**
> I would suggest creating a crontab file. Here is a good website that explains how it works [http://clickmojo.com/code/cron-tutorial.html](http://clickmojo.com/code/cron-tutorial.html)

Here is the code from a crontab I was using a month or so ago:
```
# m h  dom mon dow   command
0,10,20,30,40,50 * * * * /home/shredder/scripts/renewip
```You submit a cron job by typing: 
```
crontab yourscriptname
```To see if you correctly submitted the crontab file, you can view it by typing: 
```
crontab -l
```


Right now the problem isn't what time the task is launched at, it's getting it to work.  Like; I need the command "stop" to be put into the terminal by a shell script or by some other means.  Either way, that command needs to get into the terminal which is running the server (and then it needs to enter it so the server follows that command).

I have absolutely no clue how to do this without doing it myself, and the point of this is to not have to do anything.

---

### Post by sandman887 on 2011-06-30
> **Zukaro Travon said:**
> Right now the problem isn't what time the task is launched at, it's getting it to work.  Like; I need the command "stop" to be put into the terminal by a shell script or by some other means.  Either way, that command needs to get into the terminal which is running the server (and then it needs to enter it so the server follows that command).

I have absolutely no clue how to do this without doing it myself, and the point of this is to not have to do anything.

Why wouldn't a shell script/crontab work? I'm sorry, I'm kind of confused on what you want. Commands in a script would be executed just like if you typed them on the command line yourself.

---

### Post by sandman887 on 2011-06-30
If I'm not mistaken, it sounds like you can do it yourself manually just fine; you just want it automated. Are you saying you're having trouble creating a shell script to do this?

---

### Post by arius13721 on 2011-06-30
I can expand on what the OP is trying to accomplish. When starting minecraft, it starts its own shell from which one can run server command. To cleanly stop the server, the stop command must be run from that shell.

I've stumbled across a tool that wraps the minecraft server so you essentially "remotely" admin MC. This may be your best chance to accomplish what you're looking for. 

[http://www.minecraftforum.net/topic/23005-multiplexing-your-scripts-to-the-minecraft-server/](http://www.minecraftforum.net/topic/23005-multiplexing-your-scripts-to-the-minecraft-server/)

Alternatively you could just kill the server pid. I've done this numerous times without any adverse effects. Of coure, YMMV.

Edit: Another alternative may be to wrap the executable via screen, and send command that way. I've never done it myself, but this link may be of use:

[http://blog.lathi.net/articles/2008/09/13/scripting-screen](http://blog.lathi.net/articles/2008/09/13/scripting-screen)

---

### Post by Zukaro Travon on 2011-06-30
> **arius13721 said:**
> I can expand on what the OP is trying to accomplish. When starting minecraft, it starts its own shell from which one can run server command. To cleanly stop the server, the stop command must be run from that shell.

I've stumbled across a tool that wraps the minecraft server so you essentially "remotely" admin MC. This may be your best chance to accomplish what you're looking for. 

[http://www.minecraftforum.net/topic/23005-multiplexing-your-scripts-to-the-minecraft-server/](http://www.minecraftforum.net/topic/23005-multiplexing-your-scripts-to-the-minecraft-server/)

Alternatively you could just kill the server pid. I've done this numerous times without any adverse effects. Of coure, YMMV.

Edit: Another alternative may be to wrap the executable via screen, and send command that way. I've never done it myself, but this link may be of use:

[http://blog.lathi.net/articles/2008/09/13/scripting-screen](http://blog.lathi.net/articles/2008/09/13/scripting-screen)

Thanks; I think that will work.
(not sure yet, but I'm going to try it anyway)



[edit]
I have no clue how to use it (the screen command).

---

### Post by Zukaro Travon on 2011-06-30
> **sandman887 said:**
> If I'm not mistaken, it sounds like you can do it yourself manually just fine; you just want it automated. Are you saying you're having trouble creating a shell script to do this?

Basically.

What happens, is when I start the server a terminal comes up which the console runs in (so I can give it commands).  I need a way to give commands to that running terminal screen using a shell file (I'd be running that file through crontab because I'd need it to automatically start at a certain time).





[edit]
This is what I've got so far to start the server:
```
#!/bin/bash
screen -d -m -S Console

cd /home/mcs/Desktop/MinecraftServer/MCServer
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```

That lables it as "Console" when I do
```
screen -ls
```

But I can't figure out how to send the command "stop" to it.  This is what I've tried:
```
screen -p Console -X stop
```

---

### Post by Zukaro Travon on 2011-06-30
bump

---

### Post by sandman887 on 2011-07-01
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

### Post by Zukaro Travon on 2011-07-01
> **sandman887 said:**
> Well if you really need to use that terminal, what you can do is write to that tty or pts. 

First, do this in a second terminal window:
```
who
```This shows what users are running what processes in what tty or pts it's running in. 

TTY means teletype and an example is when you do something like CTRL-ALT-F2 or another F key. It takes you to an actual console on the machine. If you actually do try this, just remember that the graphical X session that you're on right now reading this is probably tty7. So if you want to get back to the graphical side of things after trying CTRL-ALT-F2 or whatever F key you choose, just hit CTRL-ALT-F7, and you'll come back to the friendly graphical user interface. You might want to print this page off in case you forget what button combination to press to get back to the graphical user interface.

PTS means pseudoterminal, and it's when you start an instance of gnome-terminal on your desktop once you've logged in under Gnome, for example. 

Anyway, once you see what tty/pts your server or program is running in, then you're halfway there. 

From another TTY or PTS, do this: 
```
yourcommandgoeshere > /dev/pts/0
```Or if it's a TTY instead, then change /dev/pts/0 to /dev/tty/0

I don't know what number it's going to be. Zero was just an example. It may be any number. 

You can test this out by opening 2 gnome terminals. In one of them, type this:
```
tty
```This tells you what terminal it is. So on the other terminal, type this:
```
ls -l > yourterminalid
```"yourterminalid" would actually be the result of the tty command on the other terminal. Hopefully this helps you. 

If you truly need to insert a command into a running terminal, this will do it. Just remember: your-command > the-target-tty-value

Let me know if this works for you :)

Okay, thanks (I haven't tried it yet, but I'm going to soon).  As for identifying the terminal, I put this into the file which launches the server:
```
screen -d -m -S Console
```When I type "screen -ls" from another terminal, it shows me running screens or something; anyways, Console appears in there and I just need a way to access it from another terminal and enter commands using a shell file.

(I'm going to try what you've posted soon though; thanks, and I'll tell you if it works or not)

---

### Post by arius13721 on 2011-07-01
Based upon the script snippet you posted, I believe the command to stop the server would be:

```
screen -X -S Console stuff "stop
"

```

It's worth noting that what I posted is the literal command. In the command, "stuff" stuff is telling screen to "stuff" it into the input stream.

---

### Post by Zukaro Travon on 2011-07-01
I've tried the way sandman887 and it didn't work.  I also tried the way arius13721 posted and it didn't work either.


As for the terminal running the server; I can't enter terminal commands, I can only enter server commands.  I don't know it it's because it's an application or something like that though.  Also, the server can be run using a GUI, but it runs better when I run it without the GUI (and that's when it runs in the terminal).

---

### Post by sandman887 on 2011-07-02
> **Zukaro Travon said:**
> I've tried the way sandman887 and it didn't work.  I also tried the way arius13721 posted and it didn't work either.


As for the terminal running the server; I can't enter terminal commands, I can only enter server commands.  I don't know it it's because it's an application or something like that though.  Also, the server can be run using a GUI, but it runs better when I run it without the GUI (and that's when it runs in the terminal).

Can you post the exact code you used for my suggestion? Some common mistakes people make when trying that are:
```
ls -l > /dev/pts0
```

I'm just using "ls -l" as an example...it could be any command. Anyway, there is no device pts0. There is a slash after pts, followed by the number. 

This is the correct way, assuming that you want to write to pts0 from another terminal:
```
ls -l > /dev/pts/0
```

---

### Post by sandman887 on 2011-07-03
Silly me. I forgot that this executes the command in the terminal you type it, and this only redirects output to the other terminal.

Forget about my suggestion :P

---

### Post by arius13721 on 2011-07-06
So you've done this:

```

screen -S minecraft

```

which creates a new screen called minecraft.

Then in that screen session you've typed (or whatever the command is that you use to launch mc):

```

java -Xms1024M -Xmx1024M -jar minecraft_server.jar nogui

```

which then scrolls a bunch of cruft.

You then disconnect from the session via 

```
Ctrl+a d
```

and from outside the screen you type:

```
screen -S minecraft -X stuff "stop
"
```

what happens at this point?

also please describe what happens when you reattach to the screen session (screen -R)

I've just done the above steps and it works without issue for me.

---

### Post by arius13721 on 2011-07-07
Ok.. I noticed something that escaped my attention before.

```
screen -d -m -S Console
```

This starts screen in detached mode. So when you change directories, and start the server, you're not in screen, you're still in a normal terminal.

There's a complete init script at minecraft wiki that can be used for starting, stopping, back-up, etc. 

[http://www.minecraftwiki.net/wiki/Server_startup_script](http://www.minecraftwiki.net/wiki/Server_startup_script)

---

