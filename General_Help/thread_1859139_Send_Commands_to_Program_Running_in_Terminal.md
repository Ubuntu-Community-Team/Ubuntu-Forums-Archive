---
title: "Send Commands to Program Running in Terminal"
date: 2011-10-13
forum: General Help
---

### Post by ochieman2000 on 2011-10-13
Hello, 

I have been attempting to find a solution to this problem for some time now. I have a Minecraft Server running within a terminal. I would like to send a command to this program. 

Ive read about screen command and the stty command....such modes in tty are

"echo (-echo)	Echo back (do not echo back) every character typed.
echoe (-echoe)	Echo (do not echo) ERASE character as a backspace-space-backspace string. Note: This mode will erase the ERASEed character on many CRT terminals; however, it does not keep track of column position and, as a result, it may be confusing for escaped characters, tabs, and backspaces."

Not sure if I can use these to send a command to a particular terminal. Basically for a better idea of this problem I want to send two commands.

1. save-all command, this will save all the content. 
2. say command, this is used to say something. As this is operating in a terminal, any way to echo the command to the terminal line would work but we are not on the regular command line. 

Ive tested but nothing so far has worked. 

Thank you for the look.

---

### Post by meatytaco on 2011-10-13
Maybe this will help?
 [http://minecrafton.com/billing/knowledgebase/8/How-to-use-SSH-to-access-the-server-console.html]("http://minecrafton.com/billing/knowledgebase/8/How-to-use-SSH-to-access-the-server-console.html")

---

### Post by ochieman2000 on 2011-10-13
> **meatytaco said:**
> Maybe this will help?
 [http://minecrafton.com/billing/knowledgebase/8/How-to-use-SSH-to-access-the-server-console.html]("http://minecrafton.com/billing/knowledgebase/8/How-to-use-SSH-to-access-the-server-console.html")

mmm dunno, that seems to require a person to be apart of the process. I am looking for a way to automate this whole thing. I want to have a cron run a script every couple of hours to backup the server.

---

### Post by steverichter on 2011-10-13
You want to use screen's "stuff" command to send the command:

screen -p 0 -S screenname -X eval 'stuff "save-all" \015'

---

### Post by papibe on 2011-10-14
Hi ochieman2000, as you guessed it, and steverichter suggested you can easily solve that using screen sessions and the stuff option.

Here's a [thread]("http://ubuntuforums.org/showthread.php?t=1809501&highlight=screen+stuff") that makes use of both tricks.

Hope it helps,
Regards.

---

