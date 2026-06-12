---
title: "Need some help switching from BusyBox"
date: 2009-07-21
forum: General Help
---

### Post by alpha_lt on 2009-07-21
Hello,
 
I'm new to Ubuntu. Just installed it and found some differences from BusyBox linux which I was using about year. I've noticed these:
 
1. Not asking for root pass and can't login as root, because don't know its pass. Do I need to somehow enable root login ?
2. Found nothing on /mnt. Where is my HDD partitions mounted ?
3. I logged in as regular user and command 'ps' showed that only bash and ps is running. Where all other processes ?
4. How to set up programs to run at startup ? There was /ffp/startup folder in my BusyBox machine. Now I don't know.
5. Where to find info on things like this ? In this site I can only find some info music listening, document creation and using graphic interface. Where to find more info on using terminal, configuring software in command line and so on...
 
I'm sorry if my questions is so noob, but I need someone to put me on right way.
 
Regards,
alpha

---

### Post by nikhilk on 2009-07-21
> **alpha_lt said:**
> Hello,
 
I'm new to Ubuntu. Just installed it and found some differences from BusyBox linux which I was using about year. I've noticed these:
 
1. Not asking for root pass and can't login as root, because don't know its pass. Do I need to somehow enable root login ?
2. Found nothing on /mnt. Where is my HDD partitions mounted ?
3. I logged in as regular user and command 'ps' showed that only bash and ps is running. Where all other processes ?
4. How to set up programs to run at startup ? There was /ffp/startup folder in my BusyBox machine. Now I don't know.
5. Where to find info on things like this ? In this site I can only find some info music listening, document creation and using graphic interface. Where to find more info on using terminal, configuring software in command line and so on...
 
I'm sorry if my questions is so noob, but I need someone to put me on right way.
 
Regards,
alpha

1. Logging as root is considered to be extremely dangerous. To do administrative use sudo or gksudo. See this [link]("https://help.ubuntu.com/community/RootSudo") for more details.

2. Your other partitions are probably mounted under /media.

3. Try ```
ps ax
``` or ```
ps afx
```

4. See this [link]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") for details.

5. [https://help.ubuntu.com](https://help.ubuntu.com) is a good starting point. There are other sites too e.g. [psychocats]("http://www.psychocats.net/ubuntu/index.php")

I hope that helps!

---

### Post by alpha_lt on 2009-07-21
Thanks. Its helpful.
Its hard to find help on using terminal. Even with google. But possible :P

---

### Post by alpha_lt on 2009-07-21
I've checked and my /media is empty... How it can be ? Where are my partitions mounted ?

---

### Post by michy99 on 2009-07-21
To see where your partitions are mounted:```
mount
```

---

