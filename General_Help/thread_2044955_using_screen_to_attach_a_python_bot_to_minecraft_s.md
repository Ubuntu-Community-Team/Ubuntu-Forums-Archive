---
title: "using screen to attach a python bot to minecraft server"
date: 2012-08-20
forum: General Help
---

### Post by micahpage on 2012-08-20
I am not sure where to put this thread, gaming, programming, or if it's just misuse of the program screen. 

I came across the program screen to attach a terminal to a the minecraft commands. Which it works. I can successfully type in commands from the terminal ie. screen and they are executed in my minecraft server. 

The problem i came across is when I try to automate executing the commands via a python bot.

The command I found to execute the server:
```
screen -dmS world java -Xms1024M -Xmx1024M -jar minecraft_server.jar -nogui

```

the command I found to attach a terminal to the server's cmds:
```
screen -r world
```

so i had my bot just executing the cmd 'screen -r world' and pipe the stdout for display, but if I try to have the bot execute,say anything it is on a separate screen, i think? 
for example: if i print something in the loop, and then manually enter "Cntl+a d" it kicks out of the server display screen and back to my bot displaying its loop.

My intentions was to have to the loop keep executing '/list' to display players in the server, for the initial test. In which I am confused and led me here.

---

