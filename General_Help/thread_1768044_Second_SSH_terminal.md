---
title: "Second SSH terminal"
date: 2011-05-26
forum: General Help
---

### Post by hojjat on 2011-05-26
There are times when I'm logged into a remote machine using SSH and I need a second terminal window, also logged into the same machine, to do a side task. Right now, I have to open a new terminal, log in, change directory to the same location I was in the first terminal and do the task. I was wondering if there's a command I could use to "duplicate" my terminal window right away instead.

---

### Post by SecretCode on 2011-05-26
I don't use it routinely but have a look at **screen**. It allows you to get multiple shell sessions within one console / ssh session.

---

### Post by anomie on 2011-05-26
Both tmux and GNU screen (running on the remote host) can solve this problem. What they'll allow you to do is hop between an arbitrary number of logical "terminals". 

Try a 'net search for tutorials and screenshots on either.

---

### Post by hojjat on 2011-05-26
Both great answers. Please correct me if I'm wrong but these solutions don't actually give you a second "window", but allow to use the same window for more than one ssh connection, right?

---

### Post by Habitual on 2011-05-26
I wrote a gnome-terminal+screen+tabs-HOWTO over at [http://forums.linuxmint.com/viewtopic.php?f=42&t=73413](http://forums.linuxmint.com/viewtopic.php?f=42&t=73413)

that may help you out.

---

### Post by Lars Noodén on 2011-05-27
> **hojjat said:**
> Both great answers. Please correct me if I'm wrong but these solutions don't actually give you a second "window", but allow to use the same window for more than one ssh connection, right?

That's correct.  Neither screen and tmux, as useful as they are, will actually give you a second terminal window in and of themselves.

I can't think of a way to clone a terminal (with directory and environment variables all the same.)  However, you could make a profile that goes to the same starting point each time that might be close.

---

### Post by nothingspecial on 2011-05-27
> **hojjat said:**
> Both great answers. Please correct me if I'm wrong but these solutions don't actually give you a second "window", but allow to use the same window for more than one ssh connection, right?

It depends which machine you are running screen on. If you are runninig screen on the machine you are sitting in front of, then opening a new screen "window" would require you make anothere ssh connection.

But if you are running screen on the server then it is the same ssh connection, if you see what I mean.

I would suggest looking at byobu, which is just a nicely configed version of screen. Install it on your remote machine and run it after you log on through ssh.

Byobu gives you a 'sort of' task bar. Press F2 and you will get a new 'window'. You can see how many you have open on the 'taskbar' thing. You can switch between them using F3 (left) and F4 (right). You can open a whole load of them.

You might find it usefull to press F8 in each 'window' as you create it and give it a name so you know which window is which.

If you need 2 'windows' side by side, press Ctrl-A then | (which is shift \ on my keyboard). Switch between them by pressing Ctrl-A then Tab.

[ATTACH]193343[/ATTACH]

---

### Post by hojjat on 2011-05-27
Thanks for your replies. Seems like I'm stuck with screen at best.

---

