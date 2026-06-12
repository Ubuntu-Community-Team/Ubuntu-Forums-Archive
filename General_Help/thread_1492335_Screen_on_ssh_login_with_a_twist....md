---
title: "Screen on ssh login with a twist..."
date: 2010-05-24
forum: General Help
---

### Post by kempy1000 on 2010-05-24
I have managed to get screen to run on ssh login using this guide:
[http://taint.org/wk/RemoteLoginAutoScreen](http://taint.org/wk/RemoteLoginAutoScreen)

My .zshrc has this in it now:
```

# Auto-screen invocation. see: http://taint.org/wk/RemoteLoginAutoScreen
# if we're coming from a remote SSH connection, in an interactive session
# then automatically put us into a screen(1) session.   Only try once
# -- if $STARTED_SCREEN is set, don't try it again, to avoid looping
# if screen fails for some reason.
if [ "$PS1" != "" -a "${STARTED_SCREEN:-x}" = x -a "${SSH_TTY:-x}" != x ]
then
  STARTED_SCREEN=1 ; export STARTED_SCREEN
  [ -d $HOME/lib/screen-logs ] || mkdir -p $HOME/lib/screen-logs
  sleep 1
  screen -RR && exit 0
  # normally, execution of this rc script ends here...
  echo "Screen failed! continuing with normal bash startup"
fi
# [end of auto-screen snippet]

```

It works perfect but I have come across a problem. On startup I run rtorrent in a deamonised screen. So when I login now I get auto attached to that screen!

Ouput of screen -ls
```

chris@chimera:~$ screen -ls
There is a screen on:
        1588.rtorrentdeamon     (24/05/10 19:59:16)     (Detached)
1 Socket in /var/run/screen/S-chris.

```

Is it possible to make screen ignore the rtorrentdeamon screen so I dont get attached to it? 
I never attach to that screen so even stopping any reattacheing would also work.

Thanks
Chris

---

### Post by jerome1232 on 2010-05-24
looking at your script you have

screen -RR, which I believe is what is attaching the screen session.

Why not just use "screen", or perhaps "screen -d" (-d will dettach if it is attached to a session)

---

### Post by v1ad on 2010-05-24
why don't you just put "screen -r screenName" in bash.rc?

---

### Post by kempy1000 on 2010-05-24
> **jerome1232 said:**
> looking at your script you have

screen -RR, which I believe is what is attaching the screen session.

Why not just use "screen", or perhaps "screen -d" (-d will dettach if it is attached to a session)

If i change screen -RR to screen then everytime I login I get a new screen with the last screen detached.

screen -d gives the error
```

There is no screen to be detached.
Screen failed! continuing with normal bash startup

```

I was hoping I could have one screen and whenever I login I attach to that screen and when I logout I detatch from that one screen. 

Im no linux expert that code was all copy and paste :) Im  learning though!

Chris

---

### Post by kempy1000 on 2010-05-24
> **v1ad said:**
> why don't you just put "screen -r screenName" in bash.rc?

Doesnt the screen name change everytime I restart though?

Chris

---

### Post by jerome1232 on 2010-05-24
> **v1ad said:**
> why don't you just put "screen -r screenName" in bash.rc?

Ah well then what this guy said.

---

### Post by jerome1232 on 2010-05-24
If you look at the man page for screen there's some idea's you can play with.

```
screen -d -RR screenName
#from what I read that reattach a screen, if necesary it will detach or create a new screen session to do so
```

And there's alot more, I'd just play with options until you get the behavior you want.

---

### Post by kempy1000 on 2010-05-24
For future ref:

I sorted this problem

```

if [ "$TTY" = "/dev/pts/0" ]
then
        if [ "$PS1" != "" -a "${STARTED_SCREEN:-x}" = x -a "${SSH_TTY:-x}" != x ]
        then
                STARTED_SCREEN=1
                Sleep 1
                screen -d -RR pts-0.chimera && exit 0
        fi
fi

```

"*****.pts-0.chimera" this is the name a screen gets when opened on my machine

Does exactly what I want:
1) On login it opens a new screen if the last screen was exited cleanly (Typing exit and enter)
2) If a screen exists that wasnt exited by the command exit then it will reattach to it (Eg clicking X in putty)
3) Forces you to always work in a screen!

I also found this does not work with the sh shell but fine with bash and zsh.

Chris

---

