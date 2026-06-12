---
title: "autologin at background"
date: 2009-12-11
forum: General Help
---

### Post by whitered on 2009-12-11
I've created an user called 'server' (his task is to run a server and some web daemons). Now I want him to autologin at system startup, but do it at background, i.e. I dont want to see his desktop. I just want to see the login screen, but this user should be already logged in.
how can I reach this?

---

### Post by lykwydchykyn on 2009-12-11
Most services allow you to configure what user they run as; you don't need to actually log in a user to make it happen. 

What are the particular services you want this user to run?

---

### Post by pricetech on 2009-12-11
Will he have to adjust the runlevels at which the services run as well ??

---

### Post by whitered on 2009-12-11
this is good news. I'm going to run my homemade ruby scripts such as jabber-bot and maybe web server. AFAIK, I can create the scripts in /etc/init.d/, but I don't want to run them with root permissions. Also I don't want to run them under my own account.

---

### Post by whitered on 2009-12-11
> **pricetech said:**
> Will he have to adjust the runlevels at which the services run as well ??
i dont know :-?

---

### Post by whitered on 2009-12-11
> **pricetech said:**
> Will he have to adjust the runlevels at which the services run as well ??
I'm going to use the computer the way I did before, so I want to keep everything at its place. But the new user needs no window system, I can manage him via console. Is it answer for your question?

---

### Post by pricetech on 2009-12-11
Sorry.  I should have specifically addressed the question to lykwydchykyn.  I know him and he's good at Linux.  I occasionally get to pick his brain myself.

---

### Post by lykwydchykyn on 2009-12-11
Shouldn't have to mess with runlevels.

If these are custom scripts, you should be able to add the following line to /etc/rc.local, before the line that says "exit 0":

```

su username -c "my_script.whatever" &

```

where "username" is the name of the user you want running the script, and "my_script.whatever" is the name of your custom script.  I'd recommend using full paths to the files in question.

---

### Post by whitered on 2009-12-12
thank you, it works fine

---

