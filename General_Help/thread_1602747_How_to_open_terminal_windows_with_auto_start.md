---
title: "How to open terminal windows with auto start?"
date: 2010-10-21
forum: General Help
---

### Post by Ijin on 2010-10-21
[SIZE=3][FONT=Arial][SIZE=3]First off... I’m new to Linux (a new windows convertee) so please be [/SIZE][/FONT][/SIZE][SIZE=3][FONT=Arial][SIZE=3]patient with me...
[/SIZE]
[/FONT][FONT=Arial]I setup an xubuntu system to run a game server. I have two .sh files that I have setup to start when the system starts and they also keep checking to make sure the game server is running (will restart if it drops). My question is how can I have these scripts open a terminal window so I can see what is happening on the server? Below is an example of what the script looks like... I appreciate your help![/FONT][/SIZE]
 ```

[FONT=Courier New]until /home/trinity/bin/bin/trinity-realm -c /home/trinity/bin/etc/trinityrealm.conf 2>&1; [/FONT]
[FONT=Courier New]do date && echo "Realm server died with exit code $?. Restarting..."; [/FONT]
[FONT=Courier New]sleep 1; [/FONT]
[FONT=Courier New]done;[/FONT]

```

---

### Post by linuxpyro on 2010-10-21
So, when the system starts you want a terminal to come up in which your script runs?  First, take the commands from your post and put them into a script, say we call it game.sh (the first line of the file being #!/bin/sh).  Change the permission to make it runable (chmod 755 game.sh).

Now, I don't recall what terminal XFCE uses, but you can start your script in gnome terminal with the following command (assuming your script is in your home directory):

```

gnome-terminal --command="/home/youruser/game.sh"

```

Now, you can start that when you log in.  Again I'm not the most familiar with XFCE, but check out this thread:

[http://ubuntuforums.org/showthread.php?t=111128]("http://ubuntuforums.org/showthread.php?t=111128")

Note that if that doesn't work, you can try changing the command to /usr/bin/gnome-terminal --command="/home/youruser/game.sh".  Hope this helps!

---

### Post by Ijin on 2010-10-21
Thank you!!! I will give this a try ASAP...
 
I searched a little for the terminal name... i found xfce4-terminal... i will see if that is it.
 
Thanks again!

---

### Post by Ijin on 2010-10-21
Yes!!! That was it! Thank you so much!!!
 
also, xfce4-terminal was it as well.

---

### Post by linuxpyro on 2010-10-22
No problem, glad you got it working!  Hope you like Ubuntu. 

Also, you should edit your topic and add [solved] to the title, for anyone who might be searching.

---

