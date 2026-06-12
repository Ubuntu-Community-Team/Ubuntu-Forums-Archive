---
title: "Stealth SSH Startup Window?"
date: 2010-03-05
forum: General Help
---

### Post by zzzBrett on 2010-03-05
I'm looking for a way to, at startup, open an SSH connection to a server. I have the script, and I can put it in startup, but I have a few problems.

One, I don't like having the ssh window open in terminal. I'd like it to somehow be in the background, or as an icon on the system tray.

Two, I use a wireless connection, so I can't have it start up right away or it will attempt to connect before the wireless connection is established.

I am running KDE.

Any ideas?

Thanks!

---

### Post by Intrepid Ibex on 2010-03-05
Well you can put your script in either "~/.config/autostart" (all de's (Desktop Environment, e.g. KDE, Gnome)) or "~/.kde4/Autostart" (only KDE) if you want to have it started upon login. 

You can of course use something like xbindkeys, which will do the script you tell it to when pressing a assinged key, e.g. PageUp/PageDown (which at least I won't use anyway and therefore signed them for updating the system). You can read about it more by searching or asking somebody else, I'm too tired to go over the basics :|.

---

### Post by Flareside on 2010-03-05
You can use ssh -fN  to make ssh run in the background, but that is only good if your forwarding ports because i don't think theres anyway to access it again. You might want to look into starting an ssh session inside of a screen and detaching that and reattaching as necessary.

---

### Post by Daveski on 2010-03-05
> **zzzBrett said:**
> Two, I use a wireless connection, so I can't have it start up right away or it will attempt to connect before the wireless connection is established.


Have the script ping the router or server every few seconds and only carry on when it gets a reply.

---

### Post by zzzBrett on 2010-03-05
Thanks for the tips. The last two comments together seem like they should work, but i'm not quite there.

With ssh -fn, i get the error:
Cannot fork into background without a command to execute.

And it seems I could ping the server with a -c parameter until I get one reply, but when I'm not connected to the internet, it just comes back with unknown host and doesn't keep trying.

---

### Post by Agent ME on 2010-03-05
What is the purpose of the SSH connection? It probably should have a command to run or ports to forward.

Also, here's a script that will wait until it can get a connection, and restart if your program has an error and quits (like if your connection dies):
```
#!/bin/sh

while true
do
    until ping -c1 google.com
    do
        sleep 20
    done

    if your-command-here
    then
        exit
    fi

    sleep 10
done
```

---

### Post by prshah on 2010-03-05
You can use "screen" (from the repositories) to start up ssh in the background.

A sample command would be```
sleep 60 && screen ssh -p 22 servername.com
```

You will have to put the command into a shell script (any text file, make executable) and call that in your startup session manager.

To access the "hidden" screen, use the command```
screen -r
```

To drop out of screen, use Ctrl+A,D or to quit just close the SSH session.

---

### Post by zzzBrett on 2010-03-06
Thanks for the responses!

This is the script I ended up with by combining the last few tips, in case anyone is interested.

```
#!/bin/bash 

while true
do
    until ping -c1 google.com
    do
        sleep 20
    done

    if screen -d -m ssh -L port:localhost:port server_domain.com
    then
        exit
    fi

    sleep 10
done

```

---

