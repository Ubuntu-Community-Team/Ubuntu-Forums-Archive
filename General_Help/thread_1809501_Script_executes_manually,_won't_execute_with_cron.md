---
title: "Script executes manually, won't execute with cron"
date: 2011-07-21
forum: General Help
---

### Post by Rikeshar on 2011-07-21
Hello everyone. So I've written a script that restarts the server of a game I play, giving you a 15 second notice. If I manually start this script, it works fine. However, if I try to have cron execute it, I get this error: 

```
-X: stuff: invalid option say Server is restarting in 15 seconds-ne
```...and it says this for every line in the rest of the script (substituting the correct phrases of course, but always starting at the "say" and ending with the "-ne")

The script looks like this:


```
# This is a script to restart the Minecraft server
# giving a 15 second warning before doing so

screen -S minecraft -X stuff "say Server is restarting in 15 seconds"`echo -ne $
sleep 5
screen -S minecraft -X stuff "say Server is restarting in 10 seconds"`echo -ne $
sleep 5
screen -S minecraft -X stuff "say Server is restarting in 5 seconds"`echo -ne '$
sleep 5
screen -S minecraft -X stuff "say Server is restarting NOW"`echo -ne '\015'`
sleep 1
screen -S minecraft -X stuff "stop"`echo -ne '\015'`
sleep 5
/usr/games/Minecraft/start.sh
```

Any ideas what might be going on here? If I take out the echos at the end of the lines then it passes the text through to screen but never "hits ENTER' and so the command never actually runs.

I checked my mail folder and cron sent this:

```
From zach@thornbury-ubuntu  Thu Jul 21 18:10:22 2011
Return-Path: <zach@thornbury-ubuntu>
X-Original-To: zach
Delivered-To: zach@thornbury-ubuntu
Received: by thornbury-ubuntu (Postfix, from userid 1000)
        id CF8536C0CD2; Thu, 21 Jul 2011 18:10:22 -0400 (EDT)
From: root@thornbury-ubuntu (Cron Daemon)
To: zach@thornbury-ubuntu
Subject: Cron <zach@thornbury-ubuntu> /usr/games/Minecraft/restart.sh  (failed)
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/zach>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=zach>
Message-Id: <20110721221022.CF8536C0CD2@thornbury-ubuntu>
Date: Thu, 21 Jul 2011 18:10:22 -0400 (EDT)

Must be connected to a terminal.
```

---

### Post by papibe on 2011-07-21
I would avoid using 'echo' since the script is not running interactively. Have you tried the standard ^M at the end?

Something like this:
```
screen -S minecraft -X stuff "say Server is restarting in 15 seconds^M"
```
The ^M is inserted by pressing first control+V and then pressing control+M.

Hope it helps.

---

### Post by Rikeshar on 2011-07-23
Hey, thanks for the response and sorry for taking so long to get back to you.

CTRL+V isn't working for me, I'm using NANO and CTRL+V is the key for "next page."

I'm not too familiar with the ^M command... what's it called and what's it supposed to do?

---

### Post by galvatron408 on 2011-07-23
The error is clearly stated in the log you posted:

"Must be connected to a terminal"

When, you run something out of cron, there is no terminal. You have to find out if your script or command has a flag to turn off the requirement.

---

### Post by Rikeshar on 2011-07-23
Hm. How could I do that? I'm pretty new to bash scripting so I'm not entirely sure. I know when creating launchers and the like there's a gui option to click "Run in Terminal" but I'm not sure how to do that without the GUI.

---

### Post by papibe on 2011-07-23
> **Rikeshar said:**
> I'm not too familiar with the ^M command... what's it called and what's it supposed to do?
That is the 'enter' you need, so your commands get executed. Note that is not the character ^ and then the letter M, but a representation of 'cr' (carriage return).

> **Rikeshar said:**
> I'm using NANO and CTRL+V is the key for "next page."
I researched a little bit, and I did not find any way to insert that in nano. If you get familiar enough with vi, you'll be able to do it as I suggested before.

Hope it helps.

---

### Post by galvatron408 on 2011-07-23
yea, inserting control characters isn't going to do anything for you. like i said, the problem is because your screen needs a screen to work...

uhhh, why don't you use "wall"

put this in to your crontab

* * * * * echo "hello world" | wall

man wall (for more information)

---

### Post by papibe on 2011-07-23
If we take /usr/games/Minecraft/start.sh out of the equation, the suggestions I made before DO work.

Try this: create an screen like this:
```
$ screen mytest
```
either detach it, or open another terminal. Create a crontab:
```
# m h  dom mon dow   command
*/1 * * * * /home/youruser/cron.sh
```
For the script cron.sh:
```
#!/bin/bash
screen -S mytest -X stuff "ls -hs^M"
sleep 2
screen -S mytest -X stuff "df -h .^M"
```
That will send a couple of commands every minute to the screen 'mytest'.

Regards.

---

### Post by Rikeshar on 2011-07-23
Alright! That worked! .... partially!

the ^M did indeed send the enter command like I was looking for. However, the script at the end didn't run >_<


How do we add the start.sh back into the equation?

(And thank you so much for your time. I just want you to know that it's appreciated.)

---

### Post by papibe on 2011-07-23
Is it too long? If not, could you post it or attach it?

Depending on the content, it maybe possible to force it to run as a non-interactive script.

Regards.

---

### Post by Rikeshar on 2011-07-23
It's really simple, it's just:

```
cd /usr/games/Minecraft
screen -S minecraft java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui
```

---

### Post by papibe on 2011-07-23
I'm not familiar with minecraft, but I have a few questions:

How the screen 'minecraft' is originally created?
Is it using the same start.sh?

I ask this because I want to know the status of the screen after the last 'stop' command you send. It is terminated or it is still there?

Regards.

---

### Post by Rikeshar on 2011-07-23
In this instance it is being started with the start script. After the stop command the minecraft server is shut down and the screen terminates. When run manually a new screen session starts after 5 seconds.

---

### Post by papibe on 2011-07-23
I think when you run start.sh, by default 'screen' tries to attach itself to the actual session. You can avoid that with a combination of the options -d and -m.

Try this:
```
screen -dmS minecraft java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui
```
Hope it helps.

---

### Post by Rikeshar on 2011-08-07
Later reply, but it worked! Thanks.

---

