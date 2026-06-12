---
title: "SSH question."
date: 2012-01-26
forum: General Help
---

### Post by endoglastic on 2012-01-26
Ok, I think this one should have a fairly simple answer to it. I am still not very acquainted with ssh, but I run cs 1.6 servers through ssh. And when I start them and exit out, is there a way to see or open up that console again so I can see the current information that's going on in the cs server? Mainly to check for errors and crashes type thing. I think its possible, but maybe not. Thanks.

---

### Post by CharlesA on 2012-01-26
Run them in screen. That way you can detach the screen session when you disconnect and reconnect to it when you reconnect via ssh.

I do the same on a TF2 server.

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

---

### Post by gsgleason on 2012-01-26
I don't know anything about that particular service.  Does it log directly to standard output (to the terminal)?  When you start it, does it move to the background?

[edit]
screen was going to be my suggestion but I wanted to understand how the service works first.  screen is the answer.

---

### Post by CharlesA on 2012-01-26
I think it logs to stdout, or at least when I run TF2, it does. CS1.6 might be different tho.

---

### Post by endoglastic on 2012-01-26
I have it so it runs in the background, i put the "&" at the very end of the startup line. Maybe I'll look into this screen thing, if its the best way I guess. 

Yes, it shows me the output when I first start the service in the terminal, then when I exit out, I cant get back into it.

---

### Post by CharlesA on 2012-01-26
You'd have to run it inside screen.

I run my TF2 server like this:

```
/usr/bin/screen -d -m -S TF2 $HOME/hlds/orangebox/srcds_run -game tf +map cp_badlands -autoupdate > /dev/null 2>&1

```

Run that command and it starts the server inside screen.

---

### Post by endoglastic on 2012-01-26
Aight, sweet, thanks for the help Charles! I appreciate it a lot!

---

