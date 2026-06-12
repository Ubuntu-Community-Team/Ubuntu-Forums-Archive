---
title: "SSH questions"
date: 2009-08-04
forum: General Help
---

### Post by Patricrawley on 2009-08-04
Is there a way to SSH into another computer of mine, start a torrent client, like rtorrent or something. then close the tunnel w/o closing the program? I can tunnel in, and I can get rtorrent running but I don't know how to close it and come back later with it still running. Or if it's even possible for that matter.

---

### Post by approaching on 2009-08-04
I have been way curious about this for a while. Try this:

myCoolCommand >& /dev/null &

[http://www.linuxquestions.org/questions/linux-general-1/running-program-when-terminal-closed-36179/](http://www.linuxquestions.org/questions/linux-general-1/running-program-when-terminal-closed-36179/)

---

### Post by llamabr on 2009-08-04
I believe you want to incorporate the nohup command.  something like

nohup btdownloadheadless file.torrent &

should get you started.

You can also run it in a screen, which is immune to hanging up.  Screen is a very useful, powerful, and under appreciated tool.

---

### Post by approaching on 2009-08-04
nohup is soo much easier to remember than the one i found, and if you are just doing the one, you don't even need the &.

SWEET

---

### Post by Volt9000 on 2009-08-04
I did this recently using screen. Friggin' awesome program.

SSH into the computer in question, then just type

```

screen

```

From within, run rtorrent, or another command-line torrent app (don't know about GUI stuff, although I doubt they would work.)
Then just hit Ctrl+a then d and you'll detach from screen. Now you can log out.

Anytime you wanna check your progress, SSH back in and type

```

screen -r

```

And boom! Use the shortcut above again to detach while keep it running in the background.

---

### Post by lswb on 2009-08-04
Volt9000 beat me to it, screen is ideal for something like this.

---

### Post by Patricrawley on 2009-08-05
Thanks guys, I'm gonna try screen out when I get off work today.

---

