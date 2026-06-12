---
title: "can I shutdown my desktop from my laptop?"
date: 2009-08-30
forum: General Help
---

### Post by gdbutcher on 2009-08-30
Can I send a shutdown command from my laptop to my desktop? Both machines are on the same lan.

At the moment i use this on the desktop to shut it down at 2am just in case I forget: 
```
sudo shutdown -h -P 02:00
```

Is there a similar command I could use to shutdown the desktop from my laptop?

---

### Post by ibutho on 2009-08-30
One option could be to login to the desktop via ssh and then issue the shutdown command.

---

### Post by P4man on 2009-08-30
set up ssh

then you can log on to the desktop and type any command you want, including shutdown.

setting up ssh is really easy:
on the server (desktop):
```
sudo apt-get install openssh-server
```

on the client:
```
sudo apt-get install openssh-client
```

then log in using 

```
ssh <ip of server>
```

You can make a launcher even that will put the machine to sleep

---

### Post by wojox on 2009-08-30
SSH should already be installed on jaunty.

Login:

```
username@192.168.1.102
```

Of course substituting username and ip for yours.

---

### Post by mechdave on 2009-08-30
Yeah you can, try using ssh and then backgrounding the command to make it persistant after you exit the ssh session

---

### Post by gdbutcher on 2009-08-30
Thanks for your help everyone I did have ssh installed on both machines already and logging in using ssh worked. 

I've got no excuse for leaving my desktop on all night again now. :D

---

### Post by P4man on 2009-08-30
Thats one problem solved, and one thing I learned.. I never knew about 
```
sudo shutdown -h -P 02:00
```
Could be useful sometimes.

I wonder, is there a similar command to make a pc wake up at a given hour? 
I could use it as an alarm clock then..

---

