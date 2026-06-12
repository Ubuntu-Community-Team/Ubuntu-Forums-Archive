---
title: "How do I bring a start up application to foreground?"
date: 2009-07-20
forum: General Help
---

### Post by wds on 2009-07-20
So, I start up mplayer at start up with the following command in System > Preferences > Startup Applications

mplayer -loop 0 -shuffle -playlist Music/iTunes/playlists/good_songs.pls

Sometimes I want to bring it to the foreground, so I find the PID with pgrep.

# pgrep mplayer

and it returns, say 3446

then I try to bring it to the foreground with

# fg 3446

and I get the following response

bash: fg: 3446: no such job

1. Is there a way to bring this job to the foreground?

2. In general, is there a way to bring a job to the foreground in a shell which didn't initiate the process?

Thanks!

---

### Post by blueridgedog on 2009-07-20
Wouldn't alt+tab work as well and be fewer key strokes than launching a script that searched for an ID then brought it to the foreground?

---

### Post by wds on 2009-07-20
blueridge, thanks - it isn't available by alt-tab

---

### Post by blueridgedog on 2009-07-20
> **wds said:**
> blueridge, thanks - it isn't available by alt-tab

I knew there must have been a catch.  Mplayer as launched is simply a process then (purely command line mode)?

---

### Post by wds on 2009-07-20
Yes, as far as I know it is launched just as a command line process, but I'm not really sure where using the System > Preferences > Start Up Applications in the gnome-menu really puts it. There is a gui option for mplayer, but I just use the command line interface.

---

### Post by pastalavista on 2009-07-20
I would think the easiest way to do it would be to create a keyboard shortcut (System > Preferences > Keyboard Shortcuts) to launch the frontend interface for mplayer or maybe even launch it at startup with an icon in the notification area.

---

### Post by wds on 2009-07-20
Ok - the whole reason I wanted to bring it to the foreground was to skip a song. I can just remove it from my playlist. So, for me, the issue isn't really particular to mplayer, but rather, how do I bring a command line process which was initiated at startup to the foreground?

---

### Post by Seq on 2009-07-20
I imagine your process isn't actually "backgrounded" such as that fg would be able to retrieve it. I would think it would be easiest to do this with GNU Screen. So You'll need to install it if you don't have it.

```
screen -d -R mplayer mplayer -loop 0 -shuffle -playlist Music/iTunes/playlists/good_songs.pls
```

The first "mplayer" is a name for the screen session. -d will **d**etach mplayer if it is in use elsewhere, and -R will resume it here, creating it if neccessary (You've just logged in). The remainder is your command.

That should run from startup. Then to resume it later, just run screen again telling it to detach if neccessary and resume.

```
screen -d -r mplayer
```

The lower case -r will cause it to not create a new session if one is missing (You'll probably want to poke your startup script instead).

You will probably want to read up on GNU Screen if you are not familiar with it. It is quite powerful.

---

### Post by wds on 2009-07-20
Seq - thanks, I'll play with it and let you know. Where are my start up processes?

---

### Post by Seq on 2009-07-20
> **wds said:**
> Seq - thanks, I'll play with it and let you know. Where are my start up processes?

You tell me, I thought you had one?

I'm assuming you did it in "System > Preferences > Startup Applications"? If so, in there :)

---

### Post by wds on 2009-07-20
ok :) - I was thinking more who the processes belong to. When I'm in a shell and I start a process, it belongs to that shell, right? Who do the start-up processes belong to? Also, I understand if the response is to read up more on job control which is what this raised for me. I was wondering in general if it is possible to bring a process to the foreground in a shell which didn't initiate the process.

---

### Post by Seq on 2009-07-20
> **wds said:**
> ok :) - I was thinking more who the processes belong to. When I'm in a shell and I start a process, it belongs to that shell, right? Who do the start-up processes belong to? Also, I understand if the response is to read up more on job control which is what this raised for me. I was wondering in general if it is possible to bring a process to the foreground in a shell which didn't initiate the process.

I'm not sure. It' parent is probably gnome-session or something along those lines..

---

