---
title: "Start downloads remotely"
date: 2011-09-22
forum: General Help
---

### Post by Tibblez on 2011-09-22
I've installed a relatively fresh Ubuntu 11.04 and have set up SSH but that is about it.  I'm looking for a way to start downloading large files remotely, either through SSH or really any other way that doesn't require software installation on the remote machine.  I believe I understand that I could use wget or something command line, but then is there a way to have it continue while I close the console window?

---

### Post by TiBaal89 on 2011-09-22
> **Tibblez said:**
> I've installed a relatively fresh Ubuntu 11.04 and have set up SSH but that is about it.  I'm looking for a way to start downloading large files remotely, either through SSH or really any other way that doesn't require software installation on the remote machine.  I believe I understand that I could use wget or something command line, but then is there a way to have it continue while I close the console window?

Yes, you can make commands run in the 'background' such that they don't stop when you end your ssh session.  Just append an "&" to the end of the command to do this.  If you want to start downloading something, end your ssh and have it keep going while you're gone just use 'wget [http://blahblahbah](http://blahblahbah) &'

Look into that and the 'bg' command to learn more...

---

### Post by bodhi.zazen on 2011-09-22
Best tool for what you want is screen 

[http://www.cyberciti.biz/tips/how-to-use-screen-command-under-linux.html](http://www.cyberciti.biz/tips/how-to-use-screen-command-under-linux.html)

several other on line screen tutorials, but screen is IMO best.

As an alternate you can use 

nohup <command> &

and dtach

---

### Post by bodhi.zazen on 2011-09-22
> **TiBaal89 said:**
> Yes, you can make commands run in the 'background' such that they don't stop when you end your ssh session.  Just append an "&" to the end of the command to do this.  If you want to start downloading something, end your ssh and have it keep going while you're gone just use 'wget [http://blahblahbah](http://blahblahbah) &'

Look into that and the 'bg' command to learn more...

& puts the command in the back ground, but if you close the terminal or ssh session often the command will stop running, although it does vary a little.

---

### Post by TiBaal89 on 2011-09-23
Interesting, hadn't noticed that... many thanks. :D

---

### Post by Tibblez on 2011-09-23
With the screen method would I still have to keep the original console window open until the download is complete?  I just want to start it and run away, if possible.

---

### Post by Tibblez on 2011-09-23
Sorry for the double post, I should have tried it first.  I just added the & to the end of my line closed the terminal window entirely. When I opened a new one the process was still running! Thanks.

---

### Post by WorMzy on 2011-09-23
> **bodhi.zazen said:**
> Best tool for what you want is screen

Tmux is better than screen, imo. It's got more or less the same features, but with less of the graphical bugs.

Worth checking out if you've never heard of it. Commands can be rebound to different key combinations, so you don't have to learn new ones.

---

### Post by WorMzy on 2011-09-23
> **Tibblez said:**
> With the screen method would I still have to keep the original console window open until the download is complete?  I just want to start it and run away, if possible.

No, you can detach from the screen (or tmux) session, disconnect from ssh, then reconnect and reattach later on.

I can't remember how you detach from screen, but the man pages will tell you.

Oh, and make sure you're running screen on the remote PC, not your local PC.


Oops, double post. Meant to edit.

---

### Post by Slim Odds on 2011-09-23
> **Tibblez said:**
> With the screen method would I still have to keep the original console window open until the download is complete?  I just want to start it and run away, if possible.

For screen, you type "Control-A d" to detach and leave stuff running.

Later you run screen with the -r command line option to reconnect to a running instance.

---

