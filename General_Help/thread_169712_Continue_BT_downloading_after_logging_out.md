---
title: "Continue BT downloading after logging out"
date: 2006-05-03
forum: General Help
---

### Post by galeron on 2006-05-03
Hi all,

Currently I am using the CLI client of BT to download files. How can I make my computer continue downloading even after I've logged out of the shell? I've tried to use 'at' to run the command but it appears that it does not work.

Ideas? TIA

---

### Post by Jason_25 on 2006-05-03
The easiest way would be to just to switch to a virtual terminal with ctrl-alt-f1, login and use rtorrent or any other command-line based torrent program from there.  If you wanted to be completely logged out, you could use the ```
screen
``` command, be presented with a new prompt, start your torrent, then ctrl-alt-a-d to detach from the session.  Then log out. Your torrent program will still be running.  To get back to it, log in and type ```

screen -r
```

---

### Post by galeron on 2006-05-03
[QUOTE=Jason_25]The easiest way would be to just to switch to a virtual terminal with ctrl-alt-f1, login and use rtorrent or any other command-line based torrent program from there.  If you wanted to be completely logged out, you could use the ```
screen
``` command, be presented with a new prompt, start your torrent, then ctrl-alt-a-d to detach from the session.  Then log out. Your torrent program will still be running.  To get back to it, log in and type ```

screen -r
```[/QUOTE]

Problem being that I'm logging in using SSH from a Windows box. Would that still work?

---

### Post by Demon012 on 2006-05-03
Yes screen should work no matter what your connecting from. (As long as you have screen installed on the linux box)

---

### Post by mcduck on 2006-05-03
You could just save the .torrent somewhere, and when you log in use that to start downloading again...

---

### Post by hw-tph on 2006-05-03
A couple of days ago I wrote the most basic of screen tutorials in response to a post on LQ [here](http://www.linuxquestions.org/questions/showthread.php?p=2218386#post2218386). You too might find it useful.


Håkan

---

