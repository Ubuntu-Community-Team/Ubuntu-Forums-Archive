---
title: "Gammu command in bash startup script"
date: 2012-05-27
forum: General Help
---

### Post by DexNico on 2012-05-27
[FONT=Arial][SIZE=2]Hi all,[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]I have been stuck for days with this problem and I hope maybe someone can help med. I am new to Ubuntu and Linux so please bear with me.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]I am trying to run a bash script at system startup (Ubuntu Server Edition). One of the functions of the the script is to send a sms to me at system startup. I am trying to use Gammu to send the SMS and the script I have created works fine when I run it manually from the command prompt. I managed to get the script to create a log and it tells me that Gammu cannot find the configuration file. What am I doing wrong?[/SIZE][/FONT]
 
 
[FONT=Arial][SIZE=2]/etc/rc.local[/SIZE][/FONT]
```

[FONT=Arial][SIZE=2]nohup /home/sms_commands.sh > /tmp/sms_commands.log 2>/tmp/sms_commands.log &[/SIZE][/FONT]

```
 
 
[FONT=Arial][SIZE=2]/tmp/sms_commands.log[/SIZE][/FONT]
```

[FONT=Arial][SIZE=2]Warning: No configuration file found![/SIZE][/FONT]
[FONT=Arial][SIZE=2]Warning: No configuration read, using builtin defaults![/SIZE][/FONT]
[FONT=Arial][SIZE=2]No response in specified timeout. Probably phone not connected.[/SIZE][/FONT]

```
 
 
[FONT=Arial][SIZE=2]/home/sms_commands.sh[/SIZE][/FONT]
[FONT=Arial][SIZE=2](The first Gammu command in the script saves the output of all SMS and it is generating the error in the log above).[/SIZE][/FONT]
```

[FONT=Arial][SIZE=2]smsList=$(gammu --getallsms)[/SIZE][/FONT]

```
 
 
 
[FONT=Arial][SIZE=2]Best Regards[/SIZE][/FONT]
 
 
[FONT=Arial][SIZE=2]DexNico[/SIZE][/FONT]

---

### Post by lechien73 on 2012-05-27
Hi and welcome to the forums,

Probably what is happening is that the configuration file is stored under your user profile (likely ~/.gammurc). Try copying this file to the global config at /etc/gammurc.

Since your user isn't logged on at startup, Gammu doesn't know where to look for its config file.

---

