---
title: "Detaching screen session"
date: 2009-10-15
forum: General Help
---

### Post by kyle00123 on 2009-10-15
I need to start a program in a Screen session from a shell script and then need to detach from a that session.  The script basically starts a program in the background that I can get back to when I need.  Is there a command to detach?  Or do I somehow send Ctrl+A and Ctrl+D signals?  Please post any ideas.

---

### Post by bodhi.zazen on 2009-10-15
You start a screen session

Run your application

And use Ctrl-a Ctrl-d

[http://www.rackaid.com/resources/linux-tutorials/general-tutorials/using-screen](http://www.rackaid.com/resources/linux-tutorials/general-tutorials/using-screen)

---

### Post by kyle00123 on 2009-10-15
I already know that I can press Ctrl+A and Ctrl+D.  What I want is a way for the shell script to pass the command for me so all I have to do is run the script and not anything else.

---

### Post by bodhi.zazen on 2009-10-16
I guess I am not understanding what it is you want.

You can give a command to screen and have screen start in the detached mode.

screen -d -m foo

See man screen :

> 
 **-d** **-m**   Start *screen* in "detached" mode. This creates a new session but
               doesn't  attach  to  it.  This  is  useful  for  system startup
               scripts.

---

### Post by kyle00123 on 2009-10-29
Thank you.
This works perfectly.
I only had one problem to start with.  It wouldn't work unless I put a command after it in the script.  It would shut the window before it finished the command and then it wouldn't work.  I solved this by putting 'logout' after it, which I should have had any ways.

Thank you very much, bodhi.zazen.

---

