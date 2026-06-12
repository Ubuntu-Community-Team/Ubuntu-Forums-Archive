---
title: "How to keep an application alive even if I disconnect from ssh?"
date: 2010-05-08
forum: General Help
---

### Post by joesmith1234 on 2010-05-08
Hi All!

I like to use mnemosyne (and other applications) on my Nokia N900.  I have a server that I log into with "ssh -X" and then I open the application from there.

I worry about disconnections... let's say I'm connected via ssh while I'm on the bus, and then the bus goes through a tunnel and I get disconnected.  The application could close in an unexpected state, and all of my precious data could be corrupted.

Suppose I had gedit open, and right in the middle of my manuscript's denouement, my connection drops.  Because I forgot to save, I lose all my data. 

Is there some way to have a persistent connection?  Some kind of middle man that stays awake on the server side, kind of like you can do with IRC?

Thanks in advance!

---

### Post by t0p on 2010-05-08
Look at [this]("http://www.theinternetpatrol.com/how-to-keep-your-ssh-terminal-connected-and-from-being-automatically-disconnected-by-the-remote-computer/").

---

### Post by 3rdalbum on 2010-05-08
I don't think that's quite what the OP is after.

Joe, the answer for command-line programs over SSH is to start the "screen" program after logging in.

It starts a shell like normal, and it has features for running multiple shells and multiple programs over the one SSH connection, but it also saves your session should you be accidentally disconnected.

If you get disconnected, then you just log in again and run:

```
screen -D -R
```

which should reattach you to your running Screen session and all its shells and programs.

Does this work with X applications? No idea. Maybe try it?

(also, have a look at the man page for 'screen').

---

