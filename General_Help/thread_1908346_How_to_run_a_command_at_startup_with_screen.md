---
title: "How to run a command at startup with screen?"
date: 2012-01-13
forum: General Help
---

### Post by Nailox on 2012-01-13
Hi. I need to run a shell script in a screen session on every reboot. How can I do this ? I tried with "@reboot /path/to/script" in crontab but its not working. I found this [http://serverfault.com/questions/233084/how-do-i-use-crontab-to-start-a-screen-session](http://serverfault.com/questions/233084/how-do-i-use-crontab-to-start-a-screen-session) but I can't understand it. Can you help me with this ? TYA

---

### Post by Lars Noodén on 2012-01-13
You might try launching your script from [font=Courier New]/etc/rc.local[/font].  It is run after all the other SystemV init scripts.  

screen is very powerful and a bit complex.  If the complexity is where you are having trouble, then you might look also at tmux.  It is a lot simpler and lacks many (most) of the features of screen but it can attach/detach nicely on demand.

---

### Post by Nailox on 2012-01-13
> **Lars Noodén said:**
> You might try launching your script from [font=Courier New]/etc/rc.local[/font].  It is run after all the other SystemV init scripts.  

screen is very powerful and a bit complex.  If the complexity is where you are having trouble, then you might look also at tmux.  It is a lot simpler and lacks many (most) of the features of screen but it can attach/detach nicely on demand.

How would launch it from /etc/rc.local ? Just copy it there? 
Also if I use tmux - how to run the script with tmux on reboot?

---

### Post by Lars Noodén on 2012-01-13
Yes, just copy it there, putting it ahead of the line 'exit 0'

If you use [tmux](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tmux.1.html) it can go something like this:

```

/usr/bin/tmux new-session -d '/usr/local/bin/myscript'

```

That will start a new session, launch your script, then detach.

---

### Post by Nailox on 2012-01-13
> **Lars Noodén said:**
> Yes, just copy it there, putting it ahead of the line 'exit 0'

If you use [tmux](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tmux.1.html) it can go something like this:

```

/usr/bin/tmux new-session -d '/usr/local/bin/myscript'

```

That will start a new session, launch your script, then detach.
So i copied this line (with my details) in rc.local. I rebooted and now in the running processes i see "sleep 720" which is part of the shell script. But I dont see the name of the script there. tmux is running. The same thing happened when I used "@reboot script.sh" in cron. So how can i tell if its running correctly ?

---

### Post by Lars Noodén on 2012-01-13
You can see if tmux is running properly by listing sessions or trying to attach.

```

# list sessions
tmux list-sessions

# or attach
tmux a

```

Does your script work if you run it manually?

---

### Post by Nailox on 2012-01-13
> **Lars Noodén said:**
> You can see if tmux is running properly by listing sessions or trying to attach.

```

# list sessions
tmux list-sessions

# or attach
tmux a

```

Does your script work if you run it manually?

ok I rebooted and listed sessions - i see one window
I attached to it and I can see the script running. So that means its all good right ?

---

### Post by Lars Noodén on 2012-01-13
Yes, congratulations!

---

### Post by Nailox on 2012-01-13
Thanks a lot for the help !

---

